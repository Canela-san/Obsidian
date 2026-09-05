# 📝 Gabarito Comentado — Lista 1 (Prova 1) — ES728

**Tags:** #controle-avancado #es728 #gabarito #prova1

**Navegação:** [[ES728 - Controle Avançado de Sistemas|↑ ES728]] · [[Plano de Estudos - Lista 1 (Prova 1)]]

> [!warning] Como usar este gabarito
> Resolva o exercício **sozinho primeiro**, usando as notas de teoria ([[Plano de Estudos - Lista 1 (Prova 1)|ver mapeamento tema→nota]]). Use esta nota só para **conferir** sua resposta depois. Todas as contas abaixo foram verificadas simbolicamente (SymPy) antes de escrever, mas gabarito nenhum é 100% à prova de erro de digitação — se algo não bater, desconfie dos dois lados e refaça na mão.

---

## Tema 1 — Autovalores, Autovetores e Forma de Jordan

### Exercício 1
$A=\begin{bmatrix}-1&1\\-8&5\end{bmatrix}$. Polinômio característico: $\det(sI-A)=(s+1)(s-5)+8=s^2-4s+3=(s-1)(s-3)$.

**Autovalores:** $s_1=1,\ s_2=3$.

Para $s_1=1$: $(A-1\cdot I)v=0 \Rightarrow \begin{bmatrix}-2&1\\-8&4\end{bmatrix}v=0 \Rightarrow v_1=\begin{bmatrix}1\\2\end{bmatrix}$.
Para $s_2=3$: $(A-3I)v=0 \Rightarrow \begin{bmatrix}-4&1\\-8&2\end{bmatrix}v=0 \Rightarrow v_2=\begin{bmatrix}1\\4\end{bmatrix}$.

**Resposta:** $s_1=1,\ v_1=\begin{bmatrix}1\\2\end{bmatrix}$; $\ s_2=3,\ v_2=\begin{bmatrix}1\\4\end{bmatrix}$.

### Exercício 2
$A=\begin{bmatrix}0&1\\-2&3\end{bmatrix}$.

**(a) Equação característica:** $\det(sI-A)=s(s-3)+2=s^2-3s+2=(s-1)(s-2)=0$.

**(b) Autovalores e autovetores:** $\lambda_1=1,\ \lambda_2=2$.
Para $\lambda_1=1$: $\begin{bmatrix}-1&1\\-2&2\end{bmatrix}v=0 \Rightarrow v_1=\begin{bmatrix}1\\1\end{bmatrix}$.
Para $\lambda_2=2$: $\begin{bmatrix}-2&1\\-2&1\end{bmatrix}v=0 \Rightarrow v_2=\begin{bmatrix}1\\2\end{bmatrix}$.

**Resposta:** $\lambda_1=1,\ v_1=\begin{bmatrix}1\\1\end{bmatrix}$; $\ \lambda_2=2,\ v_2=\begin{bmatrix}1\\2\end{bmatrix}$.

### Exercício 3
Usando os autovetores do Exercício 2 como colunas de $Q$:
$$Q=\begin{bmatrix}1&1\\1&2\end{bmatrix}, \quad Q^{-1}=\begin{bmatrix}2&-1\\-1&1\end{bmatrix}$$
$$J=Q^{-1}AQ=\begin{bmatrix}1&0\\0&2\end{bmatrix}$$

**Resposta:** $Q=\begin{bmatrix}1&1\\1&2\end{bmatrix}$, $\ J=\begin{bmatrix}1&0\\0&2\end{bmatrix}$ (autovalores já são distintos, então $J$ é diagonal — não precisa de blocos de Jordan generalizados).

---

## Tema 2 — Matriz de Transição de Estados e Cayley-Hamilton

### Exercício 4
$A=\begin{bmatrix}0&1\\-2&3\end{bmatrix}$, autovalores $\lambda_1=1,\lambda_2=2$ (do Exercício 2).

**(a) Por similaridade:** $e^{At}=Qe^{Jt}Q^{-1} = \begin{bmatrix}1&1\\1&2\end{bmatrix}\begin{bmatrix}e^t&0\\0&e^{2t}\end{bmatrix}\begin{bmatrix}2&-1\\-1&1\end{bmatrix}$.

