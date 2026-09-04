# 🔢 Formas Quadráticas e Definição de Sinal

**Tags:** #controle-avancado #es728 #algebra-linear #formas-quadraticas

**Navegação:** [[ES728 - Controle Avançado de Sistemas|↑ ES728]] · ← [[Resposta no Tempo e Função de Transferência (Espaço de Estados)]] · [[Controlabilidade, Observabilidade e Realização Mínima|Próxima nota →]]

## 🛠️ O que é uma Forma Quadrática

Dada uma matriz $A$ ($n\times n$) e um vetor $x\in\mathbb{R}^n$, a forma quadrática associada é o escalar:
$$Q(x) = x^TAx = \langle x, Ax\rangle$$

Ela é classificada pelo sinal que assume para **todo** $x\neq0$:

| Classificação | Condição |
|---|---|
| Positiva definida | $x^TAx > 0$ para todo $x\neq0$ |
| Positiva semidefinida | $x^TAx \geq 0$ para todo $x$ |
| Negativa definida | $x^TAx < 0$ para todo $x\neq0$ |
| Negativa semidefinida | $x^TAx \leq 0$ para todo $x$ |
| Indefinida | $x^TAx$ muda de sinal dependendo de $x$ |

---

## 1. A Pegadinha das Matrizes Não-Simétricas

Regra prática: **"olhe os autovalores de $A$"** — mas isso só funciona diretamente se $A$ for **simétrica**. Se $A$ não é simétrica, os autovalores de $A$ **não dizem nada** sobre o sinal de $x^TAx$. O que importa é sempre a **parte simétrica**:
$$A_s = \frac{A+A^T}{2}$$

**Por quê?** Decompondo $A = A_s + A_a$ (parte simétrica + parte antissimétrica, $A_a=\frac{A-A^T}{2}$), a parte antissimétrica sempre contribui zero à forma quadrática:
$$x^TA_ax = (x^TA_ax)^T = x^TA_a^Tx = -x^TA_ax \implies 2x^TA_ax=0 \implies x^TA_ax=0$$
Logo $x^TAx = x^TA_sx$ sempre — **só a parte simétrica importa**, e é dela que você deve tirar os autovalores.

---

## 2. Critério dos Autovalores (da parte simétrica)

Como $A_s$ é simétrica, seus autovalores são sempre reais, e valem as regras usuais:
- Todos os autovalores de $A_s$ $>0$ $\implies$ $A$ é positiva definida.
- Todos $\geq0$ $\implies$ positiva semidefinida.
- Todos $<0$ $\implies$ negativa definida.
- Todos $\leq0$ $\implies$ negativa semidefinida.
- Sinais mistos $\implies$ indefinida.

## 3. Critério de Sylvester (alternativa, sem calcular autovalores)

Também é possível testar via os **menores principais líderes** de $A_s$ (determinantes dos blocos $1\times1$, $2\times2$, ..., $n\times n$ no canto superior esquerdo): todos positivos $\implies$ positiva definida; alternando de sinal começando negativo ($-,+,-,\dots$) $\implies$ negativa definida. Qualquer outro padrão sem ser um desses dois $\implies$ não é definida (pode ser semidefinida ou indefinida — Sylvester "puro" não distingue esses dois casos tão bem quanto o critério dos autovalores).

---

## 4. Exemplo Resolvido (mostrando a pegadinha na prática)

Considere $A = \begin{bmatrix}1&4\\0&1\end{bmatrix}$ (triangular superior, **não simétrica**).

**Armadilha:** os autovalores de $A$ são as raízes de $\det(A-\lambda I)=(1-\lambda)^2=0$, ou seja $\lambda_{1,2}=1$ — ambos positivos! Seria tentador concluir "positiva definida". **Isso é errado.**

**Caminho certo:** a parte simétrica é
$$A_s = \frac{A+A^T}{2} = \begin{bmatrix}1&2\\2&1\end{bmatrix}$$
cujos autovalores são $\lambda = 1\pm2 = \{3,-1\}$ — **sinais mistos**, logo $A$ é **indefinida**, não positiva definida.

**Confirmando na unha:** tome $x=\begin{bmatrix}1\\-1\end{bmatrix}$:
$$x^TAx = \begin{bmatrix}1&-1\end{bmatrix}\begin{bmatrix}1&4\\0&1\end{bmatrix}\begin{bmatrix}1\\-1\end{bmatrix} = \begin{bmatrix}1&-1\end{bmatrix}\begin{bmatrix}-3\\-1\end{bmatrix} = -2$$
Negativo — apesar dos dois autovalores de $A$ serem positivos. Isso confirma que "autovalores de $A$ direto" é a armadilha errada de se cair.

---

## 5. Por que isso importa em Controle

Duas aplicações que reaparecem no resto da ementa:
- **Estabilidade de Lyapunov:** para provar que $\dot x=Ax$ é estável, procura-se uma função $V(x)=x^TPx$ com $P$ **positiva definida** tal que $\dot V(x)<0$.
- **Controle Ótimo (LQR):** o índice de desempenho $J=\int(x^TQx+u^TRu)\,dt$ exige $Q$ positiva semidefinida e $R$ positiva definida para o problema fazer sentido fisicamente (custo nunca negativo).

---

## 🔑 Pontos-Chave para Revisão
- $x^TAx$ só depende da parte simétrica $A_s=\frac{A+A^T}{2}$ — a parte antissimétrica sempre soma zero.
- Se $A$ não é simétrica, os autovalores de $A$ **não** determinam o sinal da forma quadrática — é preciso testar os autovalores (ou os menores principais) de $A_s$.
- Definida/semidefinida/indefinida se define pelo sinal dos autovalores de $A_s$: todos $>0$, todos $\geq0$, todos $<0$, todos $\leq0$, ou mistos, respectivamente.
- **Pergunta de fixação:** se uma matriz $A$ (não simétrica) tem todos os autovalores positivos, isso garante que $x^TAx>0$ para todo $x$? → Não. É preciso testar os autovalores da parte simétrica $(A+A^T)/2$; os autovalores de $A$ sozinha podem ser totalmente enganosos, como no exemplo acima.
