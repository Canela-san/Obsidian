# 📋 Plano de Estudos — Lista 1 (Prova 1) — ES728

**Tags:** #controle-avancado #es728 #plano-de-estudos #prova1

**Navegação:** [[ES728 - Controle Avançado de Sistemas|↑ ES728]] · [[Gabarito Comentado - Lista 1 (Prova 1)|Gabarito →]]

Este é o plano de estudos derivado da **Lista de Exercícios** usada como preparação para a Prova 1 (arquivo `Lista_ES728_prova_1.pdf`, 24 exercícios em 8 temas). A lista já resolve os exercícios 1, 3, 4 e 5 como exemplo de método — o restante (a maioria) fica para praticar sozinho. As notas de referência abaixo usam **exemplos genéricos diferentes** dos exercícios da lista de propósito: a ideia é você aprender o método na nota e aplicá-lo você mesmo na lista, não colar a resposta.

---

## 🗺️ Visão Geral: Tema → Exercícios → Nota de Referência

| # | Tema | Exercícios | Nota de referência | Estudado? |
|---|------|:---:|---|:---:|
| 1 | Autovalores, autovetores e forma de Jordan | 1, 2, 3 | [[Autovalores e Autovetores]] · [[Autovetores Generalizados e a Forma de Jordan]] | [ ] |
| 2 | Matriz de transição de estados ($e^{At}$) e Cayley-Hamilton | 4, 5 | [[Matriz de Transição de Estados por método de Vandermonde (Cayley-Hamilton)]] · [[Matriz de Transição de Estados por Transformação de Similaridade]] | [ ] |
| 3 | Modelagem e representação em espaço de estados | 6, 7, 8 | [[Espaço de Estados - Modelagem e Representação]] | [ ] |
| 4 | Resposta no tempo e função de transferência | 9, 10, 11 | [[Resposta no Tempo e Função de Transferência (Espaço de Estados)]] | [ ] |
| 5 | Formas quadráticas e definição de sinal | 12 | [[Formas Quadráticas e Definição de Sinal]] | [ ] |
| 6 | Controlabilidade, observabilidade e realização mínima | 13–18 | [[Controlabilidade, Observabilidade e Realização Mínima]] | [ ] |
| 7 | Formas canônicas e transformações | 19, 20, 21 | [[Formas Canônicas e Transformações]] | [ ] |
| 8 | Projeto por realimentação de estados (Bass-Gura e Ackermann) | 22, 23, 24 | [[Projeto por Realimentação de Estados (Bass-Gura e Ackermann)]] | [ ] |

> [!info] Por que essa ordem?
> A ordem da própria lista já é a ordem de dependência certa: autovalores/Jordan → $e^{At}$ (que se apoia em autovalores) → modelagem em espaço de estados → resposta temporal e função de transferência (que se apoiam na modelagem e no $e^{At}$) → formas quadráticas (independente, mas curta) → controlabilidade/observabilidade → formas canônicas (que se apoiam em controlabilidade/observabilidade) → realimentação de estados/Bass-Gura-Ackermann (que se apoia em formas canônicas). Não pule tema 6 e 7 antes do 8 — a fórmula de Bass-Gura *é*, literalmente, a transformação para forma canônica controlável do tema 7.

---

## 🧭 Sessões de Estudo Sugeridas

Divida em blocos de acordo com o tempo que você tiver antes da prova; a ordem entre blocos importa mais que a duração de cada um.

- [ ] **Sessão 1 — Base de álgebra linear (temas 1-2).** Revise autovalores/autovetores, forma de Jordan, e as duas formas de calcular $e^{At}$ (Vandermonde e transformação de similaridade). Refaça o Exercício 1 (que já vem resolvido) sem olhar a solução, depois confira. Faça 2 e 3 sozinho.
- [ ] **Sessão 2 — Modelagem e resposta (temas 3-4).** Leia [[Espaço de Estados - Modelagem e Representação]] e [[Resposta no Tempo e Função de Transferência (Espaço de Estados)]]. Resolva 6, 7, 8 (modelagem) e depois 9, 10, 11 (resposta no tempo/FT) — nessa ordem, porque 9-11 reaproveitam a técnica de $e^{At}$ da Sessão 1.
- [ ] **Sessão 3 — Formas quadráticas + Controlabilidade/Observabilidade (temas 5-6).** O tema 5 é rápido (1 questão de múltipla escolha, cuidado com a pegadinha da matriz não-simétrica). O tema 6 é o maior bloco da prova (6 exercícios, 13-18) — reserve mais tempo aqui, principalmente para o teste "por inspeção" em forma de Jordan (Exercício 17) e para realização mínima (16, 18).
- [ ] **Sessão 4 — Formas canônicas + Realimentação de estados (temas 7-8).** Praticar a transformação para forma canônica controlável/observável (19-21) antes de tentar Bass-Gura/Ackermann (22-24), já que a matriz de transformação $T$ é reaproveitada nas duas fórmulas de posicionamento de polos.
- [ ] **Sessão 5 — Revisão geral.** Refaça 2-3 exercícios de cada tema **sem consultar as notas**, cronometrando. Use as perguntas de autoteste no final de cada nota como checagem rápida.

---

## ✅ Checklist por Exercício

Marque conforme for resolvendo. Os exercícios 1, 3, 4 e 5 já vêm resolvidos na lista — use-os para conferir seu método, não para copiar.

**Tema 1 — Autovalores, autovetores, Jordan**
- [ ] Exercício 1 (resolvido na lista — refaça e confira)
- [ ] Exercício 2
- [ ] Exercício 3 (usa o resultado do 2)

**Tema 2 — $e^{At}$ e Cayley-Hamilton**
- [ ] Exercício 4 (resolvido na lista — duas técnicas)
- [ ] Exercício 5 (resolvido na lista — usa Cayley-Hamilton para achar $A^{-1}$)

**Tema 3 — Modelagem em espaço de estados**
- [ ] Exercício 6 (sistema já em equações de 1ª ordem)
- [ ] Exercício 7 (sistema massa-mola 2 GDL → 4 estados)
- [ ] Exercício 8 (verificar realização de uma função de transferência)

**Tema 4 — Resposta no tempo / função de transferência**
- [ ] Exercício 9
- [ ] Exercício 10 (entrada degrau)
- [ ] Exercício 11 ($H(s)$ a partir do espaço de estados)

**Tema 5 — Formas quadráticas**
- [ ] Exercício 12 (múltipla escolha — atenção à matriz não-simétrica)

**Tema 6 — Controlabilidade, observabilidade, realização mínima**
- [ ] Exercício 13 (controlabilidade, 2 casos)
- [ ] Exercício 14 (observabilidade, 2 casos)
- [ ] Exercício 15 (estabilidade + controlabilidade + estabilizabilidade)
- [ ] Exercício 16 (realização mínima)
- [ ] Exercício 17 (por inspeção — 5 sistemas, alguns em forma de Jordan)
- [ ] Exercício 18 (controlabilidade/observabilidade a partir de $H(s)$ com cancelamento polo-zero)

**Tema 7 — Formas canônicas**
- [ ] Exercício 19 (forma canônica controlável, 2 casos)
- [ ] Exercício 20 (forma canônica observável, 2 casos)
- [ ] Exercício 21 (encontrar $T$ explicitamente, 2 casos)

**Tema 8 — Realimentação de estados**
- [ ] Exercício 22 (especificação de desempenho → polos desejados → $K$)
- [ ] Exercício 23 (Bass-Gura, 3 casos)
- [ ] Exercício 24 (Ackermann — repete o 23, para comparar os dois métodos)

---

## 💡 Dicas Gerais para a Prova

- O tema 6 (controlabilidade/observabilidade) é o mais pesado (6 de 24 exercícios) — não deixe para a última sessão.
- Os exercícios 23 e 24 são o mesmo problema por dois métodos diferentes: se seu $K$ bater nos dois, você tem alta confiança de que acertou.
- No Exercício 17, resista à tentação de montar a matriz de controlabilidade/observabilidade completa para os sistemas $5\times5$ e $7\times7$ — é exatamente para isso que existe o teste "por inspeção" (ver [[Controlabilidade, Observabilidade e Realização Mínima]]).
- Guarde a matriz de transformação $T$ do tema 7 — ela reaparece inteira na fórmula de Bass-Gura do tema 8.

## 🔑 Pontos-Chave para Revisão
- A lista tem 8 temas com dependência quase linear entre si; a ordem de estudo sugerida aqui segue a ordem da própria lista.
- Só os exercícios 1, 3, 4 e 5 vêm com solução — os outros 20 são para prática ativa.
- Cada nota de referência usa números diferentes dos da lista de propósito, para você aplicar o método e não decorar a resposta.