**(b) Por Vandermonde:** $V=\begin{bmatrix}1&1\\1&2\end{bmatrix}$, $V^{-1}=\begin{bmatrix}2&-1\\-1&1\end{bmatrix}$, $\alpha=V^{-1}\begin{bmatrix}e^t\\e^{2t}\end{bmatrix} \Rightarrow \alpha_0=2e^t-e^{2t},\ \alpha_1=-e^t+e^{2t}$. Depois $e^{At}=\alpha_0I+\alpha_1A$.

Os dois métodos batem (como devem):
$$\boxed{e^{At}=\begin{bmatrix}2e^t-e^{2t} & -e^t+e^{2t}\\ 2e^t-2e^{2t} & -e^t+2e^{2t}\end{bmatrix}}$$

### Exercício 5
**(a) Teorema de Cayley-Hamilton:** toda matriz quadrada satisfaz sua própria equação característica: se $\Delta(s)=s^n+a_{n-1}s^{n-1}+\cdots+a_0$, então $\Delta(A)=A^n+a_{n-1}A^{n-1}+\cdots+a_0I=0$.

**(b)** Para $A=\begin{bmatrix}0&1\\-2&3\end{bmatrix}$: $\Delta(s)=s^2-3s+2$, logo $A^2-3A+2I=0 \Rightarrow I=\frac12(3A-A^2)=A\left(\frac32I-\frac12A\right)$, ou seja $A^{-1}=\frac32I-\frac12A$.

$$\boxed{A^{-1}=\begin{bmatrix}3/2&-1/2\\1&0\end{bmatrix}}$$

**Verificação:** $AA^{-1}=I$. ✓

---

## Tema 3 — Modelagem e Representação em Espaço de Estados

### Exercício 6
Por inspeção direta das equações:
$$\dot x_1=-2x_1+x_2+u_1,\quad \dot x_2=-3x_2+u_1+2u_2$$
$$y_1=x_1+x_2,\quad y_2=2x_1+u_1,\quad y_3=2x_2+u_2$$

$$\boxed{A=\begin{bmatrix}-2&1\\0&-3\end{bmatrix},\ B=\begin{bmatrix}1&0\\1&2\end{bmatrix},\ C=\begin{bmatrix}1&1\\2&0\\0&2\end{bmatrix},\ D=\begin{bmatrix}0&0\\1&0\\0&1\end{bmatrix}}$$

Repare no $D\neq0$: $y_2$ tem o termo $u_1$ puro, e $y_3$ tem o termo $u_2$ puro (transmissão direta).

### Exercício 7
Com $m_1=m_2=k_1=k_2=k_3=1$: $M=I_2$, $K=\begin{bmatrix}2&-1\\-1&2\end{bmatrix}$, $M^{-1}K=\begin{bmatrix}2&-1\\-1&2\end{bmatrix}$. Empilhando $x=[x_1\ x_2\ \dot x_1\ \dot x_2]^T$:

$$\boxed{A=\begin{bmatrix}0&0&1&0\\0&0&0&1\\-2&1&0&0\\1&-2&0&0\end{bmatrix}}$$

(Conferência física: autovalores de $A$ são $\pm j,\ \pm j\sqrt3$ — puramente imaginários, como esperado para um sistema massa-mola sem amortecimento.)

### Exercício 8
Basta mostrar que $C(sI-A)^{-1}B=H(s)$. Para a forma companion $A=\begin{bmatrix}0&1&0\\0&0&1\\-a_0&-a_1&-a_2\end{bmatrix}$, um resultado padrão (fácil de conferir multiplicando $(sI-A)$ pelo vetor candidato) é:
$$C(sI-A)^{-1}\cdot\Delta(s) = \begin{bmatrix}s^2+a_2s+a_1 & s+a_2 & 1\end{bmatrix}, \qquad \Delta(s)=s^3+a_2s^2+a_1s+a_0$$

