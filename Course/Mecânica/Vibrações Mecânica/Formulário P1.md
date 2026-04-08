# 1 DOF - Sem Amortecimento
	$m\ddot{x}+kx=0$
	$\ddot{x}+\omega^2_{n}x=0$
	Formato de resposta -> $x(t)=X\sin (\omega_{n}+\phi)$
		$X=\frac{\sqrt{ \omega_{n}^2x_{0}^2+v_{0}}}{\omega_{n}}$
		$\phi=\tan^{-1}\left( \frac{\omega_{n}x_{0}}{v_{0}} \right)$
# Molas Equivalentes
- Viga engastada
	$\Delta=\frac{Pl^3}{3EI}$
	$k=\frac{P}{\Delta}=\frac{3EI}{l^3}$
- Viga bi-apoiada
	$\Delta=\frac{Pl^3}{48EI}$
	$k=\frac{P}{\Delta}=\frac{48EI}{l^3}$
- Viga em solicitação axial
	$\Delta=\frac{Pl}{AE}$
	$k=\frac{P}{\Delta}=\frac{AE}{l}$
1 DOF - Com Amortecimento
	$2\xi \omega_{n}=\left( \frac{c}{m} \right)$
	$m\ddot{x}+c\dot{x}+kx=0$
	$\ddot{x}+2\xi \omega_{n}\dot{x}+\omega_{n}^2x=0$	
	$\omega_{d}=\omega_{n}\sqrt{ 1-\xi^2 }$
	$s_{1,2}=-\xi \omega_{n}=\pm j\omega_{n}\sqrt{ 1-\xi^2 }$
	Formato de resposta -> $x(t)=X\sin (\omega_{d}+\phi)$
		$X=\sqrt{ \frac{(v_{0}+\xi \omega_{n}x_{0})^2+(x_{0}\omega_{d})}{\omega_{d}^2} }$
		$\phi=\tan^{-1}\left( \frac{\omega_{d}x_{0}}{v_{0}+\xi \omega_{ n}x_{0}} \right)$
	Sistema Criticamente amortecido $\xi=1$
		Duas raízes reais, Não oscila:
		$x(t)=A_{1}e^{-\omega_{n}t}+tA_{2}e^{-\omega_{n}t}$
	Sistema super Amortecido $\xi>1$
		Duas raízes reais e distintas, não oscila:
		$s_{1}=\omega_{n}(-\xi+\sqrt{ \xi^2-1 })=-\frac{1}{\tau_{1}}$
		$s_{1}=\omega_{n}(-\xi-\sqrt{ \xi^2-1 })=-\frac{1}{\tau_{2}}$
		$x(t)=A_{1}e^{-\frac{t}{\tau_{1}}}+A_{2}e^{-\frac{t}{\tau_{2}}}$
	Decremento Logarítmico:
		$\delta=\ln \frac{x(t)}{x(t+T)}$
		$\delta=\frac{1}{n}\ln \frac{x(t)}{x(t+nT)}$
Amortecimento de Coulomb, atrito seco
$m\ddot{x}=-kx-f_{d}\operatorname{sign}(\dot{x})$
$x(t)=\left( x_{0}-\frac{F_{d}}{k} \right)\cos(\omega_{n}t)+\frac{F_{d}}{k}$
$\dot{x}(t)=-\left( x_{0}-\frac{F_{d}}{k} \right)\omega_{n}\sin(\omega_{n}t)=0$
	Posição de parada: $x\left( \frac{\pi}{\omega_{n}} \right)=-\left( x_{0}-\frac{2F_{d}}{K} \right)$
	para cada ciclo temos que: $x=x_{0}-4\frac{F_{d}}{k}$
