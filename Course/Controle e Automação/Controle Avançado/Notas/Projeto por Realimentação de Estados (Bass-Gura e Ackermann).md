# 🎯 Projeto por Realimentação de Estados — Bass-Gura e Ackermann

**Tags:** #controle-avancado #es728 #espaco-de-estados #realimentacao-de-estados #posicionamento-de-polos

**Navegação:** [[ES728 - Controle Avançado de Sistemas|↑ ES728]] · ← [[Formas Canônicas e Transformações]]

## 1. A Ideia do Posicionamento de Polos

Com realimentação de estados $u=-Kx$ (mais uma referência, se houver rastreamento), a dinâmica de malha fechada vira:
$$\dot x = (A-BK)x$$
O objetivo é escolher o ganho $K$ ($1\times n$, caso de uma entrada) para que os autovalores de $A-BK$ — os **polos de malha fechada** — caiam exatamente onde você quer.

> [!important] Pré-requisito
> Posicionamento **arbitrário** de polos só é possível se $(A,B)$ for **controlável** (ver [[Controlabilidade, Observabilidade e Realização Mínima]]). Sem isso, alguns polos ficam presos onde estão, não importa o $K$ escolhido.

---

## 2. Dos Requisitos de Desempenho aos Polos Desejados

Especificações de projeto (sobressinal $\%OS$, tempo de acomodação $t_s$) mapeiam para um par de polos complexos conjugados dominantes via um sistema de 2ª ordem equivalente:
$$\%OS = e^{-\xi\pi/\sqrt{1-\xi^2}} \times 100$$
$$t_s \approx \frac{4}{\xi\omega_n} \quad \text{(critério de 2\%)}$$
$$s_{1,2} = -\xi\omega_n \pm j\omega_n\sqrt{1-\xi^2}$$

Roteiro: (1) $\%OS$ dado → resolva a primeira equação para $\xi$ (numericamente, ou por tabela — não tem forma fechada simples). (2) $t_s$ dado → $\omega_n = \dfrac{4}{\xi t_s}$. (3) monte $s_{1,2}$. Se o sistema tiver ordem $n>2$, os polos "extras" (não-dominantes) costumam ser escolhidos bem mais à esquerda (ex.: parte real $5$ a $10\times$ mais negativa que a dos dominantes), para que sua contribuição decaia rápido e não atrapalhe a resposta ditada pelo par dominante.

> [!tip] Referência rápida
> $\xi=0.707$ dá $\%OS\approx4.3\%$ — um ponto de referência clássico e fácil de lembrar para calibrar se sua conta de $\xi$ está na faixa certa.

---

## 3. Fórmula de Bass-Gura

Sejam $\Delta(s)=s^n+a_{n-1}s^{n-1}+\cdots+a_0$ o polinômio característico de $A$ (malha aberta) e $\Delta_d(s)=s^n+\alpha_{n-1}s^{n-1}+\cdots+\alpha_0$ o polinômio característico **desejado** (construído a partir dos polos-alvo do item 2). O ganho é:
$$K = \big[\alpha_0-a_0,\ \ \alpha_1-a_1,\ \ \dots,\ \ \alpha_{n-1}-a_{n-1}\big]\cdot T^{-1}$$
com $T=M_cW$ **exatamente** a matriz de transformação para forma canônica controlável de [[Formas Canônicas e Transformações]].

**Por que funciona:** na forma canônica controlável, fazer $u=-K_cz$ com $K_c=[\alpha_0-a_0,\dots,\alpha_{n-1}-a_{n-1}]$ simplesmente substitui a última linha de $A_c$ (que é $[-a_0,\dots,-a_{n-1}]$) por $[-\alpha_0,\dots,-\alpha_{n-1}]$ — ou seja, troca o polinômio característico por $\Delta_d(s)$ diretamente, por construção. Como $K=K_cT^{-1}$ (mudança de coordenadas de volta), o resultado vale em qualquer base.

