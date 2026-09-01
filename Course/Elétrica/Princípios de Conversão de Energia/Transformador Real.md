Excelente escolha! O **Step 2** é onde a teoria encontra a realidade. No Obsidian, o `circuitikz` (via plugin TikZ) é perfeito para isso, pois permite que seus esquemas fiquem com qualidade de livro didático.

---

### Passo 2: O Transformador Real

Diferente do modelo ideal, o transformador real possui imperfeições físicas que resultam em quedas de tensão e dissipação de energia. Para modelar isso, inserimos componentes elétricos que representam cada "defeito" do dispositivo:

#### 1. As 4 Imperfeições Principais

No transformador real, precisamos considerar:

- **Resistência dos Enrolamentos ($R_1, R_2$):** O fio de cobre tem resistência e aquece (Efeito Joule).
    
- **Fluxo de Dispersão ($X_{l1}, X_{l2}$):** Nem todo campo magnético fica "preso" no núcleo; parte se perde no ar ao redor das bobinas.
    
- **Perdas no Núcleo ($R_c$):** Representa as perdas por Histerese e Correntes Parasitas (Foucault) no ferro.
    
- **Corrente de Magnetização ($X_m$):** O núcleo precisa de uma corrente para ser magnetizado (reatância de magnetização).
    

#### 2. O Circuito Equivalente Completo (Modelo T)

Este circuito separa a parte ideal (o acoplamento) das perdas. No seu Obsidian, você pode representar o modelo referido ao primário assim:

```tikz
\usepackage{circuitikz}
\begin{document}

\begin{circuitikz}[american, voltage shift=0.5, scale=1.5, transform shape]

% Primário (Resistência e Reatância de dispersão)
\draw[thick] 
  (0,0) 
  to[V, l=$V_1$] (0,3)
  to[R=$R_1$, i=$I_1$] (2,3) 
  to[L=$jX_1$] (4,3)
  to[short, -*] (5,3);

% Ramo de excitação (Perdas no núcleo e Magnetização) em paralelo
\draw[thick]
  (5,3) to[R=$R_c$, i>_=$I_c$] (5,0)
  to[short, -*] (5,0);

\draw[thick]
  (5,3) -- (7,3) 
  to[L=$jX_m$, i>_=$I_m$] (7,0) 
  -- (5,0);

% Secundário refletido (Resistência, Reatância de dispersão e Carga)
\draw[thick]
  (7,3) to[short, *-] (8,3)
  to[R=$R_2'$] (10,3)
  to[L=$jX_{l2}'$, i=$I_2'$] (12,3)
  to[generic, l=$Z_{carga}'$, v=$V_2'$] (12,0)
  -- (0,0);

\end{circuitikz}
\end{document}
```

#### 3. Reflexão de Parâmetros

Para eliminar o transformador "físico" do desenho e trabalhar apenas com um circuito elétrico comum, "refletimos" os valores do secundário para o primário usando a relação de espiras $a = N_1/N_2$:

- **Tensão:** $V_2' = a \cdot V_2$.
    
- **Corrente:** $I_2' = \frac{I_2}{a}$.
    
- **Impedâncias:** $R_2' = a^2 R_2$ e $X_{l2}' = a^2 X_{l2}$.
    

#### 4. Circuito Equivalente Simplificado

Em muitos exercícios de prova (como os da sua aula), o "Ramo de Excitação" ($R_c$ e $X_m$) é movido para o início ou até ignorado para facilitar os cálculos.

Isso nos dá a **Impedância Equivalente ($Z_{eq}$)**:

$$R_{eq} = R_1 + R_2'$$

$$X_{eq} = X_{l1} + X_{l2}'$$

$$Z_{eq} = R_{eq} + jX_{eq}$$