Chamando $M=\begin{bmatrix}1&0&0\\a_2&1&0\\a_1&a_2&1\end{bmatrix}$ (a matriz do enunciado), a identidade-chave é:
$$\begin{bmatrix}s^2 & s & 1\end{bmatrix}\cdot M = \begin{bmatrix}s^2+a_2s+a_1 & s+a_2 & 1\end{bmatrix}$$
(confira multiplicando — bate exatamente). Ou seja, $C(sI-A)^{-1}\cdot\Delta(s) = [s^2\ s\ 1]\cdot M$, logo $C(sI-A)^{-1} = \dfrac{1}{\Delta(s)}[s^2\ s\ 1]\,M$. Como $B=M^{-1}[b_2\ b_1\ b_0]^T$:
$$C(sI-A)^{-1}B = \frac{1}{\Delta(s)}[s^2\ s\ 1]\,M\,M^{-1}\begin{bmatrix}b_2\\b_1\\b_0\end{bmatrix} = \frac{b_2s^2+b_1s+b_0}{\Delta(s)} = H(s) \ \checkmark$$

**Resposta:** verificado — a estrutura de $B$ (a inversa de $M$) existe exatamente para cancelar o $M$ que aparece em $C(sI-A)^{-1}$, deixando só $[s^2\ s\ 1]\cdot[b_2\ b_1\ b_0]^T=H(s)\Delta(s)$.

---

## Tema 4 — Resposta no Tempo e Função de Transferência

### Exercício 9
$A=\begin{bmatrix}0&1\\-2&4\end{bmatrix}$. Char. poly: $s^2-4s+2=0 \Rightarrow \lambda_{1,2}=2\mp\sqrt2$ (autovalores não são "redondos" neste exercício — faz parte da conta).

**(a)** Por Vandermonde com $\lambda_1=2-\sqrt2,\ \lambda_2=2+\sqrt2$:
$$\boxed{e^{At}=\begin{bmatrix}\left(\tfrac12+\tfrac{\sqrt2}{2}\right)e^{\lambda_1t}+\left(\tfrac12-\tfrac{\sqrt2}{2}\right)e^{\lambda_2t} & -\tfrac{\sqrt2}{4}e^{\lambda_1t}+\tfrac{\sqrt2}{4}e^{\lambda_2t}\\[4pt] \tfrac{\sqrt2}{2}e^{\lambda_1t}-\tfrac{\sqrt2}{2}e^{\lambda_2t} & \left(\tfrac12-\tfrac{\sqrt2}{2}\right)e^{\lambda_1t}+\left(\tfrac12+\tfrac{\sqrt2}{2}\right)e^{\lambda_2t}\end{bmatrix}}$$

**(b)** $x(t)=e^{At}x(0)$ com $x(0)=[1,-1]^T$:
$$\boxed{x_1(t)=\left(\tfrac12+\tfrac{3\sqrt2}{4}\right)e^{\lambda_1t}+\left(\tfrac12-\tfrac{3\sqrt2}{4}\right)e^{\lambda_2t}, \quad x_2(t)=\left(-\tfrac12+\sqrt2\right)e^{\lambda_1t}+\left(-\tfrac12-\sqrt2\right)e^{\lambda_2t}}$$
(conferência numérica: $x(0)=[1,-1]$ ✓, $x(0.3)\approx[0.299,\ -4.241]$)

### Exercício 10
$A=\text{diag}(-2,-3)$ (já diagonal, $e^{At}=\text{diag}(e^{-2t},e^{-3t})$), $B=[1,1]^T$, $u_0=1$ (degrau unitário), $x(0)=[2/3,\ 1/2]^T$.

Usando $x(t)=e^{At}x(0)+A^{-1}(e^{At}-I)B$ (com $A^{-1}=\text{diag}(-1/2,-1/3)$):
$$x(t)=\begin{bmatrix}\tfrac12+\tfrac16e^{-2t}\\[2pt] \tfrac13+\tfrac16e^{-3t}\end{bmatrix}$$

Com $y=[-3\ \ 4]x$:
$$\boxed{y(t) = -\frac16 - \frac12e^{-2t} + \frac23e^{-3t}}$$
(conferência: $y(0)=-1/6-1/2+2/3=0$ ✓; $y(\infty)=-1/6$)

### Exercício 11
$A=\begin{bmatrix}0&1\\-3&-2\end{bmatrix}$, $B=[0,1]^T$, $C=[1,0]$, $D=0$.
$$H(s)=C(sI-A)^{-1}B$$
$$\boxed{H(s) = \frac{1}{s^2+2s+3}}$$

