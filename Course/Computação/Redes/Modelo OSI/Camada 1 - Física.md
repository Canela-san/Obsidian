# 🔌 Camada 1: Física (Physical Layer)

**Tags:** #redes #modelo-osi #hardware #sinais #camada-fisica

**Navegação:** [[Modelo OSI (Open Systems Interconnection)|↑ Modelo OSI]] · Próxima camada → [[Camada 2 - Enlace de Dados]]

A Camada Física é a base de todo o modelo OSI. Ela lida com a transmissão bruta de sequências de bits através de um meio de transmissão físico. Diferente das camadas superiores, ela não se preocupa com o significado dos dados, mas sim com as propriedades elétricas, mecânicas e óticas do sinal.

---

## 🛠️ Função Principal
A função primordial é a **transmissão de bits**. Ela define as especificações elétricas (níveis de tensão), mecânicas (conectores e pinagens), funcionais (o que cada pino faz) e procedimentais (sequência de eventos para transmitir) para ativar, manter e desativar o link físico.

### O que ela faz na mensagem?
* **Envio (Encapsulamento):** Recebe o **Quadro (Frame)** da Camada 2 e o converte em um fluxo de sinais (pulsos elétricos, pulsos de luz ou ondas eletromagnéticas).
* **Recebimento (Desencapsulamento):** Capta os sinais do meio físico e os reconverte em bits para entregar à Camada de Enlace.
* **Nota Técnica:** Nesta camada, **não há adição de cabeçalho (Header)** no sentido de dados de controle complexos. O "acréscimo" aqui é a codificação do sinal (como Manchester ou NRZ) e a sincronização de clock.

---

## 📦 PDU (Protocol Data Unit)
O PDU desta camada é o **Bit**.
* Aqui a unidade de informação é individual (0 ou 1), transmitida serialmente ou em paralelo pelo meio.

---

## ⚙️ Serviço, Interface e Protocolo

### 1. Serviço (O que oferece para a Camada 2)
Fornece um caminho físico para a transmissão de bits entre entidades da camada de enlace. Garante que, se a Camada 2 enviar um bit "1", a Camada 2 do outro lado receba um bit "1" (gerenciando a taxa de erro de bit e a sincronização).

### 2. Interface (Como o hardware se conecta)
Define os padrões de conexão física:
* **Tipos de conectores:** RJ-45, conectores de fibra (LC, SC), DB-9 (RS-232).
* **Níveis de Tensão:** Por exemplo, definir que +5V é '1' e -5V é '0'.
* **Pinagem:** Qual pino é transmissão (TX), qual é recepção (RX) e qual é o terra (GND).

### 3. Protocolos e Padrões (As regras)
Diferente das camadas superiores que são puramente software, aqui os protocolos são padrões de engenharia:
* **Ethernet (Físico):** 1000BASE-T, 10GBASE-SR.
* **Serial/Industrial:** RS-232, RS-485 (comum em redes de automação), USB.
* **Wireless:** Especificações físicas do IEEE 802.11 (frequências de 2.4GHz/5GHz).
* **DSL, SDH, SONET.**

---

## 🛰️ Elementos de Hardware Relacionados
* Cabos (Par trançado, Coaxial, Fibra Óptica).
* Repetidores e Hubs (trabalham apenas com sinais, sem ler endereços MAC).
* Transceivers (SFP, modems).
* Placas de rede (NICs) em seu nível de interface elétrica.

---

## 🔍 Aspectos de Engenharia (Para Redes de Processos Industriais)
Em ambientes industriais, a Camada Física deve considerar a **Imunidade a Ruído (EMI/RFI)**. O uso do padrão **RS-485** com sinais diferenciais, por exemplo, é uma decisão de Camada 1 para garantir a integridade dos bits em longas distâncias e ambientes com motores elétricos.

---

## 🔑 Pontos-Chave para Revisão
- **PDU:** Bit — não existe cabeçalho de controle, só codificação de sinal (Manchester, NRZ) e sincronismo de clock.
- Não interpreta o significado dos dados: só cuida de tensão elétrica, luz ou rádio.
- Hardware típico: cabos, hubs/repetidores, transceivers (SFP), NICs (na camada elétrica).
- Padrões que caem em prova: RS-485 (imunidade a ruído em automação), Ethernet físico (1000BASE-T), IEEE 802.11 (Wi-Fi).
- **Pergunta de fixação:** por que um *hub* opera na Camada 1 e não na Camada 2? → Porque ele apenas repete o sinal elétrico para todas as portas, sem nunca ler o endereço MAC do quadro.
