---
tags:
  - Meta
  - Vault
aliases:
  - Contexto
  - Contexto do Vault
Nome: Contexto do Vault — Caderno Unicamp
Última Atualização: 2026-09-01
Status: Diagnóstico Inicial
---

# 📚 Contexto do Vault

> Este arquivo existe para dar contexto rápido sobre o estado atual do caderno: o que ele é, o que já funciona bem, o que está pela metade e o que precisa de refatoração. Serve tanto pra você quanto pra qualquer assistente (Claude incluso) que for ajudar a organizar isso depois.

## 1. Propósito do vault

Caderno pessoal de Engenharia (Unicamp), usado para:
- Registrar rapidamente o conteúdo das aulas;
- Consolidar fórmulas, conceitos e exemplos resolvidos para estudo e revisão;
- **Objetivo real: aprender a matéria escrevendo sobre ela** — não só arquivar.

A grade cobre Química, Física, Cálculo/Matemática, Computação, Elétrica, Mecânica e Controle e Automação (disciplinas de FEM, FEEC, IC, IMECC, IFGW, IQ), o que indica o curso de **Engenharia de Controle e Automação**. Também há matérias de humanas (Economia, Geociências) e dois projetos pessoais fora da grade (upgrade de rede doméstica e um processador de 18 bits).

Foram analisados **121 arquivos** do vault.

## 2. Estrutura geral de pastas

```
📁 Course/
 ├── Química/                    (3 disciplinas)
 ├── Mecânica/                   (6 subpastas)
 ├── Computação/                 (5 subpastas — Redes é a maior e melhor parte do vault)
 ├── Elétrica/                   (6 subpastas)
 ├── Matemática/                 (8 subpastas)
 ├── Fisica/                     (4 subpastas)
 ├── Controle e Automação/       (5 subpastas)
 ├── Sistemas Produtivos/        (sem nota-índice de disciplina)
 ├── Economia/                   (sem nota-índice de disciplina)
 └── Geociências/                (sem nota-índice de disciplina)
📁 Latex/                        (guias de referência: circuitikz, MathJax)
📁 Processor/                    (projeto pessoal — processador 18 bits)
📁 IC/                           (anotações soltas)
📁 Templates/                    (template de disciplina)
📁 Excalidraw/                   (desenhos)
```

## 3. Diagnóstico: pastas "casca vazia" vs pastas com conteúdo

**Critério usado:** uma pasta é "casca vazia" quando contém **só** a nota-índice da disciplina (frontmatter + ementa copiada do DAC), sem nenhuma nota real de estudo dentro. Uma pasta "com conteúdo" tem ao menos uma nota de resumo, fórmula explicada ou exemplo resolvido.

> [!important] Achado principal
> **Nenhuma das ~38 notas-índice de disciplina tem conteúdo de aula escrito nela mesma** — todas são só a ementa (é o que o `Template - Disciplina.md` gera, e ninguém volta lá pra completar). Quando existe conteúdo de verdade, ele mora solto em notas-irmãs na mesma pasta, quase sempre **sem link de volta** pra nota "oficial" da disciplina.

### 3.1 Química
| Pasta | Disciplina | Status |
|---|---|---|
| `Química/` | ES242, QG111, QG122 | 🔴 Vazia — 3 disciplinas, só ementa cada |

### 3.2 Mecânica
| Pasta | Disciplina | Status | Observação |
|---|---|---|---|
| `Vibrações Mecânica/` | EM607 | 🟢 Rica | 4 notas de conteúdo boas; 1 vazia (`Oscilação de Suporte`) |
| `Dispositivos Eletromecânicos/` | ES625 | 🔴 Vazia | |
| `Ternodinâmica/` *(sic)* | ES560, ES672, ES460 | 🟡 Confusa | conteúdo bom existe em `Untitled.md`, mas não linkado a nenhuma das 3 disciplinas e sem nome próprio |
| `Estática/` | EM306 | 🔴 Vazia | |
| `Resistência dos Materiais 1/` | ES510 | 🔴 Vazia | |
| `Dinâmica/` | EM404 | 🔴 Vazia | |

### 3.3 Computação
| Pasta | Disciplina | Status | Observação |
|---|---|---|---|
| `MC322/`, `MC102/`, `MC404/`, `MC202/` | cada uma isolada | 🔴 Vazia (x4) | mesmo `MC102`/`MC202` com bom detalhamento de ementa, zero nota pessoal |
| `Redes/` | ES900 + 3 subpastas | 🟢 **Rica (destaque do vault)** | MOCs excelentes, 7 camadas OSI completas, protocolos industriais, projeto de rede doméstica |

