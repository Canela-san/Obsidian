- Equivalência de Forças
	Mola $F_{k}=kx$
	Amortecedor $F_{c}=c \dot{x}$
	Segunda Lei de Newton $F_{R}=m\ddot{x}$

- exemplo 1 - Sistema Massa Mola

	![[Massa Mola.png|900]]
	A principio vamos desconsiderar a oscilação da superfície $r(t)=0$.
		$F_{k}=-ky(t)$
		$F_{g}=-mg$
		$\sum_{i=1}^{\infty} F_{i}=m \ddot{y}(t)$
	logo:
		$-ky(t)-mg=m \ddot{y}(t)$
		$m\ddot{y}(t)+ky(t)=-mg$
	Para modelar o movimento utilizando uma EDO mais simples devemos adotar um sistema de coordenadas correspondente, nesse caso, o sistema é uma oscilação uniforme de uma coordenada, então o melhor sistema de coordenadas será aquele em torno do ponto médio da oscilação, isso é o ponto de equilíbrio estático $\Delta$:
		$$k\Delta=mg$$
		$$\Delta=\frac{mg}{k}$$
	O novo sistema $x(t)$ será $x(t)=y(t)-\Delta$, $\dot{x}(t)=\dot{y}(t)$, $\ddot{x}(t)=\ddot{y}(t)$
	Reescrevendo a EDO em função de $x$:
		$F_k=-k(x+\Delta)$
		$F_{g}=mg$
		$\sum_{i=1}^{\infty} F_{i}=m \ddot{x}$
		logo,
		$m\ddot{x}+kx+k\left( \frac{mg}{k} \right)=mg$
		$m\ddot{x}+kx=0$
		$\ddot{x}(t)+\omega_{n}^{2}x(t)=0$
	- Solução da EDO $\ddot{x}(t)+\omega_{n}^{2}x(t)=0$:
		- Modelo de resposta 1 -> $x(t)=A\cos(w_{n}t+\phi)$
			$\dot{x}=-A\omega_{n}\sin(w_{n}t+\phi)$
			$\ddot{x}=-A\omega_{n}^2\cos(w_{n}t+\phi)$
			Substituindo
			$-Am\omega_{n}^2\cos(w_{n}t+\phi) + kA\cos(w_{n}t+\phi)$
			$(k-m\omega_{n}^2)\ A\cos(w_{n}t+\phi)=0$
			Note que $A$ não pode ser zero, para não cair na solução trivial.
			Note que $\omega_{n}$ não pode ser zero pois existe massa.
			logo, $A\cos(w_{n}t+\phi)$ não será continuamente zero.
			implica que $(k-m\omega_{n}^2)=0 \implies \omega_{n}=\sqrt{\left( \frac{m}{k} \right)}$
			- Aplicando condições iniciais
				$x(0)=x_{0}$   e   $\dot{x}(0)=\dot{x}_{0}$
				a solução proposta $x(t)=A\cos(w_{n}t+\phi)$ satisfaz:
					$x(0)=x_{0}=Z\cos(\phi) \implies \cos(\phi)=\left( \frac{x_{0}}{A} \right)$
					$\dot{x}(0)=\dot{x}_{0}=Z\sin(\phi) \implies \sin(\phi)=\left( \frac{-\dot{x}_{0}}{A\omega_{n}} \right)$
				logo,
					$$\phi=\tan^{-1} \left( \frac{\dot{x}_{0}}{x_{0}\omega_{n}} \right)$$
				Uma equação para a amplitude A pode ser definida utilizando a relação $\sin^2(\phi)+\cos^2(\phi)=1$:
				$$\frac{x^2_{0}}{A^2}+ \frac{\dot{x}^2_{0}}{A^2\omega^2_{n}}=1 \ \ \ \implies\ \ \ A=\sqrt{x^2_{0}+ \frac{\dot{x}^2_{0}}{\omega^2_{n}}}$$
		- Modelo de resposta 2 -> $x(t)=Ze^{\lambda t}$
			$\dot{x}(t)=Z\lambda e^{\lambda t}$
			$\ddot{x}=Z\lambda^2e^{\lambda t}$
			substituindo na EDO:
			$m\ddot{x}(t)+kx(t)=0$
			$mZ\lambda^2e^{\lambda t}+kZe^{\lambda t}=0$
			
			$(m\lambda^2+k)Ze^{\lambda t}=0$
			Hipótese 1 -> $Z$ não pode ser zero para não cair na solução trivial.
			Hipótese 2 -> $e^{\lambda t}$ não pode ser zero.
			
			logo, $(m\lambda^2+k)=0$
			$\lambda=\pm\sqrt{\left( -\frac{k}{m} \right)}$, já que $k$ e $m$ são positivos, a raiz é necessariamente imaginária
			$\lambda=\pm j\omega_{n}$
			temos 2 raízes conjugadas, portanto o novo formato de resposta é:
			$x(t)=Z_{1}e^{j\omega_{n}}+Z_{2}e^{-j\omega_{n}}$
			sendo que $Z_{1}$ e $Z_{2}$ são números complexos do formato $Z_{1}=A_{1}+jB_{1}$
			Aplicando a fórmula de Euler para a exponencial dada por:
				$e^{\pm j\omega_{n}t}=\cos(\omega_{n}t)\pm j\sin(\omega_{n}t)$
- Exemplo 2 - massa mola com amortecimento
	![[Massa Mola Amortecedor.png|900]]
	equação da força:
		$-kx -c\dot{x}=m\ddot{x}$
		$m\ddot{x}+c\dot{x}+kx=0$
		$\ddot{x}+\frac{c}{m}\dot{x}+\frac{k}{m}x=0$
		$\ddot{x}+2\xi \omega_{n}\dot{x}+\omega_{n}^2x=0$
		cujo as raízes são:
		$s_{1,2}=-\xi \omega_{n}\pm \omega_{n}\sqrt{ \xi^2-1 }$
		podemos simplificar a solução atribuindo: