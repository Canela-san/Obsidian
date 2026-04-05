# 🤝 Camada 5: Sessão (Session Layer)

**Tags:** #redes #modelo-osi #camada-sessao #sincronizacao #dialogo

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
A Camada 5 expõe APIs (Application Programming Interfaces) para a Camada 6 solicitar o início ou o fim de uma sessão. Ela traduz essas solicitações para a