# ⏱️ Resposta no Tempo e Função de Transferência (Espaço de Estados)

**Tags:** #controle-avancado #es728 #espaco-de-estados #resposta-temporal #funcao-de-transferencia

**Navegação:** [[ES728 - Controle Avançado de Sistemas|↑ ES728]] · ← [[Espaço de Estados - Modelagem e Representação]] · [[Formas Quadráticas e Definição de Sinal|Próxima nota →]]

## 🛠️ A Solução Geral da Equação de Estado

Para $\dot x(t) = Ax(t)+Bu(t)$, a solução geral (por variação de parâmetros, análoga a uma EDO escalar) é:
$$x(t) = \underbrace{e^{At}x(0)}_{\text{resposta a entrada nula}} + \underbrace{\int_0^t e^{A(t-\tau)}Bu(\tau)\,d\tau}_{\text{resposta a estado nulo (convolução)}}$$
$$y(t) = Cx(t) + Du(t)$$

O primeiro termo é a resposta livre (natural, devido só à condição inicial); o segundo é a resposta forçada (devido só à entrada, com $x(0)=0$). Para calcular $e^{At}$, use [[Matriz de Transição de Estados por método de Vandermonde (Cayley-Hamilton)]] ou [[Matriz de Transição de Estados por Transformação de Similaridade]].

---

## 1. Resposta a Entrada Nula ($u(t)=0$)

Só sobra $x(t)=e^{At}x(0)$.

**Exemplo genérico.** Para $A=\begin{bmatrix}0&1\\-3&-4\end{bmatrix}$ (autovalores $-1,-3$), suponha que já se calculou (por Vandermonde, por exemplo):
$$e^{At} = \begin{bmatrix} \frac{3}{2}e^{-t}-\frac{1}{2}e^{-3t} & \frac{1}{2}e^{-t}-\frac{1}{2}e^{-3t} \\ -\frac{3}{2}e^{-t}+\frac{3}{2}e^{-3t} & -\frac{1}{2}e^{-t}+\frac{3}{2}e^{-3t} \end{bmatrix}$$
Com $x(0)=\begin{bmatrix}2\\0\end{bmatrix}$, a resposta livre é simplesmente $e^{At}x(0)$: multiplique a matriz pela primeira coluna e pronto — $x(t) = \begin{bmatrix}3e^{-t}-e^{-3t}\\ -3e^{-t}+3e^{-3t}\end{bmatrix}$.

---

## 2. Resposta Completa com Entrada Degrau

Quando $u(t) = u_0 \cdot \mathbb{1}(t)$ (degrau de amplitude $u_0$, constante) e $A$ é **invertível**, a integral de convolução tem forma fechada:
$$\int_0^t e^{A(t-\tau)}B u_0\,d\tau = A^{-1}\big(e^{At}-I\big)Bu_0$$

(Confere derivando: $\frac{d}{d\tau}\left[-A^{-1}e^{A(t-\tau)}\right] = e^{A(t-\tau)}$, então a integral é $\left[-A^{-1}e^{A(t-\tau)}\right]_0^t = A^{-1}(e^{At}-I)$.)

Logo, a resposta completa fica só em função de $e^{At}$ (que você já sabe calcular) e $A^{-1}$:
$$x(t) = e^{At}x(0) + A^{-1}\big(e^{At}-I\big)Bu_0$$
$$y(t) = Cx(t) + Du(t)$$

**Exemplo genérico.** $A=\begin{bmatrix}-1&0\\0&-2\end{bmatrix}$ (diagonal, então $e^{At}=\begin{bmatrix}e^{-t}&0\\0&e^{-2t}\end{bmatrix}$ e $A^{-1}=\begin{bmatrix}-1&0\\0&-1/2\end{bmatrix}$), $B=\begin{bmatrix}1\\1\end{bmatrix}$, $u_0=1$ (degrau unitário), $x(0)=\begin{bmatrix}1\\0\end{bmatrix}$:
$$A^{-1}(e^{At}-I)B = \begin{bmatrix}-1&0\\0&-1/2\end{bmatrix}\begin{bmatrix}e^{-t}-1\\e^{-2t}-1\end{bmatrix} = \begin{bmatrix}1-e^{-t}\\ \tfrac12(1-e^{-2t})\end{bmatrix}$$
$$x(t) = \begin{bmatrix}e^{-t}\\0\end{bmatrix} + \begin{bmatrix}1-e^{-t}\\ \tfrac12(1-e^{-2t})\end{bmatrix} = \begin{bmatrix}1\\ \tfrac12(1-e^{-2t})\end{bmatrix}$$
Se $C=\begin{bmatrix}1&1\end{bmatrix}$, então $y(t) = 1 + \tfrac12(1-e^{-2t})$.

> [!warning] Se $A$ não for invertível
> Se $A$ tiver autovalor em zero, a fórmula acima não vale (divisão por zero, literalmente). Nesse caso volte para a integral de convolução direta.

---

## 3. Função de Transferência a partir do Espaço de Estados

Aplicando Laplace em $\dot x=Ax+Bu$ com **condições iniciais nulas** ($x(0)=0$):
$$sX(s) = AX(s) + BU(s) \implies X(s) = (sI-A)^{-1}BU(s)$$
$$Y(s) = \big[C(sI-A)^{-1}B + D\big]U(s) \implies \boxed{H(s) = C(sI-A)^{-1}B + D}$$

Essa é a ponte direta entre espaço de estados e função de transferência clássica. Note que os **polos de $H(s)$ são os autovalores de $A$** (as raízes de $\det(sI-A)=0$) — a menos que haja cancelamento polo-zero (ver [[Controlabilidade, Observabilidade e Realização Mínima]]).

**Exemplo genérico.** $A=\begin{bmatrix}0&1\\-2&-3\end{bmatrix}$, $B=\begin{bmatrix}0\\1\end{bmatrix}$, $C=\begin{bmatrix}1&0\end{bmatrix}$, $D=0$:
$$sI-A = \begin{bmatrix}s&-1\\2&s+3\end{bmatrix}, \quad (sI-A)^{-1} = \frac{1}{s^2+3s+2}\begin{bmatrix}s+3&1\\-2&s\end{bmatrix}$$
$$C(sI-A)^{-1}B = \frac{1}{s^2+3s+2}\begin{bmatrix}1&0\end{bmatrix}\begin{bmatrix}s+3&1\\-2&s\end{bmatrix}\begin{bmatrix}0\\1\end{bmatrix} = \frac{1}{s^2+3s+2}\begin{bmatrix}1&0\end{bmatrix}\begin{bmatrix}1\\s\end{bmatrix} = \frac{1}{(s+1)(s+2)}$$

---

## 🔑 Pontos-Chave para Revisão
- Solução geral: $x(t)=e^{At}x(0) + \int_0^t e^{A(t-\tau)}Bu(\tau)d\tau$ — soma de resposta livre (natural) e forçada.
- Para entrada degrau com $A$ invertível: $\int_0^t e^{A(t-\tau)}Bu_0\,d\tau = A^{-1}(e^{At}-I)Bu_0$ (atalho — evita integrar).
- Função de transferência: $H(s) = C(sI-A)^{-1}B+D$; os polos de $H(s)$ são os autovalores de $A$ (salvo cancelamento).
- **Pergunta de fixação:** por que a fórmula do degrau ($A^{-1}(e^{At}-I)Bu_0$) falha se $A$ tiver um autovalor igual a zero? → Porque $A^{-1}$ não existe nesse caso (matriz singular); é preciso voltar à integral de convolução original.
