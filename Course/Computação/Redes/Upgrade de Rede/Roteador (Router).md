O roteador é o "cérebro" da topologia de rede. Sua função estrita é interligar redes distintas — neste caso, a sua rede local (LAN) e a internet (WAN).

- **Camada OSI:** Camada 3 (Rede).
    
- **Unidade de Dados:** Lida com Pacotes (_Packets_) e endereçamento IP (Lógico).
    
- **Funções Principais:**
    
    - **Roteamento:** Analisa o endereço IP de destino de cada pacote e decide o melhor caminho para encaminhá-lo utilizando tabelas de roteamento.
        
    - **NAT (Network Address Translation):** Como a sua provedora fornece apenas um IP público (WAN), o roteador usa o NAT para traduzir os IPs privados (LAN) da sua casa para este IP público único, permitindo que múltiplos dispositivos acessem a internet simultaneamente.
        
    - **DHCP (Dynamic Host Configuration Protocol):** Atribui automaticamente endereços IP privados, máscaras de sub-rede, gateways e servidores DNS aos dispositivos que entram na rede.
        
    - **Segurança (Firewall SPI):** Inspeciona pacotes que entram e saem, bloqueando tráfego não solicitado de fora para dentro.