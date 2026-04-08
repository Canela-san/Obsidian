---
tags:
  - Control
  - Electrical
---
Componentes Passivos
- Resistor
- Capacitor
- Indutor

Resistor
	$V_{R}=RI$

Capacitor
	$I_{C}=C \frac{dV}{dt}$
	$V_{C}=\frac{1}{C}\int I(t)dt$
	$q=CV$
	$q=\int I(t)dt$

Indutor
	$V_{L}=L \frac{dI}{dt}$
	$I_{L}=\frac{1}{L}\int V(t)dt$

- Exemplo 1 - Modelagem de Circuito RLC
	![[Circuito RLC.png|350]]
	Note que podemos usar as lei de Kirchhoff para chegar nas equações:
	Lei das malhas:
	$V_{f}=V_{R}+V_{L}+V_{C}$
	$V_{f}=RI+L \frac{dI}{dt}+V_{C}$
	Podemos fazer uma equação em relação a tenção no capacitor
	já que $I=C \frac{dV_{C}}{dt}$
	então $\frac{dI}{dt}=C \frac{d^2V_{C}}{dt²}$
	Portanto:
	$V_{f}=RC \frac{dV_{c}}{dt}+LC \frac{d^2V_{C}}{dt^2}+ V_{C}$
	$$\bbox[5px,border:1px solid yellow]{\ddot{V_{C}}+ \frac{R}{L} \dot{V_{C}}+ V_{C}=V_{f}}$$
	