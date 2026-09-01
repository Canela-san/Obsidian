## 1. Conceitos Fundamentais da TOC

* A Teoria das Restrições (TOC) foi idealizada pelo físico Eliyahu Goldratt, tornando-se conhecida mundialmente pelo seu livro "A Meta".


* O conceito baseia-se na premissa de que toda organização possui pelo menos uma restrição que limita a performance do sistema em relação à sua meta global.


* **Tipos de Restrições:**
* **Interna:** Ocorre quando o mercado exige mais do que o sistema pode oferecer, ou seja, o gargalo está dentro da fábrica (ex: falta de capacidade de uma máquina ou de mão de obra).


* **Externa:** Ocorre quando o sistema pode produzir mais do que o mercado suporta comprar, sendo a falta de demanda a verdadeira restrição.




* **"Quebrar a restrição":** Significa elevar a capacidade de fluxo do gargalo atual (seja comprando novos equipamentos ou otimizando processos) até que ele deixe de ser o fator limitante.


* Quando uma restrição é quebrada, o gargalo (o fator limitante) muda automaticamente para outra etapa do sistema produtivo.



## 2. A "Meta" e os Indicadores de Desempenho

A TOC rejeita métricas tradicionais isoladas e foca em três indicadores essenciais para medir se a empresa está se aproximando da sua "Meta":

* **Ganho (Throughput):** É a taxa na qual o sistema gera dinheiro efetivamente através da venda dos seus produtos.


* **Inventário (Estoques):** É todo o dinheiro empregado pela empresa nos bens que pretende vender e que estão parados em espera de processamento.


* **Despesa Operacional:** É todo o dinheiro gasto pelo sistema para conseguir transformar o inventário em ganho.



## 3. Sistema Drum-Buffer-Rope (Tambor-Pulmão-Corda)

É a lógica de programação e controle da produção utilizada pelo software OPT para sincronizar a fábrica.

* **Tambor (Drum):** Representa o Recurso Restritivo Crítico (RRC), ou seja, o gargalo. É ele quem dita o ritmo e a velocidade de produção para toda a fábrica.


* **Pulmão (Buffer):** É uma proteção na forma de tempo ou estoque alocada imediatamente antes do gargalo. Ele garante que o recurso crítico nunca fique ocioso por falta de material.


* *Pulmões secundários:* Devem ser implantados na montagem (para garantir que peças de rotas não-gargalo não atrasem a união com peças da rota do gargalo) e na expedição (para proteger o prazo de entrega ao cliente).




* **Corda (Rope):** É o mecanismo de comunicação (a "corda inelástica") que liga o gargalo ao início da linha. Ela só permite a liberação de novas matérias-primas na mesma velocidade com que o gargalo as processa, controlando o nível de estoque global e evitando a superprodução.



## 4. Os 5 Passos para Gerenciar a TOC

A melhoria contínua na TOC obedece a um ciclo rígido:

1. **Identificar** a restrição (o RRC ou gargalo).


2. **Explorar** a restrição do sistema produtivo, extraindo sua capacidade máxima.


3. **Subordinar** todo o resto do sistema ao ritmo da restrição.


4. **Relaxar (elevar)** a restrição, aumentando sua capacidade instalada.


5. **Voltar ao passo 1**, verificando se o aumento de capacidade fez o gargalo mudar de lugar.



## 5. Princípios Vitais da Teoria das Restrições

O software OPT (Optimized Production Technology) e a TOC quebram paradigmas antigos através de princípios diretos:

* Balanceie o fluxo de produção, e não a capacidade das máquinas.


* A utilização de um recurso que não é gargalo não depende da sua própria disponibilidade, mas sim do ritmo ditado por uma restrição em outra parte do sistema.


* Utilização (o que é estritamente necessário produzir) e ativação (produzir até o limite máximo da máquina) não são sinônimos.


* Uma hora ganha em um recurso gargalo é uma hora real ganha para todo o sistema global.


* Uma hora ganha em um recurso não-gargalo é apenas uma miragem, pois não aumenta o ganho total.


* O lote de transferência (o que é movido para a próxima etapa) frequentemente não deveria ser igual ao lote de processamento.


* O lote de processamento deve ser variável ao longo do sistema, e não fixo.


* Os gargalos determinam o fluxo do sistema; logo, é crucial criar um *time buffer* antes deles para protegê-los.


* A programação de atividades e o cálculo da capacidade devem ser feitos de maneira simultânea, contrariando o MRP tradicional que define os *lead times* antes do planejamento.



## 6. Principais Vantagens

* Foca os investimentos de tempo e dinheiro exclusivamente onde eles darão retorno real (no gargalo), evitando esforços em áreas que não impactam o resultado final.


* Reduz os inventários e estoques em processo, frequentemente com quedas reportadas entre 40% a 75%.


* Reduz e estabiliza o tempo de entrega (*lead time*), com melhorias médias da ordem de 30%.