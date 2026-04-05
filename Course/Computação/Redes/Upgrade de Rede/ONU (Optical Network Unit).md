A ONU (frequentemente chamada de ONT (Optical Network Terminal) em contextos domésticos) é o equipamento de borda (CPE - _Customer Premises Equipment_) que faz a interface entre a rede de fibra óptica da provedora de internet (ISP) e a infraestrutura de cobre da rede local.

- **Camada OSI:** Opera primordialmente na Camada 1 (Física) e Camada 2 (Enlace).
    
- **Função Principal:** Realiza a conversão eletro-óptica. Ela recebe os pulsos de luz (sinal óptico) provenientes da OLT (_Optical Line Terminal_) da provedora através de uma rede PON (_Passive Optical Network_) e os modula/demodula em sinais elétricos (Ethernet) que os dispositivos da rede local conseguem processar.
    
- **Detalhes de Operação:** A ONU extrai os quadros (frames) Ethernet do sinal óptico multiplexado que chega pela fibra (geralmente via GPON ou EPON) e os entrega ao roteador via cabo de rede metálico (RJ45).