### 3.4 Elétrica
| Pasta | Disciplina | Status | Observação |
|---|---|---|---|
| `Circuitos Lógicos/` | ES571 | 🟡 Fraca | 1 nota boa (Sistemas de Numeração), `VHDL.md` vazia, checklist 6/17 |
| `Circuitos Elétricos 1/` | EA513 | 🟡 Fraca | `Leis de Kirchhoff.md` só tem perguntas sem resposta |
| `Circuitos Elétricos 2/` | EA611 | 🔴 Vazia | |
| `Princípios de Conversão de Energia/` | ET520 | 🟢 Rica | Transformador Ideal/Real excelentes; Magnetismo é só fórmula |
| `Eletrônica Básica 1/` | EE533 | 🔴 Vazia | |
| `Eletrônica Digital 1/` | EE610 | 🔴 Vazia | |

### 3.5 Matemática
| Pasta | Disciplina | Status | Observação |
|---|---|---|---|
| `Cálculo 1/` | MA111 | 🟡 Fraca | 3 notas totalmente vazias (Derivative Table, Integral Table, Limits and continuity) |
| `Cálculo 2/` | MA211 | 🔴 Vazia na prática | ementa detalhada, zero explicação pessoal |
| `Cálculo 3/` | MA311 | 🟡 Mista | Sequências e Séries / Laplace excelentes; Fourier incompleta; Heaviside vazia |
| `Pré Cálculo/` | — | 🔴 Vazia na prática | |
| `Modelos Probabilisticos/` *(sic)* | ME323 | 🟢 Rica | Contagem e Espaço Amostral boas; Variáveis Aleatórias vazia |
| `Algebra Linear/` | MA327 | 🟢 Rica | Autovalores/Autovetores e Forma de Jordan excelentes |
| `Cálculo Numérico/` | MS211 | 🔴 Vazia | |
| `Geometria Analítica/` | MA141 | 🔴 Vazia | |

### 3.6 Física
| Pasta | Disciplina | Status | Observação |
|---|---|---|---|
| `Física Geral 1/` | F128 | 🔴 Vazia | |
| `Fisica Geral 2/` | F228 | 🟡 Fraca | `Ondas em 1 D.md` vazia, resto é fórmula solta sem explicação |
| `Física Geral 3/` | F328 | 🔴 Vazia | |
| `Física Geral 4/` | F428 | 🟡 Confusa | `Formulário A4.md` vazia; `p.md` e `Aula Exploratória 09.md` mal nomeadas e parecem colagem de resolução de IA |

### 3.7 Controle e Automação
| Pasta | Disciplina | Status | Observação |
|---|---|---|---|
| `Análise Linear/` | ES601 | 🟡 Fraca | conteúdo espalhado, `Untitled 1.md`, checklist duplicado (`Content Checklist.md`) |
| `Controle/` | ES710 | 🔴 Vazia | |
| `Controle Avançado/` | ES728 | 🟢 Rica | 2 notas excelentes sobre matriz de transição de estados |
| `Instumentação/` *(sic)* | ES704 | 🟡 Fraca | só fórmulas, sem explicação |
| `Automação Industrial/` | ES926 | 🔴 Vazia | |

### 3.8 Outras áreas (sem nota-índice de disciplina)
| Pasta | Status | Observação |
|---|---|---|
| `Sistemas Produtivos/` | 🟢 Rica | mas `LISTA DE EXERCÍCIO.md` expõe nome completo + RA |
| `Economia/` | 🟡 Confusa | `Untitled.md` (2 linhas soltas) + `Lista 2.md` é uma colagem crua de conversa de IA |
| `Geociências/` | 🔴 Fraca | notas soltas, mal nomeadas, sem estrutura |

### 3.9 Fora de `Course/`
| Pasta | Status | Observação |
|---|---|---|
| `Latex/` | 🟢 Rica | ótimos guias de referência, mas `Circuitikz.md` tem blocos de código repetidos (mesmo exemplo colado várias vezes) |
| `Processor/` | 🟢 Rica | projeto pessoal muito bem documentado |
| `IC/` | 🟡 Confusa | anotações soltas misturando tarefas pessoais e conteúdo técnico; `Sem título.md` |
| `Templates/` | ⚪ Ok | é o template, comportamento esperado |
| `Excalidraw/` | ⚪ Ok, mas | nome do arquivo é um timestamp (`Drawing 2026-04-09 20.33.25`), pouco descritivo |

