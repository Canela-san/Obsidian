## 1. O Conceito Base

Para uma matriz quadrada $A$, se multiplicarmos essa matriz por um vetor específico $\mathbf{v}$ e o resultado for apenas uma versão "esticada" ou "encolhida" desse mesmo vetor (sem mudar sua direção), temos a relação:
$$A \mathbf{v} = \lambda \mathbf{v}$$
- **$\lambda$ (Autovalor / Eigenvalue):** É o fator de escala (o quanto o vetor esticou/encolheu ou inverteu).
- **$\mathbf{v}$ (Autovetor / Eigenvector):** É o vetor não nulo cuja direção não muda após a transformação.
## 2. O Passo a Passo do Cálculo

Para calcular na mão (muito comum em provas ou análises algébricas de matrizes de estados), a ordem de resolução é sempre encontrar os autovalores primeiro e, depois, seus autovetores correspondentes.

1. **Monte a Matriz Característica:** Subtraia $\lambda$ da diagonal principal da matriz original $A$. Matematicamente, isso é $(A - \lambda I)$, onde $I$ é a matriz identidade.

2. **Encontre a Equação Característica:** Calcule o determinante dessa nova matriz e iguale a zero: $\det(A - \lambda I) = 0$. O resultado será um polinômio.

3. **Calcule os Autovalores ($\lambda$):** Encontre as raízes desse polinômio. Se a matriz for $2 \times 2$, será uma equação de 2º grau. Se for $3 \times 3$, de 3º grau, etc.

4. **Monte o Sistema para cada $\lambda$:** Para cada autovalor encontrado, substitua o valor numérico de $\lambda$ na equação $(A - \lambda I)\mathbf{v} = 0$.

5. **Calcule os Autovetores ($\mathbf{v}$):** Resolva o sistema linear homogêneo resultante para encontrar o vetor $\mathbf{v}$. O sistema sempre terá infinitas soluções (variáveis livres), então você arbitra um valor (como 1) para encontrar a direção base do vetor.
## 3. Exemplo Prático Resolvido
Vamos calcular para a matriz do sistema $A = \begin{bmatrix} 2 & 1 \\ 1 & 2 \end{bmatrix}$.

**Passo 1 e 2: Equação Característica**
Subtraímos $\lambda$ da diagonal e calculamos o determinante:
$$\det \left( \begin{bmatrix} 2-\lambda & 1 \\ 1 & 2-\lambda \end{bmatrix} \right) = 0$$
Multiplicando cruzado (determinante $2 \times 2$):
$$(2-\lambda)(2-\lambda) - (1)(1) = 0$$
$$4 - 4\lambda + \lambda^2 - 1 = 0$$
$$\lambda^2 - 4\lambda + 3 = 0$$
**Passo 3: Encontrar os Autovalores**
Resolvendo a equação de 2º grau (por Bhaskara ou soma e produto):
- $\lambda_1 = 3$
- $\lambda_2 = 1$
**Passo 4 e 5: Autovetor para $\lambda_1 = 3$**

Substituímos $\lambda = 3$ na matriz $(A - \lambda I)$:
$$\begin{bmatrix} 2-3 & 1 \\ 1 & 2-3 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \end{bmatrix}$$
$$\begin{bmatrix} -1 & 1 \\ 1 & -1 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \end{bmatrix}$$
Isso nos dá a equação: $-x_1 + x_2 = 0 \implies x_1 = x_2$.

Arbitrando $x_1 = 1$, temos $x_2 = 1$. O primeiro autovetor é:
$$\mathbf{v}_1 = \begin{bmatrix} 1 \\ 1 \end{bmatrix}$$
**Passo 4 e 5: Autovetor para $\lambda_2 = 1$**
Substituímos $\lambda = 1$ na matriz $(A - \lambda I)$:
$$\begin{bmatrix} 2-1 & 1 \\ 1 & 2-1 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \end{bmatrix}$$
$$\begin{bmatrix} 1 & 1 \\ 1 & 1 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \end{bmatrix}$$
Isso nos dá a equação: $x_1 + x_2 = 0 \implies x_1 = -x_2$.
Arbitrando $x_2 = 1$, temos $x_1 = -1$. O segundo autovetor é:
$$\mathbf{v}_2 = \begin{bmatrix} -1 \\ 1 \end{bmatrix}$$
## 4. Aplicação: Por que isso é a base de Controle de Sistemas?
Quando você modela a dinâmica de um sistema físico usando a representação em **Espaço de Estados** ($\dot{\mathbf{x}} = A\mathbf{x} + B\mathbf{u}$), a matriz $A$ (matriz dinâmica ou matriz do sistema) guarda todos os segredos do comportamento natural do sistema.

- **Autovalores = Polos do Sistema:** Eles determinam a **estabilidade**. Se qualquer autovalor da matriz $A$ tiver parte real positiva (em tempo contínuo), o sistema é instável (explode para o infinito). Se todos tiverem parte real negativa, o sistema é assintoticamente estável. Eles também ditam a velocidade da resposta e a frequência de oscilação (se houver parte imaginária).

- **Autovetores = Modos do Sistema:** Eles ditam as **direções geométricas** no espaço de estados onde essas dinâmicas ocorrem. Ao colocar os autovetores em uma matriz de transformação (Matriz Modal), você consegue "desacoplar" o sistema (diagonalizar a matriz $A$), permitindo analisar e controlar múltiplas variáveis complexas como se fossem sistemas independentes de 1ª ordem.
- Veja também: [[Autovetores Generalizados e a Forma de Jordan]]