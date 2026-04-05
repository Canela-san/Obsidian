**Tags:** #redes #modelo-osi #camada-rede #IP #roteamento #encaminhamento

A Camada de Rede é a "geógrafa" do modelo OSI. Ela é responsável por determinar a melhor rota que os dados devem seguir do ponto de origem ao ponto de destino, atravessando múltiplas redes independentes se necessário. É aqui que o endereçamento lógico substitui o endereçamento físico.

---

## 🛠️ Função Principal
Sua função principal é o **roteamento (routing)** e o **endereçamento lógico**. Enquanto a Camada 2 sabe como falar com o vizinho no mesmo cabo, a Camada 3 sabe como encontrar um dispositivo em qualquer lugar do mundo ou de uma planta industrial complexa.

### O que ela faz na mensagem?
* **Envio (Encapsulamento):** Recebe o **Segmento** da Camada 4 e adiciona o cabeçalho (*Header*) de rede, transformando-o em um **Pacote**.
    * O cabeçalho contém os endereços lógicos (Ex: IPv4 ou IPv6) de origem e destino.
* **Recebimento (Desencapsulamento):** Recebe o **Quadro** da Camada 2, remove os cabeçalhos físicos, analisa o endereço IP de destino. Se o pacote for para a própria máquina, ela remove o cabeçalho de rede e entrega o **Segmento** para a Camada 4. Se for para outra rede, ela decide por qual interface reencaminhar o pacote.

---

## 📦 PDU (Protocol Data Unit)
O PDU desta camada é o **Pacote (Packet)**.
* Um pacote contém o endereço IP final, garantindo que a informação saiba para onde ir através de roteadores intermediários.

---

## ⚙️ Serviço, Interface e Protocolo

### 1. Serviço (O que oferece para a Camada 4)
* **Encaminhamento de Host a Host:** Diferente da entrega nó-a-nó (L2), aqui a entrega é de ponta a ponta na rede lógica.
* **Fragmentação e Reagrupamento:** Se um pacote for grande demais para o meio físico (MTU), a Camada 3 pode dividi-lo em pedaços menores e remontá-los no destino.
* **Independência de Hardware:** Permite que os dados viajem entre diferentes tipos de Camadas 1 e 2 (Ex: sai via Wi-Fi, passa por Fibra e chega via Ethernet).

### 2. Interface (Conexão entre Camadas)
A Camada 3 recebe pedidos da Camada de Transporte (L4) para transportar dados para um endereço IP específico. Ela utiliza os serviços da Camada de Enlace (L2) para colocar esses pacotes dentro de quadros físicos.

### 3. Protocolos e Padrões
* **IP (Internet Protocol):** IPv4 e IPv6 são os pilares.
* **ICMP (Internet Control Message Protocol):** Usado para mensagens de erro e diagnóstico (o famoso `ping`).
* **IPsec:** Protocolos para segurança e criptografia na camada de rede (VPNs).
* **Protocolos de Roteamento:** OSPF, BGP e RIP (ajudam os roteadores a aprender os caminhos).

---

## 🛰️ Elementos de Hardware Relacionados
* **Roteadores:** O dispositivo principal que toma decisões baseadas em tabelas de roteamento.
* **Switches Layer 3:** Equipamentos avançados que combinam a velocidade de comutação de um switch com as capacidades de roteamento de um roteador.

---

## 🔍 Visão de Engenharia: Redes Industriais e Hierarquia
Para projetos de automação em larga escala, a Camada 3 é onde definimos a segmentação da rede. Em uma planta industrial, é comum usar o roteamento para isolar a **Rede de Controle** (chão de fábrica) da **Rede Corporativa**. 

O uso de sub-redes (Subnetting) e NAT (Network Address Translation) é fundamental aqui para gerenciar dispositivos como CLPs e sensores inteligentes, garantindo que o tráfego pesado de câmeras de monitoramento, por exemplo, não interfira nos pacotes críticos de controle de processos que rodam em IP.