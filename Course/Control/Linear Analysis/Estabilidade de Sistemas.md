- Assintoticamente Estável
	Indica que a resposta do sistema se torna nula com o passar de tempo suficiente.
	Uma expressão mais formal é dizer que a parte real de todos os polos da função de transferência são negativos:
	$$H(s)=K\frac{(s-z_1)(s-z_2)...(s-z_m)}{(s-p_1)(s-p_2)...(s-p_n)}$$
	Então, se para todo $i$, a expressão $Re(p_i)<0$ for verdadeira, o sistema será assintoticamente estável.
	Note que para um sistema invariante no tempo e assintoticamente estável:
	$$\lim_{t \to \infty}y(t)=0$$
- BIBO Estável
	Um sistema é BIBO (Bounded Input Bounded Output) estável se toda entrada limitada produzir uma saída limitada. Um sinal é dito limitado se existe um valor constante M que o sinal nunca ultrapassará, isso é: $|x(t)<M|$, para todo t.
	Um sistema invariante no tempo será BIBO estável, se e somente se,
	$$||h(t)||_1=\int_{-\infty}^{\infty}|h(t)|dt<\infty$$
	ou seja, se sua resposta for absolutamente integrável.
	