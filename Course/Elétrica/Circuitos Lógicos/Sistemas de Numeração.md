- Valor da Posição
	- 532
		- 5 -> 500
		- 3 -> 30
		- 2 -> 2
	Um numero $(a_{2}a_{1}a_{0})_{b}$ em qualquer base $b$ será:
		$Valor=a_{2}b^{2}+a_{1}b^{1}+a_{0}b^{0}$
- Código BCD
	O código BCD separa cada digito decimal em um conjunto de 4 bits:
	$12\to (1)(2)\to(0001)(0010)=00010010$
	$57\to (5)(7)\to(0101)(0111)=01010111$
	Apesar de consumir mais bits para representar um numero, essa formação é util para representar números sem perda de precisão, por exemplo o número 0,2 que em binário convencional seria representado por uma dízima, mas em código BCD:
		$0,2\to (0)(2)\to(0000),(0010)=0000,0010$
- Código Gray
	O código gray é gerado por uma operação nos bits:
	- O bit mais significativo é copiado.
	- Os demais bits serão a soma do bit original com o antecessor, ignorando o carry out.
	Exemplo:	Conversão do número 10111010 para gray:
		$10111010_{\ 2}=11100111_{\ gray}$
