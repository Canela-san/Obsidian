---
Referência: https://youtube.com/playlist?list=PLAudUnJeNg4ssEeZCZ0BOgwflysb7UZmX&si=AJs77KnSJyEw8NGp
Revisão 1: 23-33
---
What is the difference of sequences and series?
A sequence is a group of terms that are arranged in a specific pattern, for exemple: $\{0,2,4,6,8\}$. The logic behind this sequence is that each term is the last term added by 2. A sequence can be separated in different categories by its pattern logic:
- Arithmetic Sequence
- Geometric Sequence
- Harmonic Sequence
- Fibonacci Sequence

The series is defined as the sum of the sequence where the order of elements does not matter. It means that the series is defined as the list of numbers with the addition symbol in between. The series can be classified as a finite series or infinite series which depends on the type of sequence whether it is finite or infinite. Note that, the finite series is a series where the list of numbers has an ending, whereas the infinite series is never-ending. For example, 1+3+5+7+.. is a series. The different types of series are:
- Geometric series
- Harmonic series
- Power series
- Alternating series
- Exponent series (P-series)

Both sequence and series can converge or diverge to a value when tended to infinity, first lest talk about sequences:
A sequence can also be expressed as intervales picked of a continuous function, that is, we can create an continuous functions that is directly linked to the sequence function, for exemple:
Sequence function: $\mathcal f(n)=\frac{\ln n}{n}$
Continuous linked function: $\mathcal f(x)=\frac{\ln x}{x}$
as you can see, the sequence function could be translated as a continuous function.
- If the continuous function has an limited value when tended to infinity, that means that the sequence function also has a limited value when tended t infinity, and they both converges to the same value.
- If the continuous function diverges when tended to infinity, than the theorem does not imply any correlation.
for exemple:
the sequence function: $f(n)=\sin{\pi n}$
continuous linked function: $f(x)=\sin{\pi x}$
in this case the continuous function does not have converges, but the sequence function is zero for all its terms, that means the limit exists and converges to zero.

Theorem: if a sequence is crescente and there is an value that the function will never pass, that necessarily means that this sequence converges.
	The limit $\\lim_{ n \to \infty }\left( 1+\frac{1}{n} \right)^n$ has its existence implied by this theorem. note that this limit is not simple and cannot be found by simple methods, but its possible with series.

the sum of the first n itens of a sequence is:
$$S_{n}=\frac{a_{1}(1-q)^n}{1-q}$$
The sum of infinity terms of a pg with $\mid q\mid<1$ is:
$$S_{\infty}=\frac{a_{1}}{1-q}$$
A series is convergente when the linked sequence tent to zero in infinity, so given the sequence $f(n), n \in \mathbb N$:
$$\sum_{n=1}^{\infty}f(n)\in \mathbb R \implies \lim_{ n \to \infty } f(n) = 0$$
Observe that if a sequence tends to infinity does not imply that the linked series will converge, for exemple there is the harmonic sequence $f(n)=\frac{1}{n}$:  
$$\lim_{ n \to \infty } \frac{1}{n}=0$$
$$\sum_{n=1}^\infty \frac{1}{n} = \infty$$
- Teorema da Comparação
	Sejam $(a_{n})_{n \in \Bbb N}, (b_{n})_{n\in \Bbb N}$ sequencias numéricas com $0\leq a_{n}\leq b_{n}$:
	- Se $\sum_{n=1}^\infty a_{n}$ for divergente $\implies \sum_{n=1}^\infty b_{n}$ diverge
	- Se $\sum_{n=1}^\infty b_{n}$ for convergente $\implies \sum_{n=1}^\infty a_{n}$  converge
	- Exemplo 1:
		sejam as séries:
		$\sum_{n=1}^\infty \frac{1}{2^n+1}$
		$\sum_{n=1}^\infty \frac{1}{2^n}$
		note que $(2^n+1)>2^n$, logo $\frac{1}{2^n+1} < \frac{1}{2^n}$
		$\frac{1}{2^n}$ é uma PG com razão $\frac{1}{2}$, logo converge.
		Já que a série maior $\frac{1}{2^n}$ converge, a série menor $\frac{1}{2^n-1}$ também converge.
	- Exemplo 2:
		Sejam as séries:
		$\sum_{n=1}^\infty \frac{1}{\ln n}$
		$\sum_{n=1}^\infty \frac{1}{n}$ (Série Harmônica)
		temos que $\ln n<n$, logo $\frac{1}{\ln n}> \frac{1}{n}$:
		Já que a série menor $\sum_{n=1}^\infty \frac{1}{n}$ diverge, a série maior $\sum_{n=1}^\infty \frac{1}{\ln n}$ também diverge.
