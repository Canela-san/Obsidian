O Access Point é o dispositivo que estende a rede cabeada para o meio aéreo, criando a rede Wi-Fi (WLAN - _Wireless Local Area Network_).

- **Camada OSI:** Camada 1 (Física) e Camada 2 (Enlace).
    
- **Função Principal:** Atua essencialmente como um _bridge_ (ponte) transparente entre o meio físico Ethernet (cabo) e o meio físico Wireless (ondas de rádio - padrão IEEE 802.11).
    
- **Detalhes de Operação:** Um AP dedicado **não faz roteamento, não distribui IP (DHCP) e não faz NAT**. Ele apenas pega os quadros de rede do cabo, modula em radiofrequência (usando técnicas como OFDM ou QAM) e os transmite pelo ar. Quando recebe o sinal de um celular ou notebook, ele demodula e injeta de volta no cabo Ethernet para o switch/roteador processar.
    
- **Gestão:** Em redes de alta performance, utiliza-se múltiplos APs espalhados pelo ambiente, todos com o mesmo SSID (nome da rede) e senha, conectados via cabo ao switch principal. Isso permite um _roaming_ eficiente e maior estabilidade, delegando o processamento pesado de roteamento apenas para o roteador.