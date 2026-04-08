---
tags:
  - Unicamp
  - Calculus
  - Transform
Data: 2024/07/17
Reference: https://math.libretexts.org/Courses/Mission_College/Math_4B%3A_Differential_Equations_(Kravets)/07%3A_Laplace_Transforms/7.01%3A_Introduction_to_the_Laplace_Transform
---
Prerequisites:
	[[Limits and continuity]]
	[[Integral]]

---
The Laplace transform is a mathematical tool used to transform a function of a real variable $t$ (usually time) into a function of a complex variable $s$. The transform is defined by the unilateral line integral of $\mathcal f(t)$:
$$\mathscr L\{\mathcal f(t)\}=
\mathcal F(s)=
\int _0 ^\infty \mathcal f(t)e^{-st}dt
$$
where:

- $\mathscr L\{\mathcal f(t)\}$ denotes the Laplace transform of $\mathcal f(t)$,
- $\mathcal F(s)$ is the image of $\mathcal f(t)$ in the $s$ domain,
- $t$ is a real variable,
- $s$ is a complex variable.

The Laplace transform is widely used in engineering and physics because it simplifies the process of solving linear differential equations with initial conditions. It converts differential equations in the time domain into algebraic equations in the complex domain, which are generally easier to manipulate and solve.
There are several transformations found in the [[Laplace Transform Table]].

Transformation of some simple functions:
- $\mathcal f(t)=C$
	$\mathscr L\{C\}=\int _0 ^\infty \mathcal Ce^{-st}dt$
	$\int _0 ^\infty \mathcal Ce^{-st}dt=\lim _{a\to \infty} \int _0 ^a \mathcal Ce^{-st}dt$
	$\lim _{a\to \infty} (-\frac {1}{s} Ce^{-st})\vert _{0}^{a}$
	$\lim _{a\to \infty}[(-\frac {1}{s} Ce^{-sa})-(-\frac {1}{s} Ce^{-0s})]$
	$\lim _{a\to \infty}[(-\frac {1}{s} Ce^{-sa})-(-\frac {C}{s})]$
	$\mathscr L\{C\}=\frac {C}{s}$
- $\mathcal f(t)=t$
	$\mathscr L\{t\}=\int _0 ^\infty \mathcal te^{-st}dt$
	$\lim _{a\to \infty} \int _0 ^a \mathcal te^{-st}dt$
	- [[Integration by parts]]
		 $\int \mathcal f(x)g^′(x)dx=f(x)g(x)-\int f^′(x)g(x)dx$
	$\int_{0}^{\infty} te^{-st}dt = [-\frac{1}{s}te^{-st}]\mid_{0}^{\infty}-\int_{0}^{\infty}-\frac{1}{s}e^{-st}dt$
	$\int_{0}^{\infty} te^{-st}dt = [-\frac{1}{s}te^{-st}-\frac{1}{s²}e^{-st}]\mid_{0}^{\infty}$
	$\int_{0}^{\infty} te^{-st}dt =\lim_{a\to \infty}[(-\frac{1}{s}ae^{-sa}-\frac{1}{s²}e^{-sa})-(-\frac{1}{s}0e^{-s0}-\frac{1}{s²}e^{-s0})]$
	$\int_{0}^{\infty} te^{-st}dt =\frac{1}{s²}$
	$\mathscr L\{t\}=\frac{1}{s²}$
- $\mathcal f(t)=\sin(at)$
	$\mathscr L\{\sin(at)\}=\int _0 ^\infty \mathcal \sin(at)e^{-st}dt$
	$\lim _{a\to \infty} \int _0 ^a \mathcal \sin(at)e^{-st}dt$
	- [[Integration by parts]]
		 $\int \mathcal f(x)g^′(x)dx=f(x)g(x)-\int f^′(x)g(x)dx$
	$\int _0 ^\infty \mathcal \sin(at)e^{-st}dt=[-\frac{1}{s}\sin(at)e^{-st}]\mid_0^\infty-\int_0^\infty -\frac{1}{s}a\cos(at)e^{-st}dt$
	$\int _0 ^\infty \mathcal \sin(at)e^{-st}dt=[-\frac{1}{s}\sin(at)e^{-st}]\mid_0^\infty +\frac{a}{s}\int_0^\infty \cos(at)e^{-st}dt$
	$\int _0 ^\infty \mathcal \sin(at)e^{-st}dt=[-\frac{1}{s}\sin(at)e^{-st}]\mid_0^\infty +\frac{a}{s}[-\frac{1}{s}cos(at)e^{-st}]\mid_0^\infty -\frac{a}{s}\int_0^\infty \frac{1}{s} a\sin(at)e^{-st}dt$
	$\int _0 ^\infty \mathcal \sin(at)e^{-st}dt=[-\frac{1}{s}\sin(at)e^{-st}]\mid_0^\infty -[\frac{a}{s^2}cos(at)e^{-st}]\mid_0^\infty -\frac{a^2}{s^2}\int_0^\infty \sin(at)e^{-st}dt$
	$\int _0 ^\infty \mathcal \sin(at)e^{-st}dt [1+\frac{a^2}{s^2}]=[-\frac{1}{s}\sin(at)e^{-st}]\mid_0^\infty -[\frac{a}{s^2}cos(at)e^{-st}]\mid_0^\infty$
	$\int _0 ^\infty \mathcal \sin(at)e^{-st}dt =\frac{1}{[1+\frac{a^2}{s^2}]}[[-\frac{1}{s}\sin(at)e^{-st}]\mid_0^\infty -[\frac{a}{s^2}cos(at)e^{-st}]\mid_0^\infty]$
	$\int _0 ^\infty \mathcal \sin(at)e^{-st}dt =\frac{1}{[1+\frac{a^2}{s^2}]}[[(0)-(0)] -[(0)-(\frac{a}{s^2})]]$
	$\int _0 ^\infty \mathcal \sin(at)e^{-st}dt =\frac{1}{[1+\frac{a^2}{s^2}]}(\frac{a}{s^2})$
	$\int _0 ^\infty \mathcal \sin(at)e^{-st}dt =\frac{a}{s^2+a^2}$
	$\mathscr L\{\sin(at)\} =\frac{a}{s^2+a^2}$
Special cases:
there are 2 special cases, the [[Heaviside and Dirac Delta Function]]:



