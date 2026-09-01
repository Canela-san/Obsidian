Para entender as máquinas reais, primeiro criamos um modelo perfeito (teórico) onde nada de ruim acontece. Um transformador ideal é considerado sem perdas.

Premissas do Transformador Ideal:

- **Resistência nula:** As resistências dos enrolamentos de cobre são desprezíveis.
    
- **Permeabilidade infinita:** O núcleo de ferro conduz o campo magnético perfeitamente, logo a corrente de magnetização necessária é nula.
    
- **Sem fugas:** Não há dispersão de fluxo (todo o fluxo magnético gerado pelo primário atravessa o secundário).
    
- **Núcleo perfeito:** Não há perdas no núcleo por correntes parasitas ou histerese.
    

#### Relações Fundamentais

A variável mais importante aqui é a **relação de transformação ($a$)**, que é definida pela proporção entre o número de espiras do primário ($N_1$) e do secundário ($N_2$).

- **Relação de Tensão:** A tensão é diretamente proporcional ao número de espiras. $\frac{\overline{V}_{1}}{\overline{V}_{2}} = \frac{N_{1}}{N_{2}} = a$
    
- **Relação de Corrente:** A corrente é inversamente proporcional ao número de espiras. Isso faz sentido porque a potência ideal se conserva ($S_1 = S_2$, ou $V_1 \cdot I_1 = V_2 \cdot I_2$). $\frac{\overline{I}_{1}}{\overline{I}_{2}} = \frac{N_{2}}{N_{1}} = \frac{1}{a}$

#### Impedância Refletida

Na conversão de energia, muitas vezes precisamos simplificar o circuito inteiro (fonte + trafo + carga) para resolver as equações. Para isso, "transferimos" ou "refletimos" a impedância da carga ($Z_2$), que está no secundário, para o lado do primário.

- **Equação da Reflexão:** A impedância vista pelo primário ($Z_2^{\prime}$) é multiplicada pelo quadrado da relação de espiras. $Z_2^{\prime} = a^2 Z_2$