---

## Tema 5 — Formas Quadráticas e Definição de Sinal

### Exercício 12
$A=\begin{bmatrix}8&-4&2\\0&2&4\\0&0&1\end{bmatrix}$ é triangular (não simétrica), autovalores $8,2,1$ (os próprios elementos da diagonal, todos positivos).

A parte simétrica é $A_s=\dfrac{A+A^T}{2}=\begin{bmatrix}8&-2&1\\-2&2&2\\1&2&1\end{bmatrix}$, cujos autovalores são $\approx\{-1.02,\ 3.40,\ 8.63\}$ — **sinais mistos**. Confirmando na unha: para $x=(-2,-3,2)$, $x^TAx=-2<0$, apesar dos autovalores de $A$ serem todos positivos. Logo (c) e (d) são falsas, e (b) é obviamente falsa.

$$\boxed{\text{Resposta: alternativa (a)}}$$

---

## Tema 6 — Controlabilidade, Observabilidade e Realização Mínima

### Exercício 13
**a)** $A=\text{diag}(-4,-5)$, $B=[1,1]^T$. $M_c=[B\ AB]=\begin{bmatrix}1&-4\\1&-5\end{bmatrix}$, $\det=-1\neq0$. **Controlável.**

**b)** $A=\begin{bmatrix}0&-10\\1&-2\end{bmatrix}$, $B=[1,2]^T$. $AB=[-20,-3]^T$, $M_c=\begin{bmatrix}1&-20\\2&-3\end{bmatrix}$, $\det=37\neq0$. **Controlável.**

### Exercício 14
**a)** $A=\text{diag}(-4,-5)$, $C=[1,1]$. $M_o=\begin{bmatrix}1&1\\-4&-5\end{bmatrix}$, $\det=-1\neq0$. **Observável.**

**b)** $A=\text{diag}(-4,-5)$, $C=[1,0]$. $M_o=\begin{bmatrix}1&0\\-4&0\end{bmatrix}$, $\det=0$. **Não observável** (o modo $-5$ nunca aparece em $y$, já que $C$ só lê $x_1$).

### Exercício 15
$A=\begin{bmatrix}-1&1\\6&-2\end{bmatrix}$, $B=[1,2]^T$, $C=[1,1]$.

**(a)** $\Delta(s)=(s+1)(s+2)-6=s^2+3s-4=(s+4)(s-1)$. Autovalores: $s=-4,\ 1$. **Não é estável** (o polo em $s=1$ tem parte real positiva).

**(b)** $AB = [1,2]^T$ (igual a $B$!). $M_c=\begin{bmatrix}1&1\\2&2\end{bmatrix}$, colunas proporcionais, $\det=0$. **Não controlável.**

**(c)** Teste PBH em cada autovalor: em $s=1$ (instável), $\text{rank}[sI-A\ \ B]=2$ (modo controlável); em $s=-4$ (estável), $\text{rank}[sI-A\ \ B]=1$ (modo **não** controlável). Como o único modo não controlável ($s=-4$) já é estável, **o sistema é estabilizável** (o modo "fora de alcance" não atrapalha, e o modo instável $s=1$ pode ser levado a zero via $K$).

### Exercício 16
$A=\begin{bmatrix}0&1\\-2&-3\end{bmatrix}$, $B=[0,1]^T$, $C=[1,1]$.
$$H(s)=C(sI-A)^{-1}B = \frac{s+1}{(s+1)(s+2)} = \frac{1}{s+2}$$
Há cancelamento polo-zero em $s=-1$! Conferindo: $M_c$ tem posto 2 (controlável — sempre vale aqui), mas $M_o=\begin{bmatrix}1&1\\-2&-2\end{bmatrix}$ tem posto 1 (**não observável**) — o modo $s=-1$ é o que está "escondido".

$$\boxed{\text{Realização mínima (ordem 1): } A=-2,\ B=1,\ C=1 \ \ (\dot x=-2x+u,\ y=x)}$$

### Exercício 17 — Por Inspeção