- Teorema da Comparação no Limite
	Sejam $(a_{n})$, $(b_{n})$ sequencias numéricas onde $(0<a_{n})$ e $(0<b_{n})$ $\forall$ $n\geq{1}$
	suponha $\lim_{ n \to \infty } \frac{a_{n}}{b_{n}}=L$
	- Caso 1: $(0<L<\infty)$, então:
		$\sum_{n=1}^\infty a_{n}$ converge $\iff \sum_{n=1}^\infty b_{n}$ converge
		$\sum_{n=1}^\infty a_{n}$ diverge $\iff \sum_{n=1}^\infty b_{n}$ diverge
	- Caso 2: $(L=0)$, então:
		$\sum_{n=1}^\infty a_{n}$ diverge $\implies \sum_{n=1}^\infty b_{n}$ diverge
	- Caso 3: $(L=\infty)$, então:
		$\sum_{n=1}^\infty b_{n}$ diverge $\implies \sum_{n=1}^\infty a_{n}$ diverge
	- Exemplo 1:
		sejam as séries:
		$\sum_{n=1}^\infty \frac{1}{2^n+1}$
		$\sum_{n=1}^\infty \frac{1}{2^n}$
		temos que $\lim_{ n \to \infty } \frac{\frac{1}{n}}{ \frac{1}{2^n-1}}=\lim_{ n \to \infty } \frac{2^n-1}{2^n}=1$
		logo, sabendo que $\sum_{n=1}^\infty \frac{1}{2^n}$ converge, $\sum_{n=1}^\infty \frac{1}{2^n+1}$ também converge.
	- Exemplo 2: aula 10 seno
