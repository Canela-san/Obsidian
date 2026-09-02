# 🤝 Camada 5: Sessão (Session Layer)

**Tags:** #redes #modelo-osi #camada-sessao #sincronizacao #dialogo

**Navegação:** [[Modelo OSI (Open Systems Interconnection)|↑ Modelo OSI]] · ← [[Camada 4 - Transporte]] · [[Camada 6 - Apresentação]] →

A Camada de Sessão é a "gerente de reuniões" do Modelo OSI. Enquanto a Camada de Transporte (4) se preocupa em criar o tubo de conexão ponta-a-ponta, a Camada de Sessão organiza e estrutura o diálogo que acontece dentro desse tubo entre duas aplicações rodando em máquinas diferentes.

---

## 🛠️ Função Principal
Sua função primordial é **estabelecer, gerenciar e encerrar sessões** de comunicação entre os aplicativos. Ela determina quem fala, quando fala e por quanto tempo, além de implementar mecanismos de recuperação em caso de falhas na rede.

### O que ela faz na mensagem?
* **Envio (Encapsulamento):** Recebe os **Dados** da Camada de Apresentação (6) e adiciona um cabeçalho (*Header*) de sessão. Esse cabeçalho contém marcadores de sincronização e informações de controle de diálogo.
* **Recebimento (Desencapsulamento):** Recebe o **Segmento/Datagrama** processado pela Camada 4, lê o cabeçalho de sessão para entender o estado atual do diálogo (ex: se é a vez dela transmitir ou receber), remove o cabeçalho e repassa os **Dados** limpos para a Camada 6.

---

## 📦 PDU (Protocol Data Unit)
O PDU desta camada é genericamente chamado de **Dados (Data)**.
* *Nota Técnica:* Em literaturas muito acadêmicas do OSI purista, pode ser referido como **SPDU (Session Protocol Data Unit)**, mas no mercado e na prática, a partir da camada 5, tratamos o payload simplesmente como "Dados" ou "Mensagem".

---

## ⚙️ Serviço, Interface e Protocolo

### 1. Serviço (O que oferece para a Camada 6)
Fornece um ambiente organizado para a troca de dados, oferecendo três serviços cruciais:
* **Controle de Diálogo:** Define como a comunicação vai ocorrer: *Simplex* (só um fala), *Half-Duplex* (um fala por vez, como um walkie-talkie) ou *Full-Duplex* (ambos falam ao mesmo tempo).
* **Gerenciamento de Token:** Impede que as duas partes tentem executar a mesma operação crítica simultaneamente (útil no modo *Half-Duplex*).
* **Sincronização (Checkpoints):** Se você está transferindo um arquivo de 10GB e a rede cai no gigabyte 9, a camada de sessão permite inserir "pontos de verificação" (checkpoints). Assim, a transmissão é retomada do último checkpoint, não do zero.

### 2. Interface (Conexão entre Camadas)
A Camada 5 expõe APIs (Application Programming Interfaces) para a Camada 6 solicitar o início ou o fim de uma sessão. Ela traduz essas solicitações para a Camada 4, mantendo a aplicação isolada dos detalhes de transporte: a Camada 6/7 só precisa pedir "abra uma sessão com o Host B", e é a Camada 5 quem cuida de toda a burocracia de handshake, tokens e pontos de sincronismo por trás dos panos — repassando o tráfego já organizado para o socket TCP/UDP correspondente na Camada 4.

### 3. Protocolos e Padrões
Diferente das camadas 1 a 4, a Camada de Sessão raramente aparece como um protocolo isolado e visível no dia a dia. No modelo TCP/IP (o que realmente rodamos na prática), suas funções costumam ser absorvidas dentro da própria aplicação — é por isso que ela, junto com a Camada 6, é frequentemente "achatada" dentro da Camada de Aplicação nos diagramas simplificados. Ainda assim, alguns exemplos clássicos:
* **NetBIOS:** Protocolo histórico de redes Windows, usado para estabelecer sessões de comunicação entre nomes de máquinas.
* **RPC (Remote Procedure Call):** Permite que um programa chame uma função em outra máquina como se fosse local, gerenciando toda a sessão dessa "chamada remota".
* **SIP (Session Initiation Protocol):** Literalmente batizado pela sua função — inicia, gerencia e encerra sessões de chamadas de voz e vídeo (VoIP).
* **Sockets API:** O ato de "abrir e fechar um socket" na programação é a materialização prática do conceito teórico desta camada.

---

## 🛰️ Elementos de Hardware Relacionados
Assim como a Camada de Apresentação (6), a Camada de Sessão é **estritamente lógica**. Não existe chip, placa ou cabo dedicado a "sessões" — tudo é gerenciado pelo Sistema Operacional (pilha de sockets) ou por bibliotecas específicas dentro da aplicação (como uma biblioteca de RPC ou de SIP).

---

## 🔍 Visão de Engenharia: Sessões em Sistemas de Supervisão (SCADA / OPC UA)
Em automação industrial, o conceito de "sessão" ganha um peso ainda maior do que na internet comum. Um exemplo direto está no protocolo **OPC UA**: ele define formalmente um objeto de **Sessão** que é *independente* da conexão de transporte da Camada 4.

Na prática, isso significa que se a rede cair por alguns segundos e o TCP precisar reconectar, a Sessão OPC UA pode ser retomada sem que o sistema supervisório (SCADA) precise refazer toda a autenticação e reconfiguração das assinaturas de dados (*subscriptions*) com o CLP — economizando um tempo que pode ser crítico numa planta que não pode ficar "cega" por muito tempo.

---

## 🔑 Pontos-Chave para Revisão
- **PDU:** Dados (ou SPDU na literatura OSI purista).
- Cuida do *diálogo*: quem fala, quando, e como retomar depois de uma queda (checkpoints/sincronização).
- Três modos de diálogo possíveis: Simplex, Half-Duplex (com gerenciamento de token) e Full-Duplex.
- Camada estritamente lógica — sem hardware dedicado, vive na pilha de sockets do SO ou em bibliotecas (RPC, SIP).
- Aplicação industrial: Sessões OPC UA sobrevivem a quedas de conexão TCP, evitando reautenticar tudo com o CLP a cada instabilidade de rede.
- **Pergunta de fixação:** qual protocolo é literalmente nomeado pela função desta camada? → **SIP** (Session Initiation Protocol), usado para iniciar/gerenciar chamadas de voz e vídeo (VoIP).