**a)** Blocos de Jordan: $\lambda=-1$ (bloco $3\times3$, linhas 1-3), $\lambda=-2$ (bloco $2\times2$, linhas 4-5).
- *Controlabilidade:* última linha do bloco $\lambda=-1$ é a linha 3 de $B$, que vale $0$ → **falha**. (Última linha do bloco $\lambda=-2$, linha 5 de $B$, vale $1\neq0$, mas já não importa.)
- *Observabilidade:* primeira coluna do bloco $\lambda=-1$ é a entrada 1 de $C$, que vale $0$ → falha. Primeira "coluna" do bloco $\lambda=-2$ é a entrada 4 de $C$, que também vale $0$ → falha.

$$\boxed{\text{Não controlável, não observável}}$$

**b)** $A=\text{diag}(-1,-2)$ (blocos $1\times1$), $B=[1,1]^T$ (ambos $\neq0$), $C=[1,1]$ (ambos $\neq0$).

$$\boxed{\text{Controlável e observável}}$$

**c)** Blocos: $\lambda_1$ tem um bloco $3\times3$ (linhas 1-3) **e** um bloco $1\times1$ (linha 4) — dois blocos, multiplicidade geométrica 2. $\lambda_2$ tem um único bloco $3\times3$ (linhas 5-7).
- *Controlabilidade:* últimas linhas dos blocos de $\lambda_1$ são as linhas 3 e 4 de $B$: $[0,1,0]$ e $[0,0,1]$ — não-nulas e linearmente independentes ✓. Última linha do bloco $\lambda_2$ é a linha 7 de $B$: $[0,0,1]$, não-nula ✓. **Controlável.**
- *Observabilidade:* primeiras colunas dos blocos de $\lambda_1$ são as colunas 1 e 4 de $C$: $[1,1,0]^T$ e $[0,2,3]^T$ — não-nulas e independentes, ok. Mas a primeira coluna do bloco de $\lambda_2$ é a **coluna 5** de $C$, que é $[0,0,0]^T$ — **inteiramente nula**! **Não observável** (falha no modo $\lambda_2$).

$$\boxed{\text{Controlável, não observável}}$$

**d)** Blocos: $\lambda=2$ tem três blocos ($\{1,2\}$ tamanho 2, $\{3\}$ e $\{4\}$ tamanho 1). $\lambda=1$ tem dois blocos ($\{5,6\}$ tamanho 2, $\{7\}$ tamanho 1).
- *Controlabilidade:* linhas de fronteira de $\lambda=2$ são as linhas 2,3,4 de $B$: $[2,1,1],[1,1,1],[3,2,1]$ — determinante $=-1\neq0$, independentes ✓. Linhas de fronteira de $\lambda=1$ são linhas 6,7 de $B$: $[1,0,1]$ e $[1,0,0]$ — não proporcionais, independentes ✓. **Controlável.**
- *Observabilidade:* colunas de fronteira de $\lambda=2$ são colunas 1,3,4 de $C$: $[2,1,1]^T,[1,1,1]^T,[3,2,1]^T$ — determinante $=-1\neq0$, independentes ✓. Colunas de fronteira de $\lambda=1$ são colunas 5,7 de $C$: $[-1,0,0]^T$ e $[1,0,0]^T$ — **proporcionais** (coluna 7 $=-1\times$ coluna 5)! Dependência linear → **não observável** (falha no modo $\lambda=1$, apesar de nenhuma das duas colunas ser individualmente nula).

$$\boxed{\text{Controlável, não observável}}$$

> [!tip] Repare na pegadinha dos itens (c) e (d)
> Em ambos, cada coluna/linha de fronteira é individualmente não-nula — o erro comum é parar por aí e declarar "observável". O que falha é a **independência linear** entre as colunas/linhas de blocos que compartilham o mesmo autovalor.

**e) (só observabilidade)**
1. $A=\text{diag}(-2,5)$, $C=[1,3]$ (blocos $1\times1$, ambas entradas $\neq0$) → **observável**.
2. $A$ com blocos $\lambda=2$ (linhas 1-2) e $\lambda=3$ (linhas 3-4); primeira coluna do bloco $\lambda=2$ é a coluna 1 de $C=\begin{bmatrix}0&1&1&0\\0&1&1&1\end{bmatrix}$, que é $[0,0]^T$ — nula → **não observável**.
3. $A$ com blocos $\lambda=-3$ (linhas 1-2) e $\lambda=1$ (linha 3); colunas de fronteira (col.1 e col.3 de $C$) são $[1,0]^T$ e $[0,-1]^T$, ambas não-nulas, único bloco cada → **observável**.

