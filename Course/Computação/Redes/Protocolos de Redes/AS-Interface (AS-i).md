**Tags:** #redes-industriais #automacao #as-interface #fieldbus #nivel0 #sensor #atuador

O AS-Interface é um sistema de barramento de campo de baixo nível, otimizado para a conexão de sensores e atuadores binários (on/off). É a solução mais simples e econômica para levar a inteligência da rede até o dispositivo físico final.

---

## 🛠️ Função Principal
A função principal é a **substituição de cabos paralelos**. Em vez de levar dois fios de cada sensor até o CLP, o AS-i utiliza um único cabo para alimentar e comunicar todos os dispositivos, reduzindo drasticamente custos de instalação e manutenção.

---

## 📐 Arquitetura OSI (Colapsada)
Para garantir velocidade extrema e baixo custo, o AS-i utiliza uma **arquitetura reduzida**, implementando apenas três camadas:

### 1. Camada 1: Física
* **O Meio:** O famoso **Cabo Amarelo** (flat cable). É um cabo de dois fios, não blindado, que transporta simultaneamente **Dados e Energia (30V DC)**.
* **Codificação:** Usa a codificação **Manchester II**, que garante que a componente DC (energia) seja constante, enquanto os dados são transmitidos como pulsos de corrente.
* **Topologia:** Totalmente flexível (Estrela, Barramento, Anel, Árvore).
* **Limites:** Máximo de 100 metros (sem repetidores).

### 2. Camada 2: Enlace
* **Método de Acesso:** **Mestre-Escravo com Polling Cíclico**. O Mestre pergunta individualmente para cada Escravo: "Qual seu estado?", e o escravo responde imediatamente.
* **Capacidade:** Originalmente 31 escravos (versão 2.0) ou até 62 escravos (versão 2.1 com endereçamento A/B).
* **Determinismo:** O tempo de ciclo é fixo. Para 31 escravos, o mestre varre todos em no máximo **5ms**.

### 3. Camada 7: Aplicação
* **Dados:** Focada em bits. Cada escravo padrão fornece 4 bits de entrada e 4 bits de saída.
* **Interface:** Mapeia os dados diretamente na tabela de imagem de entradas/saídas do CLP.

---

## 📦 PDU (Telegramas)
O AS-i trabalha com telegramas muito curtos para ser rápido:
* **Chamada do Mestre:** 14 bits (Endereço + Comando).
* **Resposta do Escravo:** 7 bits (Dados + Segurança).

---

## 🛰️ Elementos de Hardware
* **Mestre AS-i:** Geralmente um cartão no CLP ou um Gateway para outra rede (como Profinet).
* **Escravos:** Módulos de E/S ou sensores/atuadores inteligentes com chip AS-i integrado.
* **Fonte de Alimentação:** Especial para AS-i (30V), que contém um circuito de desacoplamento de dados para não "sujar" o sinal.

---

## 🔍 Visão de Engenharia: Onde usar?
O AS-i é imbatível em sistemas de transporte (esteiras), máquinas de embalagem e processos onde há muitos sensores binários espalhados. 
**Ponto de Atenção:** Ele não é adequado para transmitir grandes volumes de dados (como imagens de câmeras ou configurações complexas de inversores), onde redes como Ethernet Industrial são preferíveis.