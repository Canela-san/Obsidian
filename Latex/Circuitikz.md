# 🔌 Guia de Referência: Biblioteca `circuitikz` no Obsidian

A biblioteca `circuitikz` é uma extensão do TikZ focada em facilitar o desenho de circuitos com qualidade profissional. No Obsidian, ela geralmente é renderizada através de plugins (como o TikZJax), permitindo que você escreva o código diretamente em blocos `tikz` .

---

## 1. Estrutura Básica do Bloco

Para que o Obsidian reconheça e renderize o desenho, o código deve sempre estar envolvido no bloco `tikz`, importar o pacote e iniciar o ambiente do documento e do circuito ('''tikz)

Snippet de código
```
 ```tikz
\usepackage{circuitikz}
\begin{document}

\begin{circuitikz}[opções_globais]
% Seu código de desenho vai aqui
\end{circuitikz}

\end{document}
 ```
```

> **Dica de Ouro:** As `[opções_globais]` mais comuns são `american` ou `european` (para o padrão dos símbolos), `scale=...` (para ajustar o tamanho) e `transform shape` (para garantir que os textos escalem junto com o desenho).

---

## 2. Circuitos Elétricos

O desenho em `circuitikz` é baseado no conceito de "caminhos" (`paths`) entre coordenadas. Você diz de onde a linha sai, qual componente ela atravessa, e onde ela chega.

### Sintaxe Principal

A estrutura básica de um componente é:

`(X_inicial, Y_inicial) to[COMPONENTE, propriedades] (X_final, Y_final)`

### Exemplo Comentado (Baseado no seu código)

Snippet de código

```
\usepackage{circuitikz}
\begin{document}

% Padrão americano, ajuste de tensão, escala e transformação de texto
\begin{circuitikz}[american, voltage shift=0.5, scale=2.5, transform shape]

% \draw inicia um caminho. [thick] deixa as linhas mais grossas.
\draw[thick] 
  % Começa na coordenada (0,0)
  (0,0) 
  % Desenha uma fonte de corrente (isource) até (0,3). 
  % l = label (nome), v = voltage (tensão)
  to[isource, l=$I_0$, v=$V_0$] (0,3)
  
  % Continua até (2,3) com um curto-circuito (short). 
  % -* cria um nó (bolinha preta) no final. i = corrente.
  to[short, -*, i=$I_0$] (2,3)
  
  % Desce até (2,0) passando por um resistor (R). 
  % i>_ indica a seta de corrente abaixo do componente.
  to[R=$R_1$, i>_=$i_1$] (2,0) 
  
  % Fecha o laço voltando para (0,0) com uma linha reta (--)
  -- (0,0);

% Novo caminho começando do nó superior
\draw[thick]
  (2,3) -- (4,3)
  to[R=$R_2$, i>_=$i_2$] (4,0) 
  to[short, -*] (2,0);

\end{circuitikz}
\end{document}
```

```tikz
\usepackage{circuitikz}
\begin{document}

% Padrão americano, ajuste de tensão, escala e transformação de texto
\begin{circuitikz}[american, voltage shift=0.5, scale=2.5, transform shape]

% \draw inicia um caminho. [thick] deixa as linhas mais grossas.
\draw[thick] 
  % Começa na coordenada (0,0)
  (0,0) 
  % Desenha uma fonte de corrente (isource) até (0,3). 
  % l = label (nome), v = voltage (tensão)
  to[isource, l=$I_0$, v=$V_0$] (0,3)
  
  % Continua até (2,3) com um curto-circuito (short). 
  % -* cria um nó (bolinha preta) no final. i = corrente.
  to[short, -*, i=$I_0$] (2,3)
  
  % Desce até (2,0) passando por um resistor (R). 
  % i>_ indica a seta de corrente abaixo do componente.
  to[R=$R_1$, i>_=$i_1$] (2,0) 
  
  % Fecha o laço voltando para (0,0) com uma linha reta (--)
  -- (0,0);

% Novo caminho começando do nó superior
\draw[thick]
  (2,3) -- (4,3)
  to[R=$R_2$, i>_=$i_2$] (4,0) 
  to[short, -*] (2,0);

\end{circuitikz}
\end{document}
```

### Principais Componentes Elétricos

- **`R`**: Resistor
    
- **`C`**: Capacitor
    
- **`L`**: Indutor
    
- **`V`** ou **`vsource`**: Fonte de Tensão ideal
    
- **`I`** ou **`isource`**: Fonte de Corrente ideal
    
- **`battery`**: Bateria
    
- **`short`**: Fio simples (curto-circuito)
    

---

## 3. Circuitos Mecânicos (Sistemas Massa-Mola-Amortecedor)

O `circuitikz` também possui componentes dedicados para modelagem de sistemas dinâmicos e mecânicos translacionais. A lógica de desenho é exatamente a mesma dos circuitos elétricos.
### Exemplo de Sistema Mecânico

Aqui está um exemplo desenhando uma parede fixa, uma mola, uma massa e um amortecedor em paralelo:

Snippet de código

```
\usepackage{circuitikz}
\begin{document}

\begin{circuitikz}[scale=3, transform shape]
  % Reduz a amplitude (altura do zigue-zague) da mola globalmente
  \ctikzset{bipoles/spring/height=0.3}

  % Parede esquerda e chão
  \draw[ultra thick] (0,3) -- (0,0) -- (5,0);
  
  % Mola (Spring) - Adicionado 'thick' para engrossar a linha
  \draw[thick] (0,2.5) to[spring, l=$k$] (3,2.5);
  
  % Amortecedor (Damper) - Adicionado 'thick' para engrossar a linha
  \draw[thick] (0,1) to[damper, l=$c$] (3,1);
  
  % Bloco de Massa - Removido 'fill=gray!20' para ficar apenas o contorno
  \draw[very thick] (3,0.5) rectangle (4.5,3) node[midway] {$M$};
  
  % Seta indicando o deslocamento x(t)
  \draw[->, thick] (4.5, 1.75) -- (5.5, 1.75) node[right] {$x(t)$};
\end{circuitikz}
\end{document}

```tikz
\usepackage{circuitikz}
\usetikzlibrary{patterns} % Biblioteca necessária para as hachuras

\begin{document}

\begin{circuitikz}[scale=1.5, transform shape]
  % Mantendo a mola mais "magra"
  \ctikzset{bipoles/spring/height=0.3}

  % ==========================================
  % 1. SISTEMA MASSA-MOLA-AMORTECEDOR
  % ==========================================
  
  % Hachuras indicando o teto fixo (engastado)
  % Desenhamos um retângulo do Y=4 até Y=4.3 preenchido com linhas diagonais
  \fill[pattern=north east lines] (0,4) rectangle (4,4.3);
  
  % Teto (Linha horizontal grossa logo abaixo das hachuras)
  \draw[ultra thick] (0,4) -- (4,4);
  
  % Mola conectando o teto à massa
  \draw[thick] (1,4) to[spring, l=$k$] (1,2);
  
  % Amortecedor conectando o teto à massa
  \draw[thick] (3,4) to[damper, l=$c$] (3,2);
  
  % Bloco de Massa (Apenas o contorno)
  \draw[thick] (0.5,1) rectangle (3.5,2) node[midway] {$M$};
  
  % Seta indicando o deslocamento x(t) para baixo
  \draw[-latex, thick] (4.5, 2) -- (4.5, 0.5) node[right] {$x(t)$};
  
  % ==========================================
  % 2. DIAGRAMA DE CORPO LIVRE
  % ==========================================
  
  \begin{scope}[shift={(6,0)}]
    
    % Título acima do DCL
    
    % Bloco de Massa isolado
    \draw[thick] (0.5,1) rectangle (3.5,2) node[midway] {$M$};
    
    % Força da mola puxando para cima
    \draw[-latex, thick] (1.2, 2) -- (1.2, 3.5) node[above] {$F_k = kx$};
    
    % Força do amortecedor puxando para cima
    \draw[-latex, thick] (2.8, 2) -- (2.8, 3.5) node[above] {$F_c = c\dot{x}$};
    
    % Força Peso puxando para baixo
    \draw[-latex, thick] (2, 1) -- (2, -0.5) node[right] {$P = Mg$};
    
    % Referencial de x(t)
    \draw[-latex, dashed] (4, 2) -- (4, 0.5) node[right] {$x$};
    
  \end{scope}

\end{circuitikz}
\end{document}
```

```tikz
\usepackage{circuitikz}
\begin{document}

\begin{circuitikz}[scale=3, transform shape]
  % Reduz a amplitude (altura do zigue-zague) da mola globalmente
  \ctikzset{bipoles/spring/height=0.3}

  % Parede esquerda e chão
  \draw[ultra thick] (0,3) -- (0,0) -- (5,0);
  
  % Mola (Spring) - Adicionado 'thick' para engrossar a linha
  \draw[thick] (0,2.5) to[spring, l=$k$] (3,2.5);
  
  % Amortecedor (Damper) - Adicionado 'thick' para engrossar a linha
  \draw[thick] (0,1) to[damper, l=$c$] (3,1);
  
  % Bloco de Massa - Removido 'fill=gray!20' para ficar apenas o contorno
  \draw[very thick] (3,0.5) rectangle (4.5,3) node[midway] {$M$};
  
  % Seta indicando o deslocamento x(t)
  \draw[->, thick] (4.5, 1.75) -- (5.5, 1.75) node[right] {$x(t)$};
\end{circuitikz}
\end{document}

```tikz
\usepackage{circuitikz}
\usetikzlibrary{patterns} % Biblioteca necessária para as hachuras

\begin{document}

\begin{circuitikz}[scale=1.5, transform shape]
  % Mantendo a mola mais "magra"
  \ctikzset{bipoles/spring/height=0.3}

  % ==========================================
  % 1. SISTEMA MASSA-MOLA-AMORTECEDOR
  % ==========================================
  
  % Hachuras indicando o teto fixo (engastado)
  % Desenhamos um retângulo do Y=4 até Y=4.3 preenchido com linhas diagonais
  \fill[pattern=north east lines] (0,4) rectangle (4,4.3);
  
  % Teto (Linha horizontal grossa logo abaixo das hachuras)
  \draw[ultra thick] (0,4) -- (4,4);
  
  % Mola conectando o teto à massa
  \draw[thick] (1,4) to[spring, l=$k$] (1,2);
  
  % Amortecedor conectando o teto à massa
  \draw[thick] (3,4) to[damper, l=$c$] (3,2);
  
  % Bloco de Massa (Apenas o contorno)
  \draw[thick] (0.5,1) rectangle (3.5,2) node[midway] {$M$};
  
  % Seta indicando o deslocamento x(t) para baixo
  \draw[-latex, thick] (4.5, 2) -- (4.5, 0.5) node[right] {$x(t)$};
  
  % ==========================================
  % 2. DIAGRAMA DE CORPO LIVRE
  % ==========================================
  
  \begin{scope}[shift={(6,0)}]
    
    % Título acima do DCL
    
    % Bloco de Massa isolado
    \draw[thick] (0.5,1) rectangle (3.5,2) node[midway] {$M$};
    
    % Força da mola puxando para cima
    \draw[-latex, thick] (1.2, 2) -- (1.2, 3.5) node[above] {$F_k = kx$};
    
    % Força do amortecedor puxando para cima
    \draw[-latex, thick] (2.8, 2) -- (2.8, 3.5) node[above] {$F_c = c\dot{x}$};
    
    % Força Peso puxando para baixo
    \draw[-latex, thick] (2, 1) -- (2, -0.5) node[right] {$P = Mg$};
    
    % Referencial de x(t)
    \draw[-latex, dashed] (4, 2) -- (4, 0.5) node[right] {$x$};
    
  \end{scope}

\end{circuitikz}
\end{document}
```

### Principais Componentes Mecânicos

- **`spring`**: Mola (elasticidade)
    
- **`damper`**: Amortecedor (atrito viscoso)
    
- **`mass`**: Caixa de massa (inércia) - _Nota: Você também pode desenhar retângulos padrão do TikZ para representar blocos de massa de forma mais customizada, como no exemplo acima._
    
- **`ground`**: Referência fixa (parede ou chão). Use `rotate` para alinhar as hachuras corretamente.
    

---

## 💡 Dicas de Formatação

- **Rótulos Matemáticos:** Sempre coloque o texto dos rótulos (`l=`, `v=`, `i=`) entre símbolos de cifrão (`$`) para renderizar no formato matemático do LaTeX (ex: `$R_1$`, `$\mu F$`).
    
- **Alinhamento:** Use coordenadas inteiras ou fracionadas simples (como `1.5`) para manter o desenho em um grid invisível e evitar fios tortos.
    
- **Anotações:** Use o parâmetro `color=red` (ou outra cor) dentro das chaves de um componente específico caso queira destacá-lo em suas anotações de estudo.

mais alguns exemplos:
```tikz
\usepackage{circuitikz}
\begin{document}

\begin{circuitikz}[american, voltage shift=0.5, scale=2.5, transform shape]
\draw[thick] (0,0)
to[isource, l=$I_0$, v=$V_0$] (0,3)
to[short, -*, i=$I_0$] (2,3)
to[R=$R_1$, i>_=$i_1$] (2,0) -- (0,0);
\draw[thick](2,3) -- (4,3)
to[R=$R_2$, i>_=$i_2$]
(4,0) to[short, -*] (2,0);
\end{circuitikz}

\end{document}
```

```tikz
\usepackage{circuitikz}
\begin{document}

\begin{circuitikz}[american, voltage shift=0.5, scale=2.5, transform shape]
\draw[thick] (0,0)
to[isource, l=$I_0$, v=$V_0$] (0,3)
to[short, -*, i=$I_0$] (2,3)
to[R=$R_1$, i>_=$i_1$] (2,0) -- (0,0);
\draw[thick](2,3) -- (4,3)
to[R=$R_2$, i>_=$i_2$]
(4,0) to[short, -*] (2,0);
\end{circuitikz}

\end{document}
```
```tikz
\usepackage{circuitikz}
\begin{document}




\begin{circuitikz}[american, voltage shift=0.5, scale=2.5, transform shape]
\draw[thick] (0,0)
to[isource, l=$I_0$, v=$V_0$] (0,3);
\end{circuitikz}

\end{document}
```

```tikz
\usepackage{circuitikz}
\begin{document}

\begin{circuitikz}[scale=2, transform shape]

  % 1. LADO ESQUERDO: Fonte de Tensão (Subindo do 0,0 para o 0,3)
  % Usamos 'V' para fonte de tensão genérica. 'v=' adiciona a voltagem.
  \draw (0,0) to[battery, v=$12V$] (0,3);

  % 2. TOPO: Resistor (Indo para a direita, do 0,3 para o 3,3)
  % Usamos 'R' para resistor. 'l=' (letra L minúscula) adiciona o rótulo (label).
  \draw (0,3) to[R, l=$10 \Omega$] (3,3);

  % 3. LADO DIREITO: Capacitor (Descendo do 3,3 para o 3,0)
  % Usamos 'C' para capacitor. 
  \draw (3,3) to[C, l=$5 \mu F$] (3,0);

  % 4. CHÃO: Fio simples (Fechando o circuito, voltando do 3,0 para o 0,0)
  % Para um fio sem componentes, podemos usar apenas dois traços '--'
  \draw (3,0) -- (0,0) -- (-1,-1);

\end{circuitikz}
\end{document}
```

```tikz
\usepackage{circuitikz}
\begin{document}

\begin{circuitikz}[scale=2.5, transform shape]
  % Parede esquerda e chão
  \draw[ultra thick] (0,3) -- (0,0) -- (5,0);
  
  % Mola (Spring) conectando a parede até a massa
  \draw (0,2.5) to[spring, l=$k$] (3,2.5);
  
  % Amortecedor (Damper) conectando a parede até a massa
  \draw (0,1) to[damper, l=$c$] (3,1);
  
  % Bloco de Massa (Desenhado como um retângulo simples com texto no meio)
  \draw[thick, fill=gray!20] (3,0.5) rectangle (4.5,3) node[midway] {$M$};
  
  % Seta indicando o deslocamento x(t)
  \draw[->, thick] (4.5, 1.75) -- (5.5, 1.75) node[right] {$x(t)$};
\end{circuitikz}
\end{document}
```

![[Massa Mola Amortecedor.png]]
```tikz
\usepackage{circuitikz}
\begin{document}

\begin{circuitikz}[scale=3, transform shape]
  % Reduz a amplitude (altura do zigue-zague) da mola globalmente
  \ctikzset{bipoles/spring/height=0.3}

  % Parede esquerda e chão
  \draw[ultra thick] (0,3) -- (0,0) -- (5,0);
  
  % Mola (Spring) - Adicionado 'thick' para engrossar a linha
  \draw[thick] (0,2.5) to[spring, l=$k$] (3,2.5);
  
  % Amortecedor (Damper) - Adicionado 'thick' para engrossar a linha
  \draw[thick] (0,1) to[damper, l=$c$] (3,1);
  
  % Bloco de Massa - Removido 'fill=gray!20' para ficar apenas o contorno
  \draw[very thick] (3,0.5) rectangle (4.5,3) node[midway] {$M$};
  
  % Seta indicando o deslocamento x(t)
  \draw[->, thick] (4.5, 1.75) -- (5.5, 1.75) node[right] {$x(t)$};
\end{circuitikz}
\end{document}

```tikz
\usepackage{circuitikz}
\usetikzlibrary{patterns} % Biblioteca necessária para as hachuras

\begin{document}

\begin{circuitikz}[scale=1.5, transform shape]
  % Mantendo a mola mais "magra"
  \ctikzset{bipoles/spring/height=0.3}

  % ==========================================
  % 1. SISTEMA MASSA-MOLA-AMORTECEDOR
  % ==========================================
  
  % Hachuras indicando o teto fixo (engastado)
  % Desenhamos um retângulo do Y=4 até Y=4.3 preenchido com linhas diagonais
  \fill[pattern=north east lines] (0,4) rectangle (4,4.3);
  
  % Teto (Linha horizontal grossa logo abaixo das hachuras)
  \draw[ultra thick] (0,4) -- (4,4);
  
  % Mola conectando o teto à massa
  \draw[thick] (1,4) to[spring, l=$k$] (1,2);
  
  % Amortecedor conectando o teto à massa
  \draw[thick] (3,4) to[damper, l=$c$] (3,2);
  
  % Bloco de Massa (Apenas o contorno)
  \draw[thick] (0.5,1) rectangle (3.5,2) node[midway] {$M$};
  
  % Seta indicando o deslocamento x(t) para baixo
  \draw[-latex, thick] (4.5, 2) -- (4.5, 0.5) node[right] {$x(t)$};
  
  % ==========================================
  % 2. DIAGRAMA DE CORPO LIVRE
  % ==========================================
  
  \begin{scope}[shift={(6,0)}]
    
    % Título acima do DCL
    
    % Bloco de Massa isolado
    \draw[thick] (0.5,1) rectangle (3.5,2) node[midway] {$M$};
    
    % Força da mola puxando para cima
    \draw[-latex, thick] (1.2, 2) -- (1.2, 3.5) node[above] {$F_k = kx$};
    
    % Força do amortecedor puxando para cima
    \draw[-latex, thick] (2.8, 2) -- (2.8, 3.5) node[above] {$F_c = c\dot{x}$};
    
    % Força Peso puxando para baixo
    \draw[-latex, thick] (2, 1) -- (2, -0.5) node[right] {$P = Mg$};
    
    % Referencial de x(t)
    \draw[-latex, dashed] (4, 2) -- (4, 0.5) node[right] {$x$};
    
  \end{scope}

\end{circuitikz}
\end{document}
```
```tikz
\usepackage{circuitikz}
\begin{document}

\begin{circuitikz}[american, scale=2, transform shape]
  
  % ==========================================
  % 1. ENTRADA E IMPEDÂNCIAS SÉRIE DO PRIMÁRIO
  % ==========================================
  % Linha superior: Terminal Vp -> Fio -> Rp -> Ldp
  \draw (0,4) node[left] {$V_p$} to[short, o-] (1,4)
        to[R, l=$R_p$] (3,4) 
        to[L, l=$L_{dp}$] (5,4);
        
  % Linha inferior (Referência/Retorno)
  \draw (0,0) to[short, o-] (5,0);

  % ==========================================
  % 2. O SHUNT PARASITA (Ramo de Excitação)
  % ==========================================
  % Estendemos as linhas superior e inferior até o transformador
  \draw (5,4) -- (9,4);
  \draw (5,0) -- (9,0);
  
  % Resistência de perda no núcleo (Rc) - Desenhada na vertical
  % O "node[circ]{}" desenha o ponto de conexão (nó elétrico)
  \draw (5,4) node[circ]{} to[R, l=$R_c$] (5,0) node[circ]{};
  
  % Indutância de magnetização (Lm) - Desenhada na vertical
  \draw (7,4) node[circ]{} to[L, l=$L_m$] (7,0) node[circ]{};

  % ==========================================
  % 3. TRANSFORMADOR IDEAL (Bobinas e Núcleo)
  % ==========================================
  % Bobina Primária Ideal
  \draw (9,4) to[L, l=$N_p$] (9,0);
  
  % Linhas paralelas representando o núcleo de ferro magnético
  \draw[thick] (9.9, 0.5) -- (9.9, 3.5);
  \draw[thick] (10.1, 0.5) -- (10.1, 3.5);
  
  % Bobina Secundária Ideal 
  % (Usamos l_ ao invés de l para o texto ficar do lado de fora da bobina)
  \draw (11,4) to[L, l_=$N_s$] (11,0);

  % ==========================================
  % 4. IMPEDÂNCIAS SÉRIE DO SECUNDÁRIO E SAÍDA
  % ==========================================
  % Linha superior: Lds -> Rs -> Terminal Vs
  \draw (11,4) -- (12,4) 
        to[L, l=$L_{ds}$] (14,4) 
        to[R, l=$R_s$] (15,4) 
        to[short, -o] (17,4) node[right] {$V_s$};
        
  % Linha inferior do secundário
  \draw (11,0) to[short, -o] (17,0);
  
\end{circuitikz}
\end{document}
```
