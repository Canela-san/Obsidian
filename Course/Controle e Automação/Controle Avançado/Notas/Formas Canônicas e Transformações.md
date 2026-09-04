# 🔄 Formas Canônicas e Transformações

**Tags:** #controle-avancado #es728 #espaco-de-estados #formas-canonicas #transformacao-de-similaridade

**Navegação:** [[ES728 - Controle Avançado de Sistemas|↑ ES728]] · ← [[Controlabilidade, Observabilidade e Realização Mínima]] · [[Projeto por Realimentação de Estados (Bass-Gura e Ackermann)|Próxima nota →]]

Duas perguntas diferentes aparecem sob este tema: (1) como **escrever direto** a forma canônica de um $H(s)$ — já visto em [[Espaço de Estados - Modelagem e Representação]] — e (2) como **transformar** uma realização genérica $(A,B,C)$ qualquer na forma canônica, via uma matriz de similaridade $T$. É o item (2) que fica faltando, e é ele que sustenta o método de Bass-Gura da próxima nota.

Convenção usada abaixo: polinômio característico de $A$ é $\Delta(s)=\det(sI-A)=s^n+a_{n-1}s^{n-1}+\cdots+a_1s+a_0$.

---

## 1. Forma Canônica Controlável — Recapitulando

$$A_c = \begin{bmatrix} 0&1&0&\cdots&0\\ 0&0&1&\cdots&0\\ \vdots&&&\ddots&\vdots\\ 0&0&0&\cdots&1\\ -a_0&-a_1&-a_2&\cdots&-a_{n-1}\end{bmatrix}, \quad B_c=\begin{bmatrix}0\\0\\\vdots\\0\\1\end{bmatrix}$$

## 2. Transformando um Sistema Genérico em Forma Controlável

Se $(A,B)$ é **controlável**, existe $T$ tal que, com $x=Tz$:
$$\tilde A = T^{-1}AT = A_c, \qquad \tilde B = T^{-1}B = B_c$$

A construção de $T$:
$$T = M_c \cdot W$$
onde $M_c=[B\ AB\ \cdots\ A^{n-1}B]$ é a matriz de controlabilidade (em coordenadas originais) e $W$ é a matriz **triangular de Toeplitz** montada com os coeficientes do polinômio característico de $A$ (excluindo o coeficiente líder, que é 1):

$$n=2:\quad W=\begin{bmatrix}a_1&1\\1&0\end{bmatrix} \qquad\qquad n=3:\quad W=\begin{bmatrix}a_1&a_2&1\\a_2&1&0\\1&0&0\end{bmatrix}$$

(Padrão geral: linha $i$ é $[a_i,\ a_{i+1},\ \dots,\ a_{n-1},\ 1,\ 0,\ \dots,\ 0]$, deslocando uma posição a cada linha.)

**Exemplo genérico ($n=2$).** $A=\begin{bmatrix}-6.5&-8.5\\-5.5&-8.5\end{bmatrix}$, $B=\begin{bmatrix}0.5\\0.5\end{bmatrix}$ (valores propositalmente "feios" pra mostrar que o método funciona mesmo fora de casos redondos). Polinômio característico: $\Delta(s)=s^2+15s+6$ (então $a_1=15,\ a_0=6$).
$$M_c = \begin{bmatrix}0.5 & -3.25\\0.5&-3.75\end{bmatrix}, \quad W = \begin{bmatrix}15&1\\1&0\end{bmatrix}$$
$$T = M_c W = \begin{bmatrix}0.5\cdot15-3.25 & 0.5\\0.5\cdot15-3.75&0.5\end{bmatrix} = \begin{bmatrix}4.25&0.5\\3.75&0.5\end{bmatrix}$$
Calculando $T^{-1}AT$ dá exatamente $\begin{bmatrix}0&1\\-6&-15\end{bmatrix}$ — a forma canônica controlável com os mesmos $a_0=6,\ a_1=15$ que já tínhamos calculado. (Fórmula conferida numericamente antes de escrever esta nota.)

---

## 3. Forma Canônica Observável

