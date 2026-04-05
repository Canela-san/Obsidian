O switch é o equipamento responsável por interligar múltiplos dispositivos cabeados dentro de uma mesma rede local (LAN), criando a malha física da sua infraestrutura.

- **Camada OSI:** Camada 2 (Enlace). _(Existem switches L3 que também roteiam, mas na borda doméstica/distribuição utiliza-se L2)._
    
- **Unidade de Dados:** Lida com Quadros (_Frames_) e endereçamento MAC (Físico).
    
- **Função Principal:** Diferente de um _hub_ antigo (que replicava o sinal para todas as portas), o switch possui um circuito integrado específico (ASIC) que constrói e mantém uma tabela MAC (Tabela CAM). Ele memoriza qual endereço MAC está conectado a qual porta física.
    
- **Detalhes de Operação:** Quando um quadro chega, o switch lê o MAC de destino e encaminha o tráfego **exclusivamente** para a porta correspondente. Isso elimina colisões de pacotes (cada porta é um domínio de colisão isolado) e permite comunicação _Full-Duplex_ simultânea em máxima velocidade. Em upgrades robustos, switches gerenciáveis permitem a criação de VLANs (Redes Virtuais, padrão 802.1Q) para segmentar o tráfego (ex: separar a rede de convidados ou IoT da rede principal).