# 🚚 Camada 4: Transporte (Transport Layer)

**Tags:** #redes #modelo-osi #camada-transporte #TCP #UDP #portas #sockets

A Camada de Transporte é o divisor de águas do Modelo OSI. Ela é a ponte que separa as camadas focadas na infraestrutura e roteamento da rede (1, 2 e 3) das camadas focadas na aplicação do usuário (5, 6 e 7). Seu papel é garantir que a mensagem chegue do processo emissor ao processo receptor de ponta a ponta (*end-to-end*).

---

## 🛠️ Função Principal
Sua função central é aceitar os dados das camadas superiores, dividi-los em unidades menores se necessário, passá-los para a camada de Rede e garantir que todas as partes cheguem corretamente à outra extremidade. É aqui que acontece a **multiplexação**, permitindo que vários aplicativos usem a conexão de rede simultaneamente através do conceito de **Portas**.

### O que ela faz na mensagem?
* **Envio (Encapsulamento):** Recebe os **Dados** brutos da Camada 5 (Sessão) e os "quebra" em pedaços menores. Adiciona o cabeçalho (*Header*) de transporte, contendo a Porta de Origem, Porta de Destino e, dependendo do protocolo, números de sequência e mecanismos de controle de erros.
* **Recebimento (Desencapsulamento):** Recebe o **Pacote** da Camada 3, retira o cabeçalho IP e analisa o cabeçalho de transporte. Ela verifica se há erros, reordena os pedaços (se chegaram fora de ordem) e envia os **Dados** limpos e remontados para a porta correta na Camada de Sessão.

---

## 📦 PDU (Protocol Data Unit)
O PDU desta camada recebe dois nomes distintos dependendo do protocolo escolhido para a transmissão:
* **Segmento (*Segment*):** Quando utiliza o protocolo TCP.
* **Datagrama (*Datagram*):** Quando utiliza o protocolo UDP.

---

## ⚙️ Serviço, Interface e Protocolo

### 1. Serviço (O que oferece para a Camada 5)
* **Comunicação Fim-a-Fim:** A camada de transporte das duas máquinas "conversam" diretamente, ignorando os roteadores no meio do caminho (que operam apenas até a camada 3).
* **Confiabilidade (Opcional):** Pode garantir a entrega (retransmitindo pacotes perdidos) e a ordem correta dos dados.
* **Controle de Fluxo e Congestionamento:** Evita sobrecarregar o receptor ou a própria rede com dados rápidos demais.

### 2. Interface (Conexão entre Camadas)
A interface com as camadas superiores é feita através de **Sockets** (a combinação de um Endereço IP + uma Porta lógica). Por exemplo, a porta 80 é a porta padrão para tráfego web, enquanto a porta 502 é clássica para protocolos de automação. A interface com a camada inferior consiste em passar o segmento para a Camada 3 colocar o destino IP.

### 3. Protocolos e Padrões
A grande decisão técnica nesta camada se resume a dois gigantes:
* **TCP (Transmission Control Protocol):** Orientado à conexão. Realiza o *Three-Way Handshake* para estabelecer a comunicação antes de enviar qualquer dado. Garante entrega, ordem e integridade. É como uma chamada telefônica formal com aviso de recebimento.
* **UDP (User Datagram Protocol):** Não orientado à conexão. Apenas envia os dados o mais rápido possível (*"fire and forget"*). Não garante entrega nem ordem. É como jogar uma carta na caixa de correio torcendo para chegar.

---

## 🛰️ Elementos de Hardware Relacionados
Diferente das camadas inferiores, a Camada 4 não possui um hardware físico dedicado apenas a ela. Ela é puramente implementada em **software pelo Sistema Operacional** (seja o *stack* de rede do Windows ou do kernel Linux).
No entanto, equipamentos de segurança como **Firewalls** e **Balanceadores de Carga (*Load Balancers*)** operam inspecionando portas e conexões ativas operando diretamente nesta camada.

---

## 🔍 Visão de Engenharia: O Trade-off em Sistemas de Controle
Na Engenharia de Controle e Automação, a escolha do protocolo da Camada 4 é uma decisão de projeto crítica. 
Se o objetivo é transmitir um *setpoint* crítico ou alterar a configuração de um CLP, a escolha recai sobre o **TCP** (ex: Modbus TCP). Nesse cenário, a excelência e a garantia de entrega são primordiais, pois a perda de um único comando pode corromper um processo industrial inteiro. 
Por outro lado, se a tarefa for ler um sensor de vazão que atualiza 100 vezes por segundo, a abordagem ideal é o **UDP**. Se a rede perder a leitura número 45, não há tempo para pedir retransmissão, pois a leitura 46 já está chegando. Em malhas de controle de tempo real, um dado atrasado é frequentemente pior do que um dado perdido.