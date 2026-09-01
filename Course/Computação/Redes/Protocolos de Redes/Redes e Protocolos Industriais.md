# 🏭 MOC: Redes e Protocolos Industriais

**Tags:** #redes-industriais #protocolos #automacao #piramide-automacao #osi #determinismo

Esta nota é o centro nervoso do estudo de comunicação em sistemas de controle de processos. O objetivo das redes industriais é garantir que a informação flua desde o sensor mais simples no campo (Nível 0) até os sistemas de gestão da planta (Níveis superiores), respeitando requisitos críticos de tempo real, imunidade a ruídos e determinismo.

---

## 🏛️ A Pirâmide da Automação (Arquiteturas Hierárquicas)
Para entender um protocolo, precisamos saber *onde* ele opera na planta industrial e o que ele precisa fazer. 

| Nível da Pirâmide | Nome                     | Função Típica                                          | Exigência de Tempo | Protocolos Comuns                        |
| :---------------- | :----------------------- | :----------------------------------------------------- | :----------------- | :--------------------------------------- |
| **Nível 4 e 5**   | **Gestão / Corporativo** | ERP, MES, Planejamento de Produção.                    | Minutos / Horas    | Ethernet TCP/IP, HTTP, MQTT              |
| **Nível 3**       | **Supervisão**           | SCADA, IHMs avançadas, Servidores OPC.                 | Segundos           | Ethernet (TCP/IP), OPC UA                |
| **Nível 2**       | **Controle (Célula)**    | Interligação entre CLPs (PLCs) e controladores mestre. | Milissegundos      | Profinet, EtherNet/IP, Modbus TCP        |
| **Nível 1**       | **Campo (Fieldbus)**     | Instrumentação inteligente (Transmissores, Válvulas).  | Milissegundos      | CAN, Profibus DP/PA, Foundation Fieldbus |
| **Nível 0**       | **Sensor / Atuador**     | Chaves fim-de-curso, botões, sensores binários.        | Microssegundos     | AS-Interface (AS-i), IO-Link             |

---

## 🔌 O Modelo OSI Reduzido (Arquitetura Colapsada)
Diferente da internet clássica, no chão de fábrica (Níveis 0 e 1), não temos tempo para roteamento complexo ou sessões pesadas. Por isso, as redes *Fieldbus* "colapsam" o modelo OSI, focando apenas em:
* **Camada 1 (Física):** Cabos blindados, sinais diferenciais (RS-485), conectores robustos.
* **Camada 2 (Enlace):** Controle rígido de acesso ao meio (Mestre/Escravo, CSMA/CA, Token Passing).
* **Camada 7 (Aplicação):** O formato da mensagem que o CLP entende.
*(As camadas 3, 4, 5 e 6 geralmente são ignoradas ou condensadas nestes níveis mais baixos).*

---

## 📚 Catálogo de Protocolos (Notas Detalhadas)

*(Clique nos links abaixo para acessar os detalhes, camada por camada, de cada protocolo).*

### 🟢 Nível de Chão de Fábrica (Sensor, Atuador e Campo)
Foco em simplicidade, baixo custo por nó e altíssimo determinismo.
* Protocolo [[AS-Interface (AS-i)]] -> *Rede de nível de bit, cabo amarelo de 2 fios.*
* Protocolo [[CAN e CANopen]] -> *Baseado em eventos, altíssima confiabilidade, controle por CSMA/CA.*
* Protocolo [[Profibus (DP e PA)]] -> *O gigante dos barramentos de campo, baseado em RS-485.*
* Protocolo [[Modbus RTU]] -> *O protocolo mais clássico e simples, arquitetura Mestre-Escravo.*

### 🔵 Nível de Controle e Célula (Ethernet Industrial e RTE)
Foco na evolução da rede Ethernet comum para suportar Tempo Real (RTE - Real-Time Ethernet). Traz alta largura de banda para conectar os CLPs.
* [[Ethernet Industrial vs Comercial]] -> *Por que o CSMA/CD da Ethernet comum é um problema para PIDs.*
* [[Profinet]] -> *A evolução do Profibus para o mundo Ethernet (suporta RTE e IRT).*
* [[EtherNet-IP]] -> *Usa o protocolo CIP sobre a infraestrutura Ethernet padrão.*
* [[EtherCAT]] -> *Processamento "on the fly", extremamente rápido para controle de movimento.*

### 🟣 Nível de Supervisão e Integração (SCADA)
Foco na padronização dos dados para os sistemas de TI e gestão.
* [[OPC (OLE for Process Control)]] -> *A arquitetura Clássica (DCOM/Windows).*
* [[OPC UA (Unified Architecture)]] -> *O padrão moderno da Indústria 4.0, multiplataforma e seguro.*

---

## 📐 Conceitos Transversais e Fundamentos
*Para complementar o estudo de protocolos, revise os fundamentos de infraestrutura:*
* [[Topologias de Rede Industrial]] -> *Estrela, Anel (redundância DLR), Barramento, Árvore.*
* [[Meios Físicos e Cabeamento]] -> *Par Trançado, Fibra Óptica, Imunidade a Ruído EMI.*
* [[Modos de Transmissão e Fluxo de Dados]] -> *Simplex, Half-Duplex, Full-Duplex (Baseado na Aula 7).*