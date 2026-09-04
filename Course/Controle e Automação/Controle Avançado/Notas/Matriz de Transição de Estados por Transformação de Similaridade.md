## 1. O Método

Quando temos um sistema em espaço de estados, a matriz de transição de estados $e^{At}$ dita a resposta não forçada do sistema. Uma das formas mais analíticas de calculá-la é desacoplando a matriz $A$ original utilizando seus [[Autovalores e Autovetores]], através da relação de similaridade:
$$e^{At} = P e^{Dt} P^{-1}$$
Onde:
- **$A$**: Matriz de estados do sistema.
- **$P$**: Matriz Modal (cujas colunas são os autovetores de $A$).
- **$P^{-1}$**: Inversa da Matriz Modal.
- **$e^{Dt}$**: Matriz diagonal composta pelas exponenciais dos autovalores ($\lambda$) multiplicados pelo tempo ($t$).

## 2. Exemplo Resolvido
### Passo 1: Definir o sistema e encontrar Autovalores/Autovetores

Dada a matriz do sistema:
$$A = \begin{bmatrix}-3 & -2 \\ 2 & 2 \end{bmatrix}$$
Encontramos os autovalores corretos: $\lambda_1 = -2$ e $\lambda_2 = 1$.
A partir deles, calculamos os autovetores associados para montar a Matriz Modal ($P$) e sua inversa ($P^{-1}$):
$$P = \begin{bmatrix}-2 & 1 \\ 1 & -2 \end{bmatrix} \quad \text{e} \quad P^{-1} = \frac{1}{3} \begin{bmatrix}-2 & -1 \\ -1 & -2 \end{bmatrix}$$
### Passo 2: Montar a equação de Similaridade

Substituímos os valores na fórmula $e^{At} = P e^{Dt} P^{-1}$:
$$e^{At} = \begin{bmatrix}-2 & 1 \\ 1 & -2 \end{bmatrix} \begin{bmatrix} e^{-2t} & 0 \\ 0 & e^{t} \end{bmatrix} \frac{1}{3} \begin{bmatrix}-2 & -1 \\ -1 & -2 \end{bmatrix}$$

### Passo 3: Multiplicação (Ordem Sugerida: $P \times e^{Dt}$)

Para manter a organização algébrica, primeiro multiplicamos as duas matrizes iniciais. O escalar $\frac{1}{3}$ pode ser movido para a frente de toda a equação:
$$e^{At} = \frac{1}{3} \left( \begin{bmatrix}-2 & 1 \\ 1 & -2 \end{bmatrix} \begin{bmatrix} e^{-2t} & 0 \\ 0 & e^{t} \end{bmatrix} \right) \begin{bmatrix}-2 & -1 \\ -1 & -2 \end{bmatrix}$$
Resolvendo a primeira multiplicação:
$$e^{At} = \frac{1}{3} \begin{bmatrix} -2e^{-2t} & e^{t} \\ e^{-2t} & -2e^{t} \end{bmatrix} \begin{bmatrix}-2 & -1 \\ -1 & -2 \end{bmatrix}$$
### Passo 4: Multiplicação Final

Agora, multiplicamos a matriz resultante pela inversa $P^{-1}$:

- **Linha 1, Coluna 1:** $(-2e^{-2t})(-2) + (e^{t})(-1) = 4e^{-2t} - e^{t}$
- **Linha 1, Coluna 2:** $(-2e^{-2t})(-1) + (e^{t})(-2) = 2e^{-2t} - 2e^{t}$
- **Linha 2, Coluna 1:** $(e^{-2t})(-2) + (-2e^{t})(-1) = -2e^{-2t} + 2e^{t}$    
- **Linha 2, Coluna 2:** $(e^{-2t})(-1) + (-2e^{t})(-2) = -e^{-2t} + 4e^{t}$

**Matriz de Transição de Estados Final:**
$$e^{At} = \frac{1}{3} \begin{bmatrix} 4e^{-2t} - e^{t} & 2e^{-2t} - 2e^{t} \\ -2e^{-2t} + 2e^{t} & -e^{-2t} + 4e^{t} \end{bmatrix}$$