- Teorema Critério da Integral
	seja: $f[1,+\infty[\to\Bbb R$ , contínua, decrescente e $f(x)>0$ , $\forall \ x\in[1,+\infty[$
	seja $a_{n}=f(n)$:
	**Então $\sum_{n=1}^\infty a_{n}$ converge $\iff \int_{1}^{+\infty}f(x)dx$  converge.**
	- Exemplo:
		$f(n)=\frac{1}{n^\alpha}$ , $\alpha\in\Bbb R$
		para $\alpha=1$, *diverge* (série harmônica)
		Para $\alpha=0$, *diverge* por análise e pelo critério da integral
		Para $\alpha<0$, *diverge* por análise e pelo critério da integral
		Para $\alpha>1$, *converge* pelo critério da integral:
			Note que $f(x)=\frac{1}{x^\alpha}$ é contínua
			$f(x)=x^{-\alpha}$
			$f^′(x)=(-\alpha )x^{-\alpha-1} \iff f(x)$ for decrescente.
			Como a função atende os critérios, podemos fazer o teste da integral
			$$\int_{1}^{+\infty} x^{-\alpha}=\frac{x^{-\alpha+1}}{-\alpha+1}\mid_{1}^{\infty}$$
			$$\lim_{ x \to \infty}\frac{x^{-\alpha+1}}{-\alpha+1} -\frac{1}{1-\alpha}=-\frac{1}{1-\alpha}$$
			Logo a integral *converge*.
- Teorema Critério da Raiz
	Seja $(a_{n})_{n\in\Bbb N}$ , $a_{n}>0$:
	$\lim_{ n \to \infty }\sqrt[n]{2}=L$
	- Caso 1: $(L>1)$
		$(L>1)\implies \sum_{n=1}^{\infty}a_{n}$ *diverge*
	- Caso 2: $(L<1)$
		$(L<1)\implies \sum_{n=1}^{\infty}a_{n}$ *converge*
	- Caso 3: $(L=1)$
		$(L=1)$  *nada se conclui*
	- Exemplo:
		seja a séria provida pela sequência $a_{n}= \frac{n^2}{n^n}$:
		$\sum_{n=1}^{\infty}\frac{n^2}{n^n}$
		pelo Critério da Raiz:
		$\lim_{ n \to \infty }\sqrt[n]{a_{n}}\ =\ \lim_{ n \to \infty }\sqrt[n]{\frac{n^2}{n^n}}\ =\ \lim_{ n \to \infty } \frac{\sqrt[n]{n}\sqrt[n]{n}}{n}$
		$(\lim_{ n \to \infty })\sqrt[n]{n}\to 1$ , logo:
		$\lim_{ n \to \infty }\frac{\sqrt[n]{n}\sqrt[n]{n}}{n}=0$
		segue que $\sum_{n=1}^{\infty}\frac{n^2}{n^n}$ converge
- Teorema Critério da Razão
	Seja $(a_{n})_{n\in\Bbb N}$ , $a_{n}>0$:
	$\lim_{ n \to \infty } \frac{a_{n+1}}{a_{n}}=L$
	- Caso 1: $(L>1)$
		$L>1\implies \sum_{n=1}^{\infty}a_{n}$ *diverge*
	- Caso 2: $(L<1)$
		$L<1\implies \sum_{n=1}^{\infty}a_{n}$ *converge*
	- Caso 3: $(L=1)$
		para $L=1$ *nada se conclui*
	- Exemplo 1:
		Determine se a série a seguir converge ou diverge: $\sum_{n=0}^\infty \frac{3^n}{n!}$:
		$\lim_{ n \to \infty } \frac{a_{n+1}}{a_{n}}=\lim_{ n \to \infty } \frac{\frac{3^{(n+1)}}{(n+1)!}}{\frac{3^n}{n!}}$
		$\lim_{ n \to \infty } \frac{a_{n+1}}{a_{n}}=\lim_{ n \to \infty }\frac{3}{n+1}=0$
		logo a série converge.
- Teorema Critério de Leibniz
	Seja $(a_{n})_{n\in\Bbb N}$ , $a_{n}>0$:
	$\lim_{ n \to \infty } a_n=0$, sendo $a_{n+1}<a_{n}$, isso é, $a_{n}$ é decrescente.
	Então: $\sum_{n=0}^{\infty}(-1)^na_{n}$ *converge*

- Classificação das Séries Numéricas
	- Caso $\sum_{n=0}^{\infty} a_{n}$ seja convergente
		- caso $\sum_{n=0}^{\infty}|a_{n}|$ seja convergente a série recebe o nome de **Absolutamente Convergente**
		- caso $\sum_{n=0}^{\infty}|a_{n}|$ seja divergente a série recebe o nome de **Condicionalmente Convergente**
	- Caso $\sum_{n=0}^{\infty} a_{n}$ seja divergente
		- caso $\sum_{n=0}^{\infty}|a_{n}|$ seja convergente a série recebe o nome de **Absolutamente Divergente**
		- caso $\sum_{n=0}^{\infty}|a_{n}|$ seja divergente a série recebe o nome de **Condicionalmente Divergente**
exemplos disso e series com fatorial aula 18-19

# Séries de Potência
Uma série de potência é uma série do tipo:
$$\sum_{n=0}^{\infty}a_{n}(x-x_{0})^n$$
(dizemos que foi desenhada em torno de x)
- Intervalo de convergência
	Intervalo de convergência é o conjunto dos valores de x para os quais a série converge
- Teorema
	Dado a série $\sum_{n=0}^{\infty}a_{n}(x-x_{0})^n$:
	O intervalo de convergência é necessariamente do tipo:
	-> $I={x_{0}}$
	
	-> $I=\ ]x_{0}-r,x_{0}+r[$
	-> $I=\ [x_{0}-r,x_{0}+r[$
	-> $I=\ ]x_{0}-r,x_{0}+r]$
	-> $I=\ [x_{0}-r,x_{0}+r]$
	
	-> $I=\Bbb R$
- Teorema
	seja $\sum_{n=0}^{\infty}C_{n}(x-x_{0})^n$ uma série de potência com $C_{n}\neq{0}$: $$\lim_{ n \to \infty } \frac{|C_{n+1}|}{|C_{n}|}=L$$
	Então,$$R=\frac{1}{L}$$
	(Apenas quando o x está elevado a n, sem nenhum modificador como $2n$ ou $n^2$)
