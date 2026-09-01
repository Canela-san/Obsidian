# Revisão Final: Organização do Trabalho e Sistemas Produtivos

## 1. Arranjos Físicos (Layouts) e Balanceamento

Esta área trata de como os recursos físicos e as tarefas são organizados no espaço para otimizar o fluxo.

- **Tipos Clássicos de Layout:**
    
    - **Posicional (Fixo):** O produto fica parado (ex: navio, avião) e os recursos vão até ele. Alta customização.
        
    - **Funcional (Por Processo):** Máquinas agrupadas por função (ex: setor de tornos, setor de fresas). Flexível, mas gera muito transporte interno e acúmulo de estoque em processo. Utiliza **Cartas de Relacionamento** (define importância de proximidade entre departamentos) e **Diagramas de Carregamento** (minimiza distância x volume) no projeto.
        
    - **Celular:** Agrupa máquinas diferentes para produzir uma família inteira de peças (layout em "U"). Reduz movimentação e facilita a polivalência do operador.
        
    - **Linha (Por Produto):** Produção em massa. Focado na padronização e divisão extrema do trabalho.
        
- **One Piece Flow (Fluxo Unitário):** Conceito onde uma única peça flui continuamente entre as estações de trabalho, sem formar lotes e sem gerar estoque intermediário.
    
- **Water Spider (Mizusumashi):** Operador logístico dedicado a reabastecer as células de manufatura. Ele garante que o operador da máquina foque apenas em agregar valor, sem parar para buscar peças.
    
- **Métricas Essenciais:**
    
    - **Takt-time:** É o ritmo da demanda do mercado. Calcula-se dividindo o _Tempo Disponível_ pela _Demanda do Cliente_.
        
    - **Tempo de Ciclo:** É o tempo real que o processo leva para concluir uma peça. (O ideal é Tempo de Ciclo $\le$ Takt-time).
        

## 2. Teoria das Restrições (TOC)

Foco em identificar e otimizar o "gargalo" (restrição) do sistema, pois ele define a capacidade total da fábrica.

- **Tipos de Restrição:**
    
    - _Interna:_ O gargalo está na fábrica (máquina lenta, falta de pessoal).
        
    - _Externa:_ O gargalo é o mercado (falta de demanda).
        
- **Quebrar a Restrição:** Aumentar a capacidade do gargalo atual até que ele deixe de ser a restrição (o que fará o gargalo mudar para outra etapa).
    
- **Sistema DBR (Drum-Buffer-Rope):**
    
    - **Tambor (Drum):** O gargalo. Ele dita o ritmo da fábrica inteira.
        
    - **Pulmão (Buffer):** Estoque de proteção imediatamente antes do gargalo, garantindo que ele _nunca_ pare por falta de material.
        
        - _Pulmões Secundários:_ Usados na _Montagem_ (para garantir que peças não-gargalo não atrasem a linha principal) e na _Expedição_ (para garantir prazo ao cliente).
            
    - **Corda (Rope):** Sistema de comunicação que sincroniza a liberação de matéria-prima no início da linha com a capacidade real do Tambor.
        

## 3. Sistema Toyota de Produção (STP) e Lean Manufacturing

A filosofia de "fazer mais com menos", combatendo ativamente qualquer tipo de desperdício (Muda).

- **Contexto Histórico e Problemas de Ford:** O STP nasceu no Japão pós-guerra (escassez de capital/espaço). Ohno e Toyoda perceberam que a superprodução fordista (produzir empurrando estoques gigantescos), máquinas inflexíveis de setups longos e o hábito de "deixar o conserto dos defeitos para o final" quebrariam uma empresa japonesa.
    
- **Pilares e Princípios:**
    
    - **JIT (Just-in-Time):** Produzir só o necessário, quando necessário. Baseado na produção _puxada_.
        
    - **Kanban:** Cartão visual usado para autorizar a produção ou movimentação no sistema puxado.
        
    - **Gestão por Estresse:** Ao remover as "gorduras" (estoques) do sistema, qualquer falha para a linha. Isso cria alta tensão constante no operário para manter a excelência.
        
- **Ferramentas e Práticas Fundamentais:**
    
    - **SMED (Troca Rápida de Ferramenta):** Reduzir setups para menos de 10 minutos convertendo "setup interno" (máquina parada) em "setup externo" (máquina operando).
        
    - **Heijunka (Nivelamento):** Produzir um mix nivelado ao invés de grandes lotes (ex: ABAB em vez de AAAABBBB) para não sobrecarregar fornecedores.
        
    - **Milk Run:** Sistema logístico de transporte programado onde um caminhão faz roteiros coletando pequenos lotes de múltiplos fornecedores em horários fixos.
        
    - **Supermercado Lean:** Estoque físico controlado entre processos. Só deve ser usado quando é tecnicamente impossível fazer fluxo contínuo.
        
    - **CCQ (Círculos de Controle da Qualidade):** Grupos de funcionários do chão de fábrica que resolvem problemas operacionais (Herança de Ishikawa).
        
- **Mapeamento de Fluxo de Valor (VSM):**
    
    - Ferramenta para enxergar o fluxo de materiais e informações de ponta a ponta. O _Estado Presente_ mostra os gargalos e desperdícios atuais; o _Estado Futuro_ projeta a melhoria contínua e o fluxo ideal.
        
    - **Métricas associadas:** _PCE (Process Cycle Efficiency)_ = Tempo Agregando Valor / Lead Time Total.
        

_Dica para a prova:_ Lembre-se de conectar a **Teoria das Restrições (TOC)** com o conceito de **Lead Time** e o gargalo; e o **SMED** do Lean com a viabilização prática do sistema celular e do JIT, já que setups rápidos permitem lotes menores. Boa prova!