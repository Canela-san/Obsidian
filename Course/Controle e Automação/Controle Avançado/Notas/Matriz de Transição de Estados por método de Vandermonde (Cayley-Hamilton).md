## 1. O Conceito Base (Teorema de Cayley-Hamilton)

O Teorema de Cayley-Hamilton afirma que toda matriz quadrada satisfaz sua própria equação característica. Uma consequência poderosa disso é que **qualquer função de uma matriz $n \times n$ pode ser escrita como um polinômio de grau $n-1$**.
Para a matriz exponencial $e^{At}$, se a matriz $A$ tem ordem $2 \times 2$ (ou seja, $n = 2$), o grau do polinômio será $2 - 1 = 1$. Portanto:
$$e^{At} = \alpha_0(t)I + \alpha_1(t)A$$
Se fosse $3 \times 3$: $e^{At} = \alpha_0(t)I + \alpha_1(t)A + \alpha_2(t)A^2$, e assim por diante.
O objetivo deste método é simplesmente descobrir quem são os coeficientes escalares **$\alpha_0(t)$** e **$\alpha_1(t)$**.
## 2. A Matriz de Vandermonde

Para encontrar os coeficientes $\alpha$, aplicamos a mesma função polinomial aos **autovalores ($\lambda$)** do sistema. Montamos um sistema de equações trocando a matriz $A$ por $\lambda$:
$$e^{\lambda_1 t} = \alpha_0(t) + \alpha_1(t)\lambda_1$$
$$e^{\lambda_2 t} = \alpha_0(t) + \alpha_1(t)\lambda_2$$
Na forma matricial, isso forma a **Matriz de Vandermonde**:
$$\begin{bmatrix} 1 & \lambda_1 \\ 1 & \lambda_2 \end{bmatrix} \begin{bmatrix} \alpha_0 \\ \alpha_1 \end{bmatrix} = \begin{bmatrix} e^{\lambda_1 t} \\ e^{\lambda_2 t} \end{bmatrix}$$
## 3. Passo a Passo do Cálculo

Vamos calcular $e^{At}$ para a matriz do exemplo anterior:
$$A = \begin{bmatrix}-3 & -2 \\ 2 & 2 \end{bmatrix} \quad \text{com autovalores} \quad \lambda_1 = 1, \, \lambda_2 = -2$$
### Passo 1: Montar o sistema de equações

Substituindo $\lambda_1 = 1$ e $\lambda_2 = -2$ nas equações escalares:
1. $e^{1t} = \alpha_0 + \alpha_1(1) \implies e^t = \alpha_0 + \alpha_1$
2. $e^{-2t} = \alpha_0 + \alpha_1(-2) \implies e^{-2t} = \alpha_0 - 2\alpha_1$
### Passo 2: Isolar e encontrar os coeficientes $\alpha_0$ e $\alpha_1$

Subtraindo a Equação 2 da Equação 1:

  

$$e^t - e^{-2t} = (\alpha_0 - \alpha_0) + (\alpha_1 - (-2\alpha_1))$$

$$e^t - e^{-2t} = 3\alpha_1$$

$$\mathbf{\alpha_1 = \frac{1}{3}(e^t - e^{-2t})}$$

Substituindo $\alpha_1$ de volta na Equação 1:

  $$\alpha_0 = e^t - \alpha_1$$$$\alpha_0 = e^t - \left( \frac{1}{3}e^t - \frac{1}{3}e^{-2t} \right)$$$$\alpha_0 = \frac{3}{3}e^t - \frac{1}{3}e^t + \frac{1}{3}e^{-2t}$$$$\mathbf{\alpha_0 = \frac{2}{3}e^t + \frac{1}{3}e^{-2t}}$$
### Passo 3: Substituir na equação polinomial

Agora, jogamos $\alpha_0$ e $\alpha_1$ na equação original $e^{At} = \alpha_0 I + \alpha_1 A$:
$$e^{At} = \left( \frac{2}{3}e^t + \frac{1}{3}e^{-2t} \right) \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix} + \left( \frac{1}{3}e^t - \frac{1}{3}e^{-2t} \right) \begin{bmatrix} -3 & -2 \\ 2 & 2 \end{bmatrix}$$
### Passo 4: Multiplicar e Somar as Matrizes

- **Linha 1, Coluna 1:** $(\frac{2}{3}e^t + \frac{1}{3}e^{-2t}) \cdot 1 + (\frac{1}{3}e^t - \frac{1}{3}e^{-2t}) \cdot (-3) = \frac{2}{3}e^t + \frac{1}{3}e^{-2t} - e^t + e^{-2t} = \mathbf{-\frac{1}{3}e^t + \frac{4}{3}e^{-2t}}$
- **Linha 1, Coluna 2:** $0 + (\frac{1}{3}e^t - \frac{1}{3}e^{-2t}) \cdot (-2) = \mathbf{-\frac{2}{3}e^t + \frac{2}{3}e^{-2t}}$
- **Linha 2, Coluna 1:** $0 + (\frac{1}{3}e^t - \frac{1}{3}e^{-2t}) \cdot (2) = \mathbf{\frac{2}{3}e^t - \frac{2}{3}e^{-2t}}$
- **Linha 2, Coluna 2:** $(\frac{2}{3}e^t + \frac{1}{3}e^{-2t}) \cdot 1 + (\frac{1}{3}e^t - \frac{1}{3}e^{-2t}) \cdot (2) = \frac{2}{3}e^t + \frac{1}{3}e^{-2t} + \frac{2}{3}e^t - \frac{2}{3}e^{-2t} = \mathbf{\frac{4}{3}e^t - \frac{1}{3}e^{-2t}}$
Agrupando e colocando o termo $\frac{1}{3}$ em evidência, chegamos à matriz final:
$$e^{At} = \frac{1}{3} \begin{bmatrix} 4e^{-2t} - e^{t} & 2e^{-2t} - 2e^{t} \\ -2e^{-2t} + 2e^{t} & -e^{-2t} + 4e^{t} \end{bmatrix}$$
_(Idêntico ao resultado obtido pelo método da Matriz Modal!)_
## Ponto de Atenção: Autovalores Repetidos

O método de Vandermonde é excelente, **mas exige um cuidado extra se o sistema tiver autovalores repetidos (raízes múltiplas)**.
Se $\lambda_1 = \lambda_2 = \lambda$, as duas linhas do sistema de equações seriam idênticas, impossibilitando a resolução de $\alpha_0$ e $\alpha_1$.
Para contornar isso, a segunda equação deve ser obtida derivando a primeira em relação a $\lambda$:
1. Equação normal: $e^{\lambda t} = \alpha_0 + \alpha_1 \lambda$
2. Equação derivada: $\frac{d}{d\lambda}(e^{\lambda t}) = \frac{d}{d\lambda}(\alpha_0 + \alpha_1 \lambda) \implies t e^{\lambda t} = \alpha_1$
Isso resolve o sistema e permite que o método de Vandermonde continue funcionando.