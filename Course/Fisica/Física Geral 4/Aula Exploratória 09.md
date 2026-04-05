![[Pasted image 20251114141004.png]]
- > Ex 2
	![[Pasted image 20251114134139.png]]
	Claro! Vamos resolver esse exercício de mecânica quântica passo a passo.
	
	Este problema envolve encontrar a probabilidade de localizar um elétron em um poço de potencial infinito. O conceito-chave é que a probabilidade ($P$) de encontrar a partícula em uma determinada região (de $a$ até $b$) é dada pela integral da **densidade de probabilidade**, $|\psi(x)|^2$, nessa região.
	
	$$P(a < x < b) = \int_{a}^{b} |\psi(x)|^2 \,dx$$
	
	---
	
	### ⚛️ 1. A Função de Onda no Estado Fundamental
	
	Para um poço de potencial infinito de tamanho $L$ (de $x=0$ a $x=L$), a função de onda normalizada para o estado $n$ é:
	
	$$\psi_n(x) = \sqrt{\frac{2}{L}} \sin\left(\frac{n\pi x}{L}\right)$$
	
	O problema especifica o estado fundamental, o que significa que usamos $n=1$:
	
	$$\psi_1(x) = \sqrt{\frac{2}{L}} \sin\left(\frac{\pi x}{L}\right)$$
	
	Portanto, a densidade de probabilidade $|\psi_1(x)|^2$ é:
	
	$$|\psi_1(x)|^2 = \left(\sqrt{\frac{2}{L}} \sin\left(\frac{\pi x}{L}\right)\right)^2 = \frac{2}{L} \sin^2\left(\frac{\pi x}{L}\right)$$
	
	Com essa fórmula, podemos resolver os dois itens.
	
	---
	
	### ## a) Probabilidade na região $0 < x < L/4$
	
	Aqui, queremos calcular a probabilidade de $a=0$ até $b=L/4$. Para isso, montamos a integral:
	
	$$P = \int_{0}^{L/4} \frac{2}{L} \sin^2\left(\frac{\pi x}{L}\right) \,dx$$
	
	Passo 1: Simplificar a integral
	
	Podemos tirar a constante $\frac{2}{L}$ para fora:
	
	$$P = \frac{2}{L} \int_{0}^{L/4} \sin^2\left(\frac{\pi x}{L}\right) \,dx$$
	
	Passo 2: Usar uma identidade trigonométrica
	
	Para integrar $\sin^2(\theta)$, usamos a identidade: $\sin^2(\theta) = \frac{1 - \cos(2\theta)}{2}$.
	
	No nosso caso, $\theta = \frac{\pi x}{L}$, então $2\theta = \frac{2\pi x}{L}$.
	
	Substituindo na integral:
	
	$$P = \frac{2}{L} \int_{0}^{L/4} \frac{1}{2} \left[1 - \cos\left(\frac{2\pi x}{L}\right)\right] \,dx$$
	
	O $\frac{2}{L}$ e o $\frac{1}{2}$ se cancelam:
	
	$$P = \frac{1}{L} \int_{0}^{L/4} \left[1 - \cos\left(\frac{2\pi x}{L}\right)\right] \,dx$$
	
	Passo 3: Calcular a integral definida
	
	$$P = \frac{1}{L} \left[ x - \frac{L}{2\pi} \sin\left(\frac{2\pi x}{L}\right) \right]_{0}^{L/4}$$
	
	Agora, aplicamos os limites de integração (limite superior menos o limite inferior):
	
	- Limite superior ($x = L/4$):
	    
	    $\frac{1}{L} \left[ \frac{L}{4} - \frac{L}{2\pi} \sin\left(\frac{2\pi (L/4)}{L}\right) \right]$
	    
	    $= \frac{1}{L} \left[ \frac{L}{4} - \frac{L}{2\pi} \sin\left(\frac{\pi}{2}\right) \right]$
	    
	    Como $\sin(\frac{\pi}{2}) = 1$:
	    
	    $= \frac{1}{L} \left[ \frac{L}{4} - \frac{L}{2\pi} \right] = \frac{1}{4} - \frac{1}{2\pi}$
	    
	- Limite inferior ($x = 0$):
	    
	    $\frac{1}{L} \left[ 0 - \frac{L}{2\pi} \sin\left(\frac{2\pi (0)}{L}\right) \right]$
	    
	    $= \frac{1}{L} \left[ 0 - \frac{L}{2\pi} \sin(0) \right]$
	    
	    Como $\sin(0) = 0$:
	    
	    $= 0$
	    
	
	Resultado (a):
	
	A probabilidade exata é $P = \frac{1}{4} - \frac{1}{2\pi}$.
	
	Calculando o valor numérico:
	
	$P \approx 0.25 - \frac{1}{2 \times 3.14159...} \approx 0.25 - 0.159$
	
	$P \approx 0.091$ ou $9.1\%$
	
	---
	
	#### [b] Probabilidade na região com $\Delta x=0,01L$ e centro em $5L/8$
	
	Aqui, temos uma região $\Delta x$ muito pequena, e o exercício nos dá a dica de que $|\psi(x)|^2$ "varia pouco" nesse intervalo. Isso significa que **não precisamos integrar**.
	
	Podemos _aproximar_ a probabilidade tratando a densidade de probabilidade $|\psi(x)|^2$ como constante dentro desse pequeno intervalo $\Delta x$. A probabilidade é simplesmente o valor da densidade no ponto central ($x_c = 5L/8$) multiplicado pela largura do intervalo ($\Delta x = 0.01L$).
	
	$$P \approx |\psi(x_c)|^2 \cdot \Delta x$$
	
	Passo 1: Calcular a densidade de probabilidade no centro $x_c = 5L/8$
	
	Usamos a fórmula da densidade de probabilidade:
	
	$$|\psi_1(5L/8)|^2 = \frac{2}{L} \sin^2\left(\frac{\pi (5L/8)}{L}\right)$$
	
	$$|\psi_1(5L/8)|^2 = \frac{2}{L} \sin^2\left(\frac{5\pi}{8}\right)$$
	
	Passo 2: Calcular $\sin^2\left(\frac{5\pi}{8}\right)$
	
	Podemos usar a mesma identidade de antes: $\sin^2(\theta) = \frac{1 - \cos(2\theta)}{2}$.
	
	Aqui, $\theta = \frac{5\pi}{8}$, então $2\theta = \frac{10\pi}{8} = \frac{5\pi}{4}$.
	
	$\sin^2\left(\frac{5\pi}{8}\right) = \frac{1 - \cos(5\pi/4)}{2}$
	
	Sabemos que $\cos(5\pi/4) = -\frac{\sqrt{2}}{2}$ (é o cosseno de 225°).
	
	$\sin^2\left(\frac{5\pi}{8}\right) = \frac{1 - (-\sqrt{2}/2)}{2} = \frac{1 + \sqrt{2}/2}{2} = \frac{2 + \sqrt{2}}{4}$
	
	Passo 3: Substituir de volta na fórmula da probabilidade
	
	$$P \approx \left[ \frac{2}{L} \cdot \left(\frac{2 + \sqrt{2}}{4}\right) \right] \cdot \Delta x$$
	
	$$P \approx \left[ \frac{1}{L} \left(\frac{2 + \sqrt{2}}{2}\right) \right] \cdot (0.01L)$$
	
	Os $L$ no numerador e denominador se cancelam:
	
	$$P \approx \left(\frac{2 + \sqrt{2}}{2}\right) \cdot (0.01)$$
	
	Resultado (b):
	
	Calculando o valor numérico (com $\sqrt{2} \approx 1.414$):
	
	$P \approx \left(\frac{2 + 1.414}{2}\right) \cdot 0.01$
	
	$P \approx \left(\frac{3.414}{2}\right) \cdot 0.01$
	
	$P \approx 1.707 \cdot 0.01$
	
	$P \approx 0.0171$ ou $1.71\%$

- 