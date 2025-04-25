A transformada de Fourier é uma ferramenta matemática muito poderosa, utilizada para transformar funções do domínio do tempo (ou espaço) para o domínio da frequência. Essa transformação revela a composição da função em termos de senos, cossenos (ou exponenciais complexas) de diferentes frequências. Em muitas áreas da engenharia, física e matemática, ela é empregada para analisar sistemas, resolver equações diferenciais e processar sinais.

## 1. Conceitos Básicos

### 1.1. Motivação

No domínio do tempo, uma função pode representar, por exemplo, uma onda ou um sinal. Contudo, muitas vezes é mais interessante conhecer quais frequências estão presentes nesse sinal. A transformada de Fourier permite “descompor” o sinal nas suas frequências constituintes, similar a uma análise de espectro.

### 1.2. Definição

A definição mais comumente utilizada para a transformada de Fourier de uma função f(t) é:
$$F(\omega)=\int_{-\infty}^{\infty} f(t)e^{ -i\omega t } \, dt $$
onde:
- $F(\omega)$ é a imagem de $f(t)$ no espaço das frequências.
- $\omega$ representa a frequência angular (medida em radianos por segundo).
- $e^{ -i \omega t }$ é o núcleo da transformação (exponencial complexa).
$$f(t)=\frac{1}{2\pi}\int_{-\infty}^{\infty} F(\omega)e^{ i\omega t } \, d\omega $$
**Observação:** Existem convenções diferentes (por exemplo, na presença de fatores $2\pi$ ou normalizações simétricas). É importante estar ciente da convenção utilizada em cada contexto.

## 2. Propriedades Importantes

A transformada de Fourier possui várias propriedades fundamentais que a tornam útil na análise de sinais, tais como:

- **Linearidade:** Se $f(t)$ e $g(t)$ têm transformadas  $F(\omega)$ e $G(\omega)$, então para constantes $a$ e $b$:
$$\mathcal{F} \{af(t)+bg(t)\}=aF(\omega)+bG(\omega)$$
- **Translação no tempo:** Um deslocamento no tempo gera uma modulação em frequência.
- **Escala:** Se a função é “esticada” ou “comprimida” no tempo, sua transformada sofre uma transformação inversa na escala de frequências.
- **Convolução:** A convolução de duas funções no tempo se transforma no produto de suas transformadas de Fourier.
- **Teorema de Parseval:** Relaciona a energia total de um sinal em função do tempo com a energia em sua representação de frequência.
## 3. Exemplo Prático: Transformada de Fourier de uma Função Gaussiana

Um exemplo clássico é calcular a transformada de Fourier de uma função Gaussiana. Considere:
$f(t)=e^{ -at^2 }$ , Com $a > 0$
### 3.1. Cálculo Passo a Passo

A transformada de Fourier dessa função é:
$$F(\omega)=\int_{-\infty}^{\infty} e^{ -at^2  } e^{ 
-j\omega t}\, dt $$
Para resolver essa integral, podemos utilizar o método do “completar o quadrado” na exponencial.

1. **Juntar os expoentes:**
$$F(\omega)=\int_{-\infty}^{\infty} e^{ -at^2-j\omega t}\, dt$$
2. resolva a integral
$$$$
