# 🎛️ Controlabilidade, Observabilidade e Realização Mínima

**Tags:** #controle-avancado #es728 #espaco-de-estados #controlabilidade #observabilidade

**Navegação:** [[ES728 - Controle Avançado de Sistemas|↑ ES728]] · ← [[Formas Quadráticas e Definição de Sinal]] · [[Formas Canônicas e Transformações|Próxima nota →]]

## 1. Controlabilidade

Um sistema $\dot x=Ax+Bu$ é **controlável** se, para qualquer estado inicial $x(0)$ e qualquer estado final $x_f$, existe uma entrada $u(t)$ que leva o sistema de $x(0)$ a $x_f$ em tempo finito.

**Teste:** monte a **matriz de controlabilidade**
$$M_c = \begin{bmatrix} B & AB & A^2B & \cdots & A^{n-1}B \end{bmatrix}$$
O sistema é controlável $\iff \text{rank}(M_c) = n$.

**Exemplo genérico.** $A=\begin{bmatrix}0&1\\-2&-3\end{bmatrix}$, $B=\begin{bmatrix}0\\1\end{bmatrix}$:
$$M_c = \begin{bmatrix}0&1\\1&-3\end{bmatrix}, \quad \det(M_c)=-1\neq0 \implies \text{controlável.}$$
Já com $B=\begin{bmatrix}1\\0\end{bmatrix}$: $M_c=\begin{bmatrix}1&0\\0&1\cdot(-2)\end{bmatrix}=\begin{bmatrix}1&0\\0&-2\end{bmatrix}$, ainda posto 2 — controlável. Mas se $B=\begin{bmatrix}1\\-2\end{bmatrix}$ (paralelo a uma "direção ruim"): $AB=\begin{bmatrix}-2\\4\end{bmatrix}=-2B$, então $M_c=\begin{bmatrix}1&-2\\-2&4\end{bmatrix}$ tem colunas proporcionais $\implies \det=0 \implies$ **não controlável**.

---

## 2. Observabilidade

Um sistema $(A,C)$ é **observável** se, observando a saída $y(t)$ (e a entrada $u(t)$, conhecida) durante um intervalo finito, é possível determinar univocamente o estado inicial $x(0)$.

**Teste (dual do anterior):** monte a **matriz de observabilidade**
$$M_o = \begin{bmatrix} C \\ CA \\ CA^2 \\ \vdots \\ CA^{n-1} \end{bmatrix}$$
O sistema é observável $\iff \text{rank}(M_o) = n$.

---

## 3. Teste PBH (Popov-Belevitch-Hautus)

Alternativa útil, principalmente quando você já tem os autovalores à mão:
- **Controlabilidade:** $(A,B)$ é controlável $\iff$ $\text{rank}\big[\,\lambda I - A \ \ B\,\big] = n$ para **todo** autovalor $\lambda$ de $A$.
- **Observabilidade:** $(A,C)$ é observável $\iff$ $\text{rank}\begin{bmatrix}\lambda I-A\\C\end{bmatrix} = n$ para **todo** autovalor $\lambda$ de $A$.

Interpretação: um autovalor "escapa" do teste (deixa o posto cair) exatamente quando existe um autovetor esquerdo de $A$ associado a ele que é ortogonal a $B$ (caso controlabilidade) — ou seja, aquele modo não recebe nenhuma "força" da entrada.

---

## 4. Teste "por Inspeção" — Forma Diagonal e Jordan

Quando $A$ já está diagonalizada ou em forma de Jordan, existe um atalho que evita montar $M_c$ ou $M_o$ inteiras (essencial para sistemas grandes, tipo $5\times5$ ou $7\times7$, resolvidos "de cabeça"):