### 3.10 Números gerais
- ~38 notas-índice de disciplina → **100%** são só ementa
- ~20 pastas 🔴 vazias (nada além da ementa)
- ~12 pastas 🟡 fracas/confusas
- ~8 pastas 🟢 realmente ricas
- **11 notas totalmente vazias** (0 conteúdo), espalhadas pelo vault
- **5 notas com nome genérico** ("Untitled" x3, "Sem título", e uma pasta com duas "Untitled.md" diferentes)
- **2 notas com conteúdo cortado no meio** (`Transformada de Fourier.md`, `Camada 5 - Sessão.md`)
- **3 notas com resíduo de conversa de IA colado** (`Lista 2.md`, `Transformador Real.md`, `Aula Exploratória 09.md`)

## 4. O que já funciona bem (preservar e replicar)

- **MOC (Map of Content)**: `Modelo OSI`, `Redes e Protocolos Industriais`, `Home Network Upgrade` — nota central que linka sub-notas com tabela resumo. É o melhor padrão do vault e está sub-utilizado fora de Redes.
- **Estrutura fixa por nota de conteúdo**: Função Principal → PDU → Serviço/Interface/Protocolo → Hardware → Aplicação prática (as 7 camadas OSI seguem isso à risca). Dá consistência sem virar texto genérico.
- **Frontmatter com `Pré Requisitos` como wikilink** — cria um grafo de dependência entre disciplinas de graça.
- **Exemplo resolvido passo a passo** (Autovalores e Autovetores, Matriz de Transição de Estados) — é onde o "aprender escrevendo" realmente acontece.
- **Emoji como âncora visual de seção** (📦 🛠️ ⚙️ 🔍) — ótimo pra escanear, mas só é usado em Redes.
- **circuitikz para diagramas** de circuitos e sistemas massa-mola — resultado com cara de livro didático.

## 5. Problemas recorrentes

1. **Notas-índice nunca viram hub de estudo** — são só ementa, e o conteúdo real (quando existe) fica desconectado.
2. **11 notas vazias** dão falsa sensação de progresso na lista de arquivos.
3. **Nomes genéricos** (`Untitled.md`, `Untitled 1.md`, `Sem título.md`) quebram busca e backlink.
4. **Typo recorrente no frontmatter**: tag `Cource` (praticamente todas as ~38 notas de disciplina, deveria ser `Course`) e `Mathmatics` (nas 3 notas de Cálculo, deveria ser `Mathematics`).
5. **Typos em nome de pasta**: `Ternodinâmica` → Termodinâmica; `Instumentação` → Instrumentação; `Modelos Probabilisticos` → Probabilísticos; `Fisica Geral 2` é a única subpasta de Física sem acento (as outras três têm).
6. **Conteúdo cortado no meio da frase/integral** em 2 notas importantes (Fourier, Camada 5).
7. **Colagem crua de chat de IA**, incluindo diálogo residual ("Gostaria que eu continuasse...", "Excelente escolha!") e o nome do usuário exposto no meio do texto.
8. **Dado pessoal identificável**: nome completo + RA em `LISTA DE EXERCÍCIO.md`.
9. **Mistura de idioma sem critério aparente**: Laplace e Séries em inglês, resto do vault em português.
10. **Tabela placeholder esquecida** em `Tabela da Transformada de Laplace.md` (uma tabela de exemplo "Coluna 1/Linha 1" antes da tabela real).
11. **Checklist duplicado e dessincronizado** entre `ES601` e `Content Checklist.md`.
12. **DAC apontando para anos diferentes** (2023 a 2026) sem padrão, dificultando saber se o link ainda é válido.
13. **Campo de progresso inconsistente** — `Cursado:` só aparece em 6 das ~38 notas, e olhe lá.

## 6. Proposta de padronização

### 6.1 Novo `Template - Disciplina.md`
O template atual só tem frontmatter vazio. Proposta de expansão:

