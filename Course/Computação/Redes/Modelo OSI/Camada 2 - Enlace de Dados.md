# 🔗 Camada 2: Enlace de Dados (Data Link Layer)

**Tags:** #redes #modelo-osi #camada-enlace #MAC #switch #ethernet

**Navegação:** [[Modelo OSI (Open Systems Interconnection)|↑ Modelo OSI]] · ← [[Camada 1 - Física]] · [[Camada 3 - Rede]] →

A Camada de Enlace de Dados transforma o meio de transmissão bruto (Camada 1) em um link confiável. Ela é responsável por organizar os dados em formatos lógicos e garantir que a comunicação entre dois dispositivos conectados diretamente no mesmo meio físico ocorra sem erros de endereçamento.

---

## 🛠️ Função Principal
Sua principal função é o **controle de acesso ao meio** e a **detecção de erros**. Ela mascara as imperfeições da camada física, fazendo com que o link pareça livre de erros para a camada de rede.

### O que ela faz na mensagem?
* **Envio (Encapsulamento):** Recebe o **Pacote** da Camada 3 e adiciona um cabeçalho (*Header*) e um rodapé (*Trailer*), criando o **Quadro**. 
    * O *Header* contém os endereços físicos (MAC) de origem e destino.
    * O *Trailer* contém o **FCS (Frame Check Sequence)** para detecção de erros.
* **Recebimento (Desencapsulamento):** Recebe os bits da Camada 1, verifica se o endereço MAC de destino é o seu e se o FCS indica que o quadro está íntegro. Se tudo estiver correto, ela "descasca" o cabeçalho e o rodapé e entrega o **Pacote** para a Camada 3.

---

## 📦 PDU (Protocol Data Unit)
O PDU desta camada é o **Quadro (Frame)**.
* É a primeira unidade de dados com uma estrutura lógica definida (início, endereços, dados, verificação de erro e fim).

---

## ⚙️ Serviço, Interface e Protocolo

### 1. Serviço (O que oferece para a Camada 3)
Fornece a transferência de pacotes entre máquinas vizinhas. Isso inclui:
* **Enquadramento (Framing):** Delimitação de onde começa e termina um grupo de bits.
* **Controle de Erro:** Identifica quadros corrompidos através de cálculos matemáticos (CRC).
* **Controle de Fluxo:** Evita que um transmissor rápido "atropele" um receptor lento.

### 2. Interface (Conexão entre Camadas)
A Camada 2 é frequentemente dividida em duas subcamadas para facilitar a interface:
* **LLC (Logical Link Control):** Interface com a Camada 3 (Rede), tratando da parte lógica e protocolos superiores.
* **MAC (Medium Access Control):** Interface com a Camada 1 (Física), tratando do endereçamento físico e quem tem o direito de transmitir no cabo agora.

### 3. Protocolos e Padrões
* **Ethernet (IEEE 802.3):** O mais comum em redes cabeadas.
* **Wi-Fi (IEEE 802.11):** Controle de acesso ao meio sem fio (CSMA/CA).
* **PPP (Point-to-Point Protocol):** Usado em links diretos.
* **ARP (Address Resolution Protocol):** Embora alguns o coloquem na fronteira, ele é essencial aqui para traduzir IPs em endereços MAC.

---

## 🛰️ Elementos de Hardware Relacionados
* **Switches:** O hardware clássico da Camada 2. Ele lê o endereço MAC para decidir em qual porta o quadro deve ser enviado.
* **Bridges (Pontes):** Conectam dois segmentos de rede.
* **Placa de Rede (NIC):** É onde reside o endereço MAC gravado em hardware.

---

## 🔍 Visão de Engenharia: Redes Industriais e VLANs
Em sistemas de automação, a Camada 2 é onde configuramos as **VLANs (Virtual LANs)**. Isso permite isolar o tráfego de controle (como mensagens de um CLP/PLC) do tráfego administrativo, aumentando a segurança e reduzindo colisões. 

Protocolos industriais como o **Profinet** ou **EtherNet/IP** utilizam extensivamente as capacidades da Camada 2 para garantir que os dados cheguem no tempo correto (determinismo) através de priorização de quadros (QoS).

---

## 🔑 Pontos-Chave para Revisão
- **PDU:** Quadro (Frame) — primeira camada com estrutura lógica de verdade (Header + Trailer).
- Subcamadas: **LLC** (conversa com a Camada 3) e **MAC** (conversa com a Camada 1, controla quem transmite).
- Detecção de erro via FCS/CRC no trailer; controle de fluxo evita atropelar um receptor lento.
- Hardware típico: Switch (lê MAC pra decidir a porta), Bridge, NIC.
- Aplicação industrial: VLANs isolam o tráfego de CLP do tráfego administrativo; Profinet/EtherNet-IP usam priorização de quadros pra garantir determinismo.
- **Pergunta de fixação:** qual a diferença entre um Hub (Camada 1) e um Switch (Camada 2)? → O Switch lê o endereço MAC e encaminha só pra porta certa; o Hub apenas repete o sinal elétrico pra todas as portas, sem inteligência nenhuma.