> [!important] Regra (bloco de Jordan com 1's na superdiagonal)
> - **Controlabilidade:** olhe a linha de $B$ alinhada com a **última linha de cada bloco de Jordan**. Se ela for identicamente zero, o sistema **não é controlável**. Se um autovalor tiver **mais de um bloco**, além de cada linha ser não-nula, essas linhas (uma por bloco) precisam ser **linearmente independentes** entre si.
> - **Observabilidade:** olhe a coluna de $C$ alinhada com a **primeira linha de cada bloco de Jordan**. Mesma lógica: precisa ser não-nula, e (se o autovalor repete em blocos separados) as colunas correspondentes precisam ser linearmente independentes.

Por que a última linha do bloco para controlabilidade e a primeira para observabilidade? Num bloco de Jordan com $\lambda$ na diagonal e $1$ na superdiagonal, o estado do **topo** do bloco depende do estado abaixo dele ($\dot x_1=\lambda x_1+x_2$), enquanto o estado do **fundo** do bloco só depende de si mesmo e da entrada ($\dot x_k=\lambda x_k + [\text{linha de }B]u$) — é essa variável de "fundo" que precisa ser alcançada pela entrada. Para observabilidade a lógica é a dual (a variável do topo é a que "carrega" toda a informação da cadeia até a saída).

**Exemplo genérico.** $A=\begin{bmatrix}\lambda_1&1&0\\0&\lambda_1&0\\0&0&\lambda_2\end{bmatrix}$ (bloco $2\times2$ para $\lambda_1$ + bloco $1\times1$ para $\lambda_2$):
- Controlável $\iff$ linha 2 de $B$ (fundo do bloco $\lambda_1$) $\neq0$ **e** linha 3 de $B$ (o bloco $\lambda_2$, sozinho) $\neq0$. A linha 1 de $B$ pode ser zero sem problema.
- Observável $\iff$ coluna 1 de $C$ (topo do bloco $\lambda_1$) $\neq0$ **e** coluna 3 de $C$ $\neq0$. A coluna 2 pode ser zero.

---

## 5. Estabilizabilidade e Detectabilidade

Versões "mais fracas" (e mais realistas) de controlabilidade/observabilidade:
- **Estabilizável:** todo modo **não controlável** já é, por si só, estável ($\text{Re}(\lambda)<0$). Ou seja: os modos "fora de alcance" da entrada não seriam um problema mesmo sem controle.
- **Detectável:** todo modo **não observável** já é estável — os modos "invisíveis" na saída não atrapalham porque decaem sozinhos.

**Atalho prático:** aplique o teste PBH de controlabilidade (item 3) só nos autovalores com $\text{Re}(\lambda)\geq0$ (instáveis ou marginais). Se o teste passar (posto completo) para todos esses, o sistema é estabilizável — não importa o que acontece nos modos já estáveis.

---

## 6. Realização Mínima

Dado um $H(s)$, existem infinitas triplas $(A,B,C)$ que o realizam ($C(sI-A)^{-1}B=H(s)$), com diferentes dimensões de estado $n$. A **realização mínima** é a de menor $n$ possível — e o resultado central é:

> [!important] Um sistema $(A,B,C)$ é uma realização mínima $\iff$ ele é **simultaneamente controlável e observável**.

**Por que isso conecta com cancelamento polo-zero?** Se você monta a forma canônica controlável de um $H(s)$ **antes** de simplificar fatores comuns no numerador/denominador, o resultado é sempre controlável (é propriedade da forma canônica), mas pode **não ser observável** — o fator cancelado "some" da saída sem sumir do estado.

**Exemplo genérico.** $H(s) = \dfrac{s+2}{(s+1)(s+2)}$, que simplifica para $\dfrac{1}{s+1}$. Montando a forma canônica controlável de ordem 2 **sem simplificar** ($a_0=2,a_1=3$ de $(s+1)(s+2)=s^2+3s+2$; $b_0=2,b_1=1$ de $s+2$):
$$A=\begin{bmatrix}0&1\\-2&-3\end{bmatrix}, \quad B=\begin{bmatrix}0\\1\end{bmatrix}, \quad C=\begin{bmatrix}2&1\end{bmatrix}$$
Conferindo: $C(sI-A)^{-1}B = \dfrac{1}{s+1}$ ✓ (o fator $(s+2)$ realmente cancela). A matriz de controlabilidade $M_c=\begin{bmatrix}0&1\\1&-3\end{bmatrix}$ tem posto 2 (sempre vale para forma canônica controlável), mas a de observabilidade $M_o=\begin{bmatrix}2&1\\-2&-1\end{bmatrix}$ tem **posto 1** — o modo em $s=-2$ ficou invisível na saída. **Não é realização mínima.**

**Como achar a realização mínima na prática:**
1. Calcule $H(s)=C(sI-A)^{-1}B+D$ e simplifique cancelando fatores comuns entre numerador e denominador.
2. Construa qualquer forma canônica (ver [[Formas Canônicas e Transformações]]) do $H(s)$ **já simplificado** — a ordem dessa realização (o grau do denominador reduzido) é a dimensão mínima.
3. No exemplo acima, a realização mínima de $H(s)=\frac{1}{s+1}$ é simplesmente $A=-1,\ B=1,\ C=1$ (ordem 1).

---

## 🔑 Pontos-Chave para Revisão
- Controlabilidade: $\text{rank}(M_c)=n$ com $M_c=[B\ AB\ \cdots\ A^{n-1}B]$. Observabilidade: $\text{rank}(M_o)=n$ com $M_o=[C;CA;\cdots;CA^{n-1}]$ (dual).
- Teste PBH: posto de $[\lambda I-A\ \ B]$ (ou $[\lambda I - A; C]$) tem que ser $n$ para cada autovalor $\lambda$.
- Em forma de Jordan: controlabilidade olha a **última linha de $B$** de cada bloco; observabilidade olha a **primeira coluna de $C$** de cada bloco; com blocos repetidos, exige independência linear entre eles.
- Estabilizável = modos não controláveis já são estáveis; detectável = modos não observáveis já são estáveis.
- Realização mínima $\iff$ controlável **e** observável ao mesmo tempo; cancelamento polo-zero na função de transferência é o sintoma de uma realização não-mínima.
- **Pergunta de fixação:** um sistema tem $M_c$ de posto completo mas $M_o$ com posto deficiente. Ele é uma realização mínima de sua função de transferência? → Não — precisa ser controlável **e** observável ao mesmo tempo; aqui a perda de observabilidade indica um cancelamento polo-zero escondido.
