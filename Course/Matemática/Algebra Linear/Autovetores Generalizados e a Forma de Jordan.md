---
aliases: [Autovetores Generalizados, Forma Canônica de Jordan, Cadeias de Jordan, Matriz Modal]
tags: [sistemas-de-controle, espaco-de-estados, algebra-linear, unicamp, eng-controle-automacao]
---
Para manter a alta qualidade e o rigor na análise de sistemas dinâmicos em Engenharia de Controle e Automação, é fundamental compreender as ferramentas de desacoplamento de matrizes que não são totalmente diagonalizáveis. Esta nota sintetiza o conceito de autovetores generalizados, suas formas de cálculo e sua utilidade na transformação do espaço de estados.

## 1. O Papel dos Autovetores no Espaço de Estados
Ao analisar transformações de um espaço nele mesmo, os sistemas lineares são modelados utilizando matrizes quadradas.
* Quando a matriz $A$ opera sobre um vetor especial $x$, o resultado é uma versão escalonada desse mesmo vetor, caracterizada pela relação $Ax = \lambda x$.
* Nesta equação, $x$ representa o autovetor e $\lambda$ o autovalor associado.
* Os $n$ autovalores de um sistema de ordem $n$ são obtidos calculando-se as raízes do polinômio característico, definido pela equação $|A - \lambda I| = 0$.
* Se utilizarmos os autovetores como base vetorial para o espaço de estados de um sistema autônomo ($\dot{x} = Ax$), agrupando-os nas colunas de uma matriz modal $M$, é possível realizar uma transformação de similaridade.
* Essa transformação, calculada como $\dot{\bar{x}} = M^{-1}AM\bar{x}$, permite diagonalizar a matriz e gerar equações diferenciais lineares de primeira ordem totalmente desacopladas.

## 2. Multiplicidades e a Deficiência de Autovetores
Ao solucionar o polinômio característico, alguns autovalores podem ser complexos ou consistir em raízes repetidas. O comportamento analítico de raízes repetidas depende da relação entre duas grandezas:
* **Multiplicidade Algébrica ($m$):** Corresponde à ordem da raiz na equação característica, ou seja, quantas vezes o autovalor se repete matematicamente.
* **Multiplicidade Geométrica ($gm$):** Representa o número de autovetores regulares linearmente independentes que podem ser encontrados para um determinado autovalor. É calculada observando-se a deficiência de posto (degenerescência) da matriz $(A - \lambda I)$.

O fato de um autovalor ser repetido não implica obrigatoriamente na necessidade de vetores generalizados. No entanto, se a multiplicidade geométrica for estritamente menor que a algébrica ($gm < m$), não existirão vetores independentes em número suficiente para diagonalizar o sistema. É nestas situações que precisamos expandir a base com **autovetores generalizados**.

## 3. Cálculo e Estrutura em Cadeia
Existem abordagens estruturadas para encontrar os vetores faltantes.

### Método "Bottom-Up"
Este método constrói a base progressivamente através da resolução de sistemas lineares sequenciais:
1. Encontre as soluções regulares ($x_i$) resolvendo a equação homogênea: $(A - \lambda I)x_i = 0$.
2. Para cada vetor $x_i$ encontrado, resolva a equação não-homogênea para encontrar o próximo vetor da cadeia: $(A - \lambda I)x_{i+1} = x_i$.
3. Se os novos vetores gerados ($x_{i+1}$) forem linearmente independentes de todos os anteriores, eles são classificados como autovetores generalizados.
4. Caso ocorra dependência linear, o processo deve continuar iterativamente resolvendo $(A - \lambda I)x_{i+2} = x_{i+1}$, checando a independência, até que se forme um conjunto completo de $n$ vetores para a matriz modal.

```tikz
\usepackage{tikz}
\begin{document}

\begin{tikzpicture}[node distance=3.5cm, auto, thick, >=stealth, scale=2.5, transform shape]
  \node (x3) [align=center] {$x_3$ \\ \footnotesize (Gen. Ordem 2)};
  \node (x2) [right of=x3, align=center] {$x_2$ \\ \footnotesize (Gen. Ordem 1)};
  \node (x1) [right of=x2, align=center] {$x_1$ \\ \footnotesize (Autovetor Regular)};
  \node (zero) [right of=x1] {$\mathbf{0}$};
  
  \draw[->] (x3) edge node {$(A-\lambda I)$} (x2);
  \draw[->] (x2) edge node {$(A-\lambda I)$} (x1);
  \draw[->] (x1) edge node {$(A-\lambda I)$} (zero);
\end{tikzpicture}

\end{document}
```

### Método "Top-Down"
Essa abordagem envolve o cálculo prévio do **índice** ($\eta_i$) associado ao autovalor $\lambda_i$.
- O índice $\eta_i$ é definido como o menor valor inteiro de $\eta$ tal que o posto algébrico de $(A - \lambda_i I)^\eta = n - m_i$
- Este valor informa diretamente o tamanho máximo do Bloco de Jordan correspondente àquele autovalor.
## 4. Forma Canônica de Jordan
Quando a matriz modal $M$ abriga autovetores generalizados, a transformação de similaridade $M^{-1}AM$ não resulta em uma matriz estritamente diagonal, mas sim em uma matriz diagonal em blocos, conhecida como Forma Canônica de Jordan.

- Um Bloco de Jordan apresenta o autovalor repetido ($\lambda$) na sua diagonal principal.
- Apresenta o valor $1$ em todos os elementos da superdiagonal (imediatamente acima da diagonal principal).
- O restante do bloco é composto exclusivamente por zeros.
- A quantidade de Blocos de Jordan ligados a um autovalor repetido equivale à multiplicidade geométrica desse autovalor (o número de autovetores regulares associados).
- A soma das dimensões de todos os blocos associados a $\lambda$ resultará na sua multiplicidade algébrica.

$$
\begin{bmatrix}
\lambda & 1 & 0 & \dots & 0 \\
0 & \lambda & 1 & \dots & 0 \\
\vdots & \vdots & \ddots & \ddots & \vdots \\
0 & \dots & \dots & \lambda & 1 \\
0 & \dots & \dots & 0 & \lambda \\
\end{bmatrix}
$$

_Modelo estrutural genérico de um Bloco de Jordan.