```markdown
---
tags:
  - Course
  - Unicamp
  - <Área>            # Mecânica, Elétrica, Computação, Matemática, Física, Controle, Química
aliases:
  - <Código>
Nome:
Código:
Cursado:              # ex: 2026/1 — deixe vazio se ainda não cursou
DAC:
Status: Não iniciado  # Não iniciado | Em andamento | Concluído
Pré Requisitos:
---
> [!abstract] Ementa
> (cole a ementa oficial do DAC aqui, sem editar)

## 🗺️ Mapa de Conteúdo
- [ ] Tópico 1 → [[Nota do tópico 1]]
- [ ] Tópico 2 → [[Nota do tópico 2]]

## 📝 Observações gerais da disciplina
(o que for de aula que não vira nota própria: recados, formato de prova, etc.)
```
Isso resolve os problemas #1 e #2: a nota-índice vira MOC de verdade, e cada tópico linka pra uma nota de conteúdo (que linka de volta).

### 6.2 Convenção de nomes de arquivo
- Nunca deixar "Untitled" / "Sem título" — nomear pelo assunto assim que escrever a primeira frase.
- Nome de nota de conteúdo = o **conceito**, não a origem ("Lista 2" → algo como "Economia - Consumo, Investimento e Juros (Keynes)").
- Corrigir os typos de pasta listados no item 5.5 assim que possível (renomear pasta no Obsidian atualiza os links automaticamente).

### 6.3 Tags padronizadas
- Corrigir globalmente `Cource` → `Course` e `Mathmatics` → `Mathematics` (find & replace no vault todo).
- Como o vault é majoritariamente PT-BR, considerar migrar as tags de área para português (`Computação`, `Elétrica`, `Mecânica`...) por consistência com o resto do conteúdo.
- Tags de status (`#status/vazio`, `#status/rascunho`, `#status/completo`) pra localizar notas incompletas com uma busca só.

### 6.4 Padrão de nota de conteúdo
Baseado no que já funciona nas notas de Redes e Controle Avançado:
1. Frase de abertura contextualizando o "porquê" do conceito.
2. Definição/fórmula.
3. Exemplo resolvido passo a passo (ponto forte atual — replicar sempre que possível).
4. Aplicação prática / conexão com outra matéria — é o que separa "arquivo" de "aprendizado".
5. Link de volta pra nota-índice da disciplina e para os pré-requisitos usados.

### 6.5 Regra de ouro
Nenhuma nota fica com 0 linhas de conteúdo por mais de uma semana: ou vira um `> [!todo] Ainda não estudei isso` explícito, ou é apagada. Isso mata a "falsa sensação de completude" das notas vazias.

## 7. Plano de ação priorizado

**Fase 1 — Limpeza rápida (baixo esforço, alto impacto)**
- [ ] Corrigir tag `Cource` → `Course` em todas as notas de disciplina
- [ ] Renomear as 5 notas "Untitled/Sem título" pra nomes descritivos
- [ ] Decidir: apagar ou marcar como `> [!todo]` as 11 notas vazias
- [ ] Reescrever `Lista 2.md` e o início de `Transformador Real.md` removendo resíduo de chat e o nome do usuário
- [ ] Corrigir nomes de pasta: `Ternodinâmica`→Termodinâmica, `Instumentação`→Instrumentação, `Modelos Probabilisticos`→Probabilísticos
- [ ] Remover a tabela placeholder em `Tabela da Transformada de Laplace.md`
- [ ] Avaliar remover/anonimizar o RA em `LISTA DE EXERCÍCIO.md`

**Fase 2 — Estrutura (esforço médio)**
- [ ] Atualizar `Template - Disciplina.md` com o formato da seção 6.1
- [ ] Nas 8 disciplinas 🟢 ricas, transformar a nota-índice em MOC real linkando o conteúdo já existente
- [ ] Unificar os checklists duplicados de `ES601`/`Content Checklist.md`
- [ ] Terminar as 2 notas cortadas no meio (Fourier, Camada 5 - Sessão)

**Fase 3 — Conteúdo (contínuo — é o objetivo real)**
- [ ] Priorizar disciplinas do semestre atual (`Cursado` em branco) pra não deixar acumular
- [ ] Preencher as ~20 pastas 🔴 vazias conforme as aulas forem acontecendo, seguindo o novo template
- [ ] Replicar o padrão das Camadas OSI em outras sequências temáticas longas (as 3 disciplinas de Termodinâmica, os dois transformadores, etc.)

---
*Quer que eu já reescreva o `Template - Disciplina.md` atualizado, ou comece limpando alguma das notas específicas citadas aqui (ex: `Lista 2.md`)?*
