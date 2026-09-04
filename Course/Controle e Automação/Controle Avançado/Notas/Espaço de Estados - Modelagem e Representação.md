# 🧩 Espaço de Estados: Modelagem e Representação

**Tags:** #controle-avancado #es728 #espaco-de-estados #modelagem

**Navegação:** [[ES728 - Controle Avançado de Sistemas|↑ ES728]] · ← [[Matriz de Transição de Estados por Transformação de Similaridade]] · [[Resposta no Tempo e Função de Transferência (Espaço de Estados)|Próxima nota →]]

A representação em espaço de estados descreve um sistema dinâmico por um conjunto **mínimo** de variáveis (o **vetor de estados** $x(t)$) cujo valor no instante $t$, junto com a entrada futura, determina completamente o comportamento futuro do sistema. A forma padrão (caso linear, invariante no tempo) é:
$$\dot{x}(t) = Ax(t) + Bu(t)$$
$$y(t) = Cx(t) + Du(t)$$
onde $x \in \mathbb{R}^n$ é o estado, $u$ a entrada, $y$ a saída, $A$ a matriz dinâmica ($n\times n$), $B$ a matriz de entrada, $C$ a matriz de saída e $D$ a matriz de transmissão direta (feedthrough).

Existem três situações típicas de prova para chegar nessa forma, cobertas abaixo.

---

## 1. Partindo de Equações de Estado já Desacopladas

Se o enunciado já dá um conjunto de equações diferenciais de 1ª ordem (uma para cada estado) mais equações algébricas para as saídas, o trabalho é só **organizar por inspeção**: cada coeficiente de $x_i$ ou $u_j$ vai direto na posição correspondente das matrizes.

**Exemplo genérico.** Considere:
$$\dot x_1 = -3x_1 + 2x_2 + u_1$$
$$\dot x_2 = -x_2 + u_1 - u_2$$
$$y_1 = x_1 - x_2$$
$$y_2 = 3x_1 + u_2$$

Aqui já dá pra ver, olhando cada equação, que:
$$A = \begin{bmatrix} -3 & 2 \\ 0 & -1 \end{bmatrix}, \quad B = \begin{bmatrix} 1 & 0 \\ 1 & -1 \end{bmatrix}$$
$$C = \begin{bmatrix} 1 & -1 \\ 3 & 0 \end{bmatrix}, \quad D = \begin{bmatrix} 0 & 0 \\ 0 & 1 \end{bmatrix}$$

Note que $D \neq 0$: a saída $y_2$ depende diretamente de $u_2$ (transmissão direta), não só dos estados. Esse é o detalhe que mais se perde de vista — sempre cheque se alguma saída tem um termo de entrada "puro" (sem passar pelos estados).

---

## 2. Partindo de Sistemas Físicos de Ordem Superior (ex: Mecânicos)

Sistemas mecânicos com $N$ graus de liberdade (GDL) tipicamente aparecem como uma equação matricial de **2ª ordem no tempo**:
$$M\ddot{q}(t) + C_d\dot q(t) + Kq(t) = F(t)$$
onde $q$ é o vetor de posições ($N\times 1$), $M$ a matriz de massa, $C_d$ de amortecimento e $K$ de rigidez.

Como o espaço de estados exige equações de **1ª ordem**, o truque padrão é **duplicar o estado**, empilhando posição e velocidade:
$$x = \begin{bmatrix} q \\ \dot q \end{bmatrix} \quad (2N \times 1)$$

Derivando e isolando $\ddot q = M^{-1}(F - Kq - C_d\dot q)$, chega-se à forma em blocos:
$$\dot x = \begin{bmatrix} \dot q \\ \ddot q \end{bmatrix} = \underbrace{\begin{bmatrix} 0 & I \\ -M^{-1}K & -M^{-1}C_d \end{bmatrix}}_{A} x + \underbrace{\begin{bmatrix} 0 \\ M^{-1} \end{bmatrix}}_{B} F$$

**Exemplo genérico (2 GDL, sem amortecimento, $F=0$).** Com $m_1=2$, $m_2=1$, $k_1=3$, $k_2=2$ (valores diferentes dos que você tem no seu exercício — troque pelos seus):
$$M = \begin{bmatrix} 2 & 0 \\ 0 & 1 \end{bmatrix}, \quad K = \begin{bmatrix} k_1+k_2 & -k_2 \\ -k_2 & k_2 \end{bmatrix} = \begin{bmatrix} 5 & -2 \\ -2 & 2 \end{bmatrix}$$

