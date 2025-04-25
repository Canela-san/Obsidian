---
tags:
  - Software
  - Tutorial
Data: 2024/07/17
Paint Symbols: http://detexify.kirelabs.org/classify.html
Reference: https://math.meta.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference
---
 ′
MathJax is a JavaScript plugin for the markdown of mathematics symbols.

The used symbol is \$ Syntax \$
To make it appear in an exclusive line use \$\$ Syntax \$\$

For Example: \$y=x\^\2\$ results in $y=x²$.
Fractions: \$\frac{A+B}{C+D}\$ results in $\frac{A+B}{C+D}$

Greek letters also have an code:

| Symbol              | Code              |
| ------------------- | ----------------- |
| $\pi$               | \pi               |
| $\Pi$               | \Pi               |
| $\infty$            | \infty            |
| $\mathbb {NZQIRCU}$ | \mathbb {NZQIRCU} |
| $\mathscr {L}$      | \mathscr {L}      |
| $\partial$          | \partial          |
| $\mathrm {m}²$      | \mathrm {m}²      |
| $\alpha$            | \alpha            |
| $\beta$             | \beta             |
| $\omega$            | \omega            |
| $\Gamma$            | \Gamma            |
| $\Delta$            | \Delta            |
| $\Omega$            | \Omega            |
| $\epsilon$          | \epsilon          |
| $\varepsilon$       | \varepsilon       |
| $\phi$              | \phi              |
| $\varphi$           | \varphi           |
| $\lt$               | \lt               |
| $\gt$               | \gt               |
| $\le$               | \le               |
| $\ge$               | \ge               |
| $\neq$              | \neq              |
| $45^\text{o}$       | 45^\text{o}       |

More complex symbols can also be used:

| Function                                 | Code                                   |
| ---------------------------------------- | -------------------------------------- |
| $\log_2 {x}$                             | \log_2 {x}                             |
| $\ln {x}$                                | \ln {x}                                |
| $\left(\frac{\sqrt x}{y^3}\right)$       | \left(\frac{\sqrt x}{y^3}\right)       |
| $\sqrt[]{\frac{x}{y}}$                   | \sqrt[]{\frac{x}{y}}                   |
| $\sum_{n=1}^{N} n$                       | \sum_{n=1}^{N} n                       |
| $\int_{0}^{\infty}xdx$                   | \int_{0}^{\infty}xdx                   |
| $\iint$                                  | \iint                                  |
| $\iiint$                                 | \iiint                                 |
| $\lim_{0 \to \infty}\frac{1}{x}$         | \lim_{0 \to \infty}\frac{1}{x}         |
| $\prod$                                  | \prod                                  |
| $\bigcup$                                | \bigcup                                |
| $\bigcap$                                | \bigcap                                |
| $\operatorname{foo}(x)$                  | \operatorname{foo}(x)                  |
| $\hat {x}$                               | \hat {x}                               |
| $\widehat {xy}$                          | \widehat {xy}                          |
| $\bar {x}$                               | \bar {x}                               |
| $\overline {xyz}$                        | \overline {xyz}                        |
| $\vec {x}$                               | \vec {x}                               |
| $\overrightarrow {xy}$                   | \overrightarrow {xy}                   |
| $\overleftrightarrow {xy}$               | \overleftrightarrow {xy}               |
| $\dot {x}$                               | \dot {x}                               |
| $\ddot {x}$                              | \ddot {x}                              |
| $\frac{d}{dx}x\dot x=\dot {x}²+x\ddot x$ | \frac{d}{dx}x\dot x=\dot {x}²+x\ddot x |

There is a site that you can paint the symbols and it will tell you the symbolic name in MathJax,
the site URL is: http://detexify.kirelabs.org/classify.html

To make equation systems, you can follow this code:
```
$$
\left\{ 
\begin{array}{c}
a_1x+b_1y+c_1z=d_1 \\ 
a_2x+b_2y+c_2z=d_2 \\ 
a_3x+b_3y+c_3z=d_3
\end{array}
\right. 
$$
```
Results in
$$
\left\{ 
\begin{array}{c}
a_1x+b_1y+c_1z=d_1 \\ 
a_2x+b_2y+c_2z=d_2 \\ 
a_3x+b_3y+c_3z=d_3
\end{array}
\right. 
$$
To add an border, you can do:
```
$$ \bbox[5px,border:2px solid red]
{
e^x=\lim_{n\to\infty} \left( 1+\frac{x}{n} \right)^n
\qquad (2) 
}
$$
```
$$ \bbox[5px,border:2px solid red]
{
e^x=\lim_{n\to\infty} \left( 1+\frac{x}{n} \right)^n
\qquad (2) 
}
$$
Normal simplex tableau
```
\begin{array}{rrrrrr|r}
               & x_1 & x_2 & s_1 & s_2 & s_3 &    \\ \hline
           s_1 &   0 &   1 &   1 &   0 &   0 &  8 \\
           s_2 &   1 &  -1 &   0 &   1 &   0 &  4 \\
           s_3 &   1 &   1 &   0 &   0 &   1 & 12 \\ \hline
               &  -1 &  -1 &   0 &   0 &   0 &  0
\end{array}
```
$$\begin{array}{rrrrrr|r}
               & x_1 & x_2 & s_1 & s_2 & s_3 &    \\ \hline
           s_1 &   0 &   1 &   1 &   0 &   0 &  8 \\
           s_2 &   1 &  -1 &   0 &   1 &   0 &  4 \\
           s_3 &   1 &   1 &   0 &   0 &   1 & 12 \\ \hline
               &  -1 &  -1 &   0 &   0 &   0 &  0
\end{array}$$