**f) (só controlabilidade)**
1. $A=\text{diag}(-7,-5,-1)$, linhas de $B$: $[0,1],[4,0],[7,5]$ — todas não-nulas, blocos únicos → **controlável**.
2. $A$ com blocos $\lambda=-3$ (linhas 1-2) e $\lambda=1$ (linha 3); últimas linhas (linha2, linha3) de $B$: $[2,-1]$ e $[0,3]$ — não-nulas → **controlável**.
3. $A=\text{diag}(3,-1,-2)$, $B=[2,1,0]^T$ — a linha 3 (bloco $\lambda=-2$) é **zero** → **não controlável**.
4. $A$ com blocos $\lambda=-4$ (linhas 1-2) e $\lambda=-2$ (linha 3); última linha do bloco $\lambda=-4$ é a linha 2 de $B=[0,0]$ — **inteiramente nula** → **não controlável**.

### Exercício 18
$H(s)=\dfrac{s+3}{(s+1)(s+2)(s+3)}=\dfrac{s+3}{s^3+6s^2+11s+6}$. Montando a forma canônica controlável (ordem 3, **sem** simplificar o cancelamento):
$$A=\begin{bmatrix}0&1&0\\0&0&1\\-6&-11&-6\end{bmatrix},\ B=\begin{bmatrix}0\\0\\1\end{bmatrix},\ C=\begin{bmatrix}3&1&0\end{bmatrix}$$
$M_c$ tem posto 3 (sempre cheio para forma canônica controlável). $M_o$ tem posto **2** (deficiente).

$$\boxed{\text{Controlável (posto 3), não observável (posto 2)} - \text{o modo } s=-3 \text{ é o que cancela e fica invisível na saída}}$$

---

## Tema 7 — Formas Canônicas e Transformações

### Exercício 19 — Forma Canônica Controlável

**a)** $A=\text{diag}(-4,-5)$, $B=[1,0]^T$, $C=[1,0]$. Calculando $H(s)=C(sI-A)^{-1}B$: como $B$ só "acorda" o modo $-4$ (segunda linha de $B$ é zero), o modo $-5$ nunca aparece — de fato, $H(s)=\dfrac{1}{s+4}$ exatamente (grau 1, não 2). Isso é consistente com $M_c$ ter posto 1 (sistema original não é controlável — ver Tema 6).

$$\boxed{\text{Forma canônica controlável (ordem 1): } A_c=-4,\ B_c=1,\ C_c=1}$$

**b)** $A=\begin{bmatrix}0&-10\\1&-2\end{bmatrix}$, $B=[1,2]^T$, $C=[0,1]$. Aqui o sistema é controlável (Ex. 13b), então a ordem se mantém em 2:
$$H(s)=\frac{2s+1}{s^2+2s+10}$$
$$\boxed{A_c=\begin{bmatrix}0&1\\-10&-2\end{bmatrix},\ B_c=\begin{bmatrix}0\\1\end{bmatrix},\ C_c=\begin{bmatrix}1&2\end{bmatrix}}$$

### Exercício 20 — Forma Canônica Observável

**a)** $A=\text{diag}(-4,-5)$, $B=[1,1]^T$, $C=[1,1]$ — este par é observável (Ex. 14a), a ordem se mantém em 2:
$$H(s)=\frac{2s+9}{(s+4)(s+5)}=\frac{2s+9}{s^2+9s+20}$$
$$\boxed{A_o=\begin{bmatrix}0&-20\\1&-9\end{bmatrix},\ B_o=\begin{bmatrix}9\\2\end{bmatrix},\ C_o=\begin{bmatrix}0&1\end{bmatrix}}$$

**b)** $A=\text{diag}(-4,-5)$, $B=[1,0]^T$, $C=[1,0]$ — mesmo sistema do Ex. 19a, que já vimos não ser observável (Ex. 14b): $H(s)=\dfrac{1}{s+4}$.

$$\boxed{\text{Forma canônica observável (ordem 1): } A_o=-4,\ B_o=1,\ C_o=1}$$