**Exemplo genérico ($n=2$).** $A=\begin{bmatrix}0&1\\-5&-6\end{bmatrix}$, $B=\begin{bmatrix}0\\1\end{bmatrix}$ (controlável — companion form). $\Delta(s)=s^2+6s+5$ ($a_1=6,a_0=5$). Polos desejados: $-2,-3$ $\implies \Delta_d(s)=s^2+5s+6$ ($\alpha_1=5,\alpha_0=6$).
$$M_c=\begin{bmatrix}0&1\\1&-6\end{bmatrix}, \quad W=\begin{bmatrix}6&1\\1&0\end{bmatrix}, \quad T=M_cW=\begin{bmatrix}1&0\\0&1\end{bmatrix}\ (\text{já estava em forma canônica})$$
$$K_c = [\alpha_0-a_0,\ \alpha_1-a_1] = [6-5,\ 5-6] = [1,-1]$$
$$K = K_cT^{-1} = [1,-1]$$
**Conferindo:** $A-BK = \begin{bmatrix}0&1\\-5-1&-6+1\end{bmatrix}=\begin{bmatrix}0&1\\-6&-5\end{bmatrix}$, cujo polinômio característico é $s^2+5s+6=(s+2)(s+3)$ ✓ — os polos foram exatamente para $-2$ e $-3$. (Resultado conferido simbolicamente antes de escrever esta nota.)

---

## 4. Fórmula de Ackermann

Caminho alternativo, sem precisar montar $W$ nem transformar coordenadas explicitamente:
$$K = \begin{bmatrix}0&0&\cdots&0&1\end{bmatrix}\cdot M_c^{-1}\cdot \Delta_d(A)$$
onde $\Delta_d(A) = A^n + \alpha_{n-1}A^{n-1}+\cdots+\alpha_1A+\alpha_0I$ é o polinômio característico **desejado avaliado na matriz $A$** (não em $s$ — é uma matriz $n\times n$ resultante, não um polinômio).

**Mesmo exemplo, conferindo que dá o mesmo $K$:**
$$\Delta_d(A) = A^2+5A+6I$$
$$A^2 = \begin{bmatrix}0&1\\-5&-6\end{bmatrix}\begin{bmatrix}0&1\\-5&-6\end{bmatrix} = \begin{bmatrix}-5&-6\\30&31\end{bmatrix}$$
$$\Delta_d(A) = \begin{bmatrix}-5&-6\\30&31\end{bmatrix}+5\begin{bmatrix}0&1\\-5&-6\end{bmatrix}+6\begin{bmatrix}1&0\\0&1\end{bmatrix} = \begin{bmatrix}1&-1\\5&-5\end{bmatrix}$$
$$M_c^{-1} = \begin{bmatrix}0&1\\1&-6\end{bmatrix}^{-1} = \begin{bmatrix}6&1\\1&0\end{bmatrix} \ \ (\det M_c=-1)$$
$$K = \begin{bmatrix}0&1\end{bmatrix}\begin{bmatrix}6&1\\1&0\end{bmatrix}\begin{bmatrix}1&-1\\5&-5\end{bmatrix} = \begin{bmatrix}1&0\end{bmatrix}\begin{bmatrix}1&-1\\5&-5\end{bmatrix} = [1,-1]$$
Bate exatamente com o resultado de Bass-Gura. ✓

---

## 5. Sempre Verifique

Depois de calcular $K$ por qualquer um dos métodos, **confira** computando os autovalores de $A-BK$ diretamente e comparando com os polos desejados. Se os dois métodos (Bass-Gura e Ackermann) derem o mesmo $K$ — como no exemplo acima — isso já é uma forte confirmação de que a conta está certa.

---

## 🔑 Pontos-Chave para Revisão
- Posicionamento arbitrário de polos exige $(A,B)$ controlável.
- $\%OS$ e $t_s$ mapeiam para $\xi$ e $\omega_n$, que dão os polos dominantes desejados $s_{1,2}=-\xi\omega_n\pm j\omega_n\sqrt{1-\xi^2}$.
- Bass-Gura: $K=[\alpha_0-a_0,\dots,\alpha_{n-1}-a_{n-1}]\cdot T^{-1}$, reaproveitando o $T=M_cW$ da nota de formas canônicas.
- Ackermann: $K=[0\ \cdots\ 0\ 1]\cdot M_c^{-1}\cdot\Delta_d(A)$ — mesmo resultado, caminho mais direto (sem montar $W$).
- Os dois métodos são equivalentes; usá-los como conferência cruzada é uma boa prática de prova.
- **Pergunta de fixação:** se $(A,B)$ não for controlável, o que acontece ao tentar aplicar Bass-Gura ou Ackermann? → $M_c$ não é invertível (posto $<n$), então $M_c^{-1}$ (Ackermann) ou $T^{-1}=(M_cW)^{-1}$ (Bass-Gura) simplesmente não existem — as fórmulas quebram antes mesmo de dar uma resposta errada.
