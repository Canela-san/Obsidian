
**Tags:** #redes #modelo-osi #arquitetura-redes

O Modelo OSI é um modelo conceitual criado pela ISO (International Organization for Standardization) que padroniza as funções de um sistema de telecomunicações ou computação. Ele divide o processo de comunicação em 7 camadas lógicas. 

O grande objetivo do OSI não é ser implementado exatamente como está (o TCP/IP acabou vencendo na prática), mas sim servir como a **referência universal** para entender redes, desenvolver hardwares/softwares interoperáveis e realizar *troubleshooting* (especialmente útil na análise de redes de processos industriais).

---

## 📦 O Fluxo da Informação: Encapsulamento e Desencapsulamento

A essência do modelo OSI é entender como a mensagem viaja de um software para outro. Quando os dados descem pelas camadas (do remetente para a rede), eles passam pelo **Encapsulamento**. Quando sobem (da rede para o destinatário), passam pelo **Desencapsulamento**.

* **Encapsulamento (Transmissão):** Cada camada (da 7 para a 1) recebe a informação da camada superior, adiciona o seu próprio cabeçalho (Header) com informações de controle essenciais para aquela camada, e repassa para a camada de baixo. É como colocar uma carta dentro de um envelope, e esse envelope dentro de uma caixa, e assim por diante.
* **Desencapsulamento (Recepção):** O processo inverso. Cada camada (da 1 para a 7) lê o cabeçalho destinado a ela, executa a sua função, retira o seu cabeçalho (descarta) e entrega apenas a "carga útil" (payload) pura para a camada de cima.

---

## 🧩 Unidades de Dados de Protocolo (PDU)

O **PDU (Protocol Data Unit)** é o nome que a informação recebe em cada camada específica. Ele é a soma dos dados da camada superior mais o cabeçalho (Header) adicionado pela camada atual.

| Camada |   Nome da Camada    |        PDU (Nome do Dado)         | Função Principal (Resumo)                                                           | Link da Nota                   |
| :----: | :-----------------: | :-------------------------------: | :---------------------------------------------------------------------------------- | :----------------------------- |
| **7**  |    **Aplicação**    |         Dados / Mensagem          | Interface direta com o usuário e os aplicativos de rede.                            | [[Camada 7 - Aplicação]]       |
| **6**  |  **Apresentação**   |               Dados               | Tradução, criptografia e compressão dos dados.                                      | [[Camada 6 - Apresentação]]    |
| **5**  |     **Sessão**      |               Dados               | Estabelece, gerencia e encerra conexões (sessões) entre as aplicações.              | [[Camada 5 - Sessão]]          |
| **4**  |   **Transporte**    | Segmento (TCP) ou Datagrama (UDP) | Entrega fim-a-fim, controle de fluxo e correção de erros.                           | [[Camada 4 - Transporte]]      |
| **3**  |      **Rede**       |         Pacote (*Packet*)         | Roteamento e endereçamento lógico (ex: IP) entre redes diferentes.                  | [[Camada 3 - Rede]]            |
| **2**  | **Enlace de Dados** |         Quadro (*Frame*)          | Endereçamento físico (ex: MAC), detecção de erros e acesso ao meio físico.          | [[Camada 2 - Enlace de Dados]] |
| **1**  |     **Física**      |                Bit                | Transmissão pura e bruta dos sinais (elétricos, ópticos ou rádio) pelo meio físico. | [[Camada 1 - Física]]          |

---

## 📐 Conceitos Chaves para as Notas Individuais

Para manter a consistência em cada uma das 7 notas vinculadas acima, lembre-se das seguintes definições ao preencher os tópicos:

1.  **Serviço:** É *o que* a camada faz. O conjunto de primitivas fornecidas pela camada *N* para a camada superior *N+1*.
2.  **Interface:** É *como* a camada superior acessa a camada inferior. Define os parâmetros e as portas pelas quais as informações são passadas entre a camada *N* e a camada *N-1*.
3.  **Protocolo:** São as *regras*. Como a camada *N* do Host A conversa com a camada *N* idêntica no Host B (comunicação par-a-par ou *peer-to-peer*).