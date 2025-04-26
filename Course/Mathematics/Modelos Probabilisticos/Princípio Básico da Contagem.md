- #### O Princípio Básico da Contagem
	Suponha que dois experimentos são realizados. Se o experimento 1 pode gerar qualquer um dentre $m$ possíveis resultados e se, para cada resultado deste experimento, houver $n$ possíveis resultados para o experimento 2, então os dois experimentos possuem conjuntamente $mn$ possíveis resultados.
- #### Permutação
	- Motivação
		Quantas configurações (arranjos) ordenadas distintas das letras A, B, C são possíveis de serem formadas?
		As possíveis combinações são:
			ABC, ACB, BAC, BCA, CAB e CBA
		Cada arranjo (configuração) das letras é chamada de uma **permutação**.
		Nesse caso temos 6 permutações
	- No caso geral, se temos $n$ objetos então há:$$n\times(n-1)\times(n-2)\times\dots \times2\times1=n!$$diferentes permutações de $n$ objetos.
- #### Arranjos Repetidos
	- Quantos arranjos diferentes temos para as letras $PEPPER$?
		Existem $(6! =720)$ arranjos (em princípio), mas com repetição
		Há $3$ letras $P$ e $2$ letras $E$
		Para cada arranjo, há $3!\times2!$ permutações que levam ao mesmo arranjo
		Então há:$$\frac{6!}{3! 2!}=60$$arranjos distintos possíveis.
		No caso geral há $$\frac{n!}{n_{1}!n_{2}!\dots n_{r}!}$$permutações distintas de $n$ objetos, dos quais $n1$ são semelhantes, outros $n2$ são semelhantes, ..., outros $n_r$ são semelhantes.
- #### Combinações
	- Motivação
		Quantos diferentes grupos de 3 elementos podem ser selecionados a partir de 5 elementos A,B,C,D e E?
		- Pelo principio básico da contagem, há $5\times 4\times 3$ maneiras de se selecionar um grupo de 3 elementos quando a ordem de seleção ***é relevante***, então cada grupo de 3 elementos é contado 6 vezes.
		- Portanto, a quantidade de grupos distintos de 3 elementos que podem ser selecionados a partir dos 5 elementos são:$$\frac{5\times 4\times 3}{3\times 2\times 1}=10$$
		- Caso geral: A quantidade de maneiras distintas através das quais um grupo de $r$ elementos pode ser selecionado a partir de $n$ elementos $(r\leq n)$ quando a ordem de seleção ***é relevante*** é igual a $$n(n-1)(n-2)\dots(n-r+1)$$
		- Portanto, a quantidade de grupos distintos de $r$ elementos que podem ser formados a partir de um conjunto de $n$ elementos é igual a:$$\frac{n(n-1)(n-2)\dots(n-r+1)}{r!}=\frac{n!}{(n-r)!r!}$$
	- Definições de Combinação:
		- para $r\leq n$ (inteiros não negativos), defini-se $$\binom{n}{k}=\frac{n!}{(n-r)!r!}$$
		- $\binom{n}{k}$ representa o número de combinações possíveis de $n$ objetos em grupos de $r$ elementos de cada vez quando a ordem ***não é relevante***.
	- Convenções:
		1) $0! = 1$
		2) $\binom{n}{i}=0$ quando $i<0$ ou $i>n$
	- Teorema Binomial 
		$$(n+y)^n=\sum_{k=0}^n \binom{n}{k}x^ky^{n-k}$$
- #### Coeficientes Multinomiais
	- dwad
	- 