$$M^{-1} = \begin{bmatrix} 1/2 & 0 \\ 0 & 1 \end{bmatrix} \implies M^{-1}K = \begin{bmatrix} 5/2 & -1 \\ -2 & 2 \end{bmatrix}$$

Logo, com $x = [q_1\ q_2\ \dot q_1\ \dot q_2]^T$ (4 estados):
$$A = \begin{bmatrix} 0 & 0 & 1 & 0 \\ 0 & 0 & 0 & 1 \\ -5/2 & 1 & 0 & 0 \\ 2 & -2 & 0 & 0 \end{bmatrix}$$

A lógica é sempre a mesma: **bloco identidade** ligando posição a velocidade, e **$-M^{-1}K$** (e $-M^{-1}C_d$, se houver amortecimento) na parte de baixo.

> [!tip] Ordem dos estados
> Alguns professores preferem $x = [q_1\ \dot q_1\ q_2\ \dot q_2\ ...]^T$ (intercalado) em vez de $[q\ \dot q]$ (empilhado). O conteúdo físico é idêntico — só muda a ordem das linhas/colunas de $A$. Confira qual convenção seu professor usa.

---

## 3. Partindo de uma Função de Transferência (Forma Canônica Controlável)

Dada uma função de transferência estritamente própria
$$H(s) = \frac{b_{n-1}s^{n-1} + \dots + b_1 s + b_0}{s^n + a_{n-1}s^{n-1} + \dots + a_1 s + a_0}$$
uma realização em espaço de estados **sempre válida** (mas não única — ver [[Formas Canônicas e Transformações]] para outras) é a **forma canônica controlável**:
$$A = \begin{bmatrix} 0 & 1 & 0 & \cdots & 0 \\ 0 & 0 & 1 & \cdots & 0 \\ \vdots & & & \ddots & \vdots \\ 0 & 0 & 0 & \cdots & 1 \\ -a_0 & -a_1 & -a_2 & \cdots & -a_{n-1} \end{bmatrix}, \quad B = \begin{bmatrix} 0 \\ 0 \\ \vdots \\ 0 \\ 1 \end{bmatrix}, \quad C = \begin{bmatrix} b_0 & b_1 & \cdots & b_{n-1} \end{bmatrix}, \quad D=0$$

Ou seja: os coeficientes do denominador (trocados de sinal) vão na última linha de $A$, e os coeficientes do numerador viram diretamente a linha $C$.

**Para verificar** se um dado $(A,B,C,D)$ realiza um $H(s)$ específico (o tipo de pergunta do Exercício 8), dois caminhos:
1. **Por reconhecimento de padrão:** confira se $A$ tem a estrutura companion acima com $-a_0,-a_1,\dots$ na última linha (ou coluna, se for a forma observável dual) batendo com o denominador, e se $B,C$ têm a cara certa.
2. **Por força bruta:** calcule $\det(sI-A)$ (deve bater com o denominador) e $C(sI-A)^{-1}B + D$ (deve bater com $H(s)$ inteiro) — ver [[Resposta no Tempo e Função de Transferência (Espaço de Estados)]] para a fórmula geral $H(s)=C(sI-A)^{-1}B+D$.

---

## 🔑 Pontos-Chave para Revisão
- O vetor de estados é o conjunto mínimo de variáveis que resume a "memória" do sistema; a forma padrão é $\dot x=Ax+Bu$, $y=Cx+Du$.
- Equações já desacopladas → matrizes por inspeção direta; preste atenção a termos de $u$ aparecendo puro em $y$ (isso é $D\neq0$).
- Sistemas físicos de 2ª ordem ($M\ddot q + C_d\dot q + Kq=F$) → empilhar $x=[q;\dot q]$ e montar $A$ em blocos com $-M^{-1}K$ e $-M^{-1}C_d$.
- Função de transferência → forma canônica controlável: denominador (com sinal trocado) na última linha de $A$, numerador vira $C$.
- **Pergunta de fixação:** por que a forma canônica controlável do item 3 nunca falha em realizar $H(s)$, não importa quem sejam os polos? → Porque $A$ é construída por definição para ter $\det(sI-A)$ igual ao denominador de $H(s)$ — a estrutura companion garante isso automaticamente, sem precisar resolver nada.