> [!info] Por que 19a e 20b deram a mesma resposta?
> Porque é **o mesmo sistema** ($A,B,C$ idênticos nos dois enunciados) — e ele não é controlável nem observável em relação ao modo $-5$, então tanto a forma canônica controlável quanto a observável colapsam para a mesma realização mínima de ordem 1.

### Exercício 21 — Transformação Explícita

**a) Canônica controlável.** $A=\begin{bmatrix}-2&1\\-2&0\end{bmatrix}$, $B=[1,3]^T$, $C=[1,0]$. $\Delta(s)=s^2+2s+2$ ($a_1=2,a_0=2$).
$$M_c=\begin{bmatrix}1&1\\3&-2\end{bmatrix}\ (\det=-5\neq0,\text{ controlável}), \quad W=\begin{bmatrix}2&1\\1&0\end{bmatrix}$$
$$T=M_cW=\begin{bmatrix}3&1\\4&3\end{bmatrix}$$
$$\boxed{\tilde A=T^{-1}AT=\begin{bmatrix}0&1\\-2&-2\end{bmatrix},\ \tilde B=T^{-1}B=\begin{bmatrix}0\\1\end{bmatrix},\ \tilde C=CT=\begin{bmatrix}3&1\end{bmatrix}}$$
(conferência: $H(s)=\frac{s+3}{s^2+2s+2}$ bate nos dois sistemas, antes e depois de $T$)

**b) Canônica observável.** $A=\begin{bmatrix}-2&1\\-2&0\end{bmatrix}$, $B=[1,0]^T$, $C=[1,3]$. Mesmo $\Delta(s)=s^2+2s+2$.
$$M_o=\begin{bmatrix}1&3\\-8&1\end{bmatrix}\ (\det=25\neq0,\text{ observável}), \quad W=\begin{bmatrix}2&1\\1&0\end{bmatrix}$$
$$S=WM_o=\begin{bmatrix}-6&7\\1&3\end{bmatrix}$$
$$\boxed{\tilde A=SAS^{-1}=\begin{bmatrix}0&-2\\1&-2\end{bmatrix},\ \tilde C=CS^{-1}=\begin{bmatrix}0&1\end{bmatrix},\ \tilde B=SB=\begin{bmatrix}-6\\1\end{bmatrix}}$$
(conferência: $H(s)=\frac{s-6}{s^2+2s+2}$ bate nos dois sistemas)

---

## Tema 8 — Projeto por Realimentação de Estados

### Exercício 22
$A=\begin{bmatrix}0&1\\9&0\end{bmatrix}$, $B=[0,-2]^T$. $\%OS=4\%\Rightarrow \xi=\dfrac{-\ln(0.04)}{\sqrt{\pi^2+\ln^2(0.04)}}\approx0.7156$. Com $t_s=1$s (critério 2%): $\omega_n=\dfrac{4}{\xi t_s}\approx5.589$ rad/s.

Polos desejados: $s_{1,2}=-\xi\omega_n\pm j\omega_n\sqrt{1-\xi^2} \approx -4.00\pm j3.904$ (a parte real dá exatamente $-4$, já que $\xi\omega_n=4/t_s=4$ por construção).

$\Delta_d(s)\approx s^2+8s+31.24$. Char. poly de $A$: $s^2-9$ ($a_1=0,a_0=-9$). $M_c=\begin{bmatrix}0&-2\\-2&0\end{bmatrix}$ ($\det=-4$).

$$\boxed{K \approx \begin{bmatrix}-20.12 & -4.00\end{bmatrix}}$$
(conferência: autovalores de $A-BK$ recaem em $-4.00\pm j3.904$ ✓)

### Exercício 23 — Bass-Gura

**a)** $A=\begin{bmatrix}0&1\\-6&-8\end{bmatrix}$, $B=[0,1]^T$, polos desejados $-4,-5$. $\Delta(s)=s^2+8s+6$, $\Delta_d(s)=s^2+9s+20$. Como $A$ já está em forma companion, $M_c=\begin{bmatrix}0&1\\1&-8\end{bmatrix}$ e $T=I$.
$$\boxed{K=\begin{bmatrix}14&1\end{bmatrix}}$$