Dual da controlável (mesmo $\Delta(s)$, coeficientes $b_i$ do numerador de $H(s)=C(sI-A)^{-1}B$):
$$A_o = \begin{bmatrix} 0&0&\cdots&0&-a_0\\ 1&0&\cdots&0&-a_1\\ 0&1&\cdots&0&-a_2\\ \vdots&&\ddots&&\vdots\\ 0&0&\cdots&1&-a_{n-1}\end{bmatrix}, \quad B_o = \begin{bmatrix}b_0\\b_1\\\vdots\\b_{n-1}\end{bmatrix}, \quad C_o = \begin{bmatrix}0&0&\cdots&0&1\end{bmatrix}$$

Repare que $A_o = A_c^T$ e $C_o = B_c^T$ — é literalmente a transposta da forma controlável (por isso "dual").

## 4. Transformando um Sistema Genérico em Forma Observável

Se $(A,C)$ é **observável**, existe $S$ tal que, com $z=Sx$:
$$\tilde A = SAS^{-1} = A_o, \qquad \tilde C = CS^{-1} = C_o$$

$$S = W \cdot M_o$$
usando a **mesma** matriz $W$ de antes (do polinômio característico de $A$) e $M_o=[C;CA;\cdots;CA^{n-1}]$ a matriz de observabilidade.

> [!warning] Direção da transformação
> Repare que para a forma controlável a convenção usual é $x=Tz$ (T multiplicando à direita, $\tilde A=T^{-1}AT$), enquanto para a forma observável é $z=Sx$ (S multiplicando à esquerda, $\tilde A=SAS^{-1}$). São convenções-espelho — confira qual seu professor usa antes da prova, mas o conteúdo (a matriz $W$, a lógica de $M_c$/$M_o$) é o mesmo.

**Exemplo genérico ($n=2$).** $A=\begin{bmatrix}0&1\\-5&-6\end{bmatrix}$, $C=\begin{bmatrix}2&3\end{bmatrix}$. $\Delta(s)=s^2+6s+5$ ($a_1=6,a_0=5$).
$$M_o = \begin{bmatrix}2&3\\-15&-16\end{bmatrix} \ (\text{pois } CA=\begin{bmatrix}-15&-16\end{bmatrix}), \quad W=\begin{bmatrix}6&1\\1&0\end{bmatrix}$$
$$S = WM_o = \begin{bmatrix}6\cdot2-15 & 6\cdot3-16\\2&3\end{bmatrix} = \begin{bmatrix}-3&2\\2&3\end{bmatrix}$$
Conferido: $SAS^{-1}=\begin{bmatrix}0&-5\\1&-6\end{bmatrix}=A_o$ e $CS^{-1}=\begin{bmatrix}0&1\end{bmatrix}=C_o$. ✓

---

## 5. Por que isso importa: a ponte para Bass-Gura

A matriz $T=M_cW$ desta nota **é exatamente** a matriz usada na fórmula de Bass-Gura para posicionamento de polos (próxima nota). Vale a pena guardar o procedimento de montar $T$ como uma ferramenta reutilizável, não como um exercício isolado.

---

## 🔑 Pontos-Chave para Revisão
- Forma canônica controlável: coeficientes do denominador (com sinal trocado) na última linha de $A$; forma observável é a transposta/dual (na última coluna).
- Transformação para forma controlável: $x=Tz$, $T=M_c\cdot W$ ($M_c$=matriz de controlabilidade, $W$=Toeplitz do polinômio característico).
- Transformação para forma observável: $z=Sx$, $S=W\cdot M_o$ (mesma $W$, agora com a matriz de observabilidade).
- A matriz $W$ só depende do polinômio característico de $A$ — é a mesma nas duas transformações.
- **Pergunta de fixação:** por que a matriz $T=M_cW$ só existe (é invertível) se o sistema for controlável? → Porque $W$ é sempre invertível (é triangular com 1's fora da diagonal principal), então $T$ é invertível se e somente se $M_c$ for invertível — que é exatamente a condição de controlabilidade.