**b)** $A=\begin{bmatrix}0&1\\-6&0\end{bmatrix}$, $B=[0,1]^T$, polos desejados $-4,-5$. $\Delta(s)=s^2+6$ (note: $a_1=0$), $\Delta_d(s)=s^2+9s+20$.
$$\boxed{K=\begin{bmatrix}14&9\end{bmatrix}}$$

**c)** $A=\begin{bmatrix}0&8\\1&10\end{bmatrix}$, $B=[1,0]^T$, polos desejados $-1\pm i$. $\Delta(s)=s^2-10s-8$, $\Delta_d(s)=s^2+2s+2$. Aqui $M_c=I$ (coincidência da estrutura de $A,B$), $T=W=\begin{bmatrix}-10&1\\1&0\end{bmatrix}$.
$$\boxed{K=\begin{bmatrix}12&130\end{bmatrix}}$$

Em todos os três casos, os autovalores de $A-BK$ batem exatamente com os polos pedidos (conferido).

### Exercício 24 — Ackermann
Repetindo os três itens do Exercício 23 com $K=[0\ \cdots\ 0\ 1]M_c^{-1}\Delta_d(A)$:

$$\boxed{\text{a) } K=[14,\ 1] \qquad \text{b) } K=[14,\ 9] \qquad \text{c) } K=[12,\ 130]}$$

Os três resultados **batem exatamente** com os do Exercício 23 — como deve ser, já que Bass-Gura e Ackermann são duas formas de calcular o mesmo ganho.

---

## 🔑 Conferência Rápida (todas as respostas)

| Ex. | Resposta final |
|---|---|
| 1 | $s=1,3$; $v_1=[1,2]^T,\ v_2=[1,4]^T$ |
| 2 | $s^2-3s+2=0$; $\lambda=1,2$; $v_1=[1,1]^T,\ v_2=[1,2]^T$ |
| 3 | $Q=\begin{bmatrix}1&1\\1&2\end{bmatrix}$, $J=\text{diag}(1,2)$ |
| 4 | $e^{At}=\begin{bmatrix}2e^t-e^{2t}&-e^t+e^{2t}\\2e^t-2e^{2t}&-e^t+2e^{2t}\end{bmatrix}$ |
| 5 | $A^{-1}=\begin{bmatrix}3/2&-1/2\\1&0\end{bmatrix}$ |
| 6 | $A,B,C,D$ — ver acima ($D\neq0$) |
| 7 | $A=\begin{bmatrix}0&0&1&0\\0&0&0&1\\-2&1&0&0\\1&-2&0&0\end{bmatrix}$ |
| 8 | Verificado algebricamente (identidade $[s^2\ s\ 1]M=[\ldots]$) |
| 9 | $\lambda=2\mp\sqrt2$; $e^{At}$ e $x(t)$ acima |
| 10 | $y(t)=-\tfrac16-\tfrac12e^{-2t}+\tfrac23e^{-3t}$ |
| 11 | $H(s)=\dfrac{1}{s^2+2s+3}$ |
| 12 | Alternativa **(a)** |
| 13 | a) controlável; b) controlável |
| 14 | a) observável; b) não observável |
| 15 | instável; não controlável; **estabilizável** |
| 16 | $H(s)=\tfrac1{s+2}$; realização mínima ordem 1 |
| 17 | a) nem cont. nem obs.; b) ambos; c) cont., não obs.; d) cont., não obs.; e) obs./não obs./obs.; f) cont./cont./não cont./não cont. |
| 18 | controlável, não observável |
| 19 | a) ordem 1: $(-4,1,1)$; b) $A_c=\begin{bmatrix}0&1\\-10&-2\end{bmatrix}$ |
| 20 | a) $A_o=\begin{bmatrix}0&-20\\1&-9\end{bmatrix}$; b) ordem 1: $(-4,1,1)$ |
| 21 | a) $T=\begin{bmatrix}3&1\\4&3\end{bmatrix}$; b) $S=\begin{bmatrix}-6&7\\1&3\end{bmatrix}$ |
| 22 | $K\approx[-20.12,\ -4.00]$ |
| 23 | a) $[14,1]$; b) $[14,9]$; c) $[12,130]$ |
| 24 | idêntico ao 23 |
