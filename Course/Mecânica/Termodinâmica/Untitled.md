# Folha de Consulta - Sistemas Fluidotérmicos I

Este documento resume as equações e conceitos fundamentais abordados nos problemas propostos, cobrindo sistemas de refrigeração, turbinas a gás (para geração de potência e propulsão) e sistemas de compressão de gás.

## 1. Sistemas de Refrigeração por Compressão de Vapor (Baseado no PP01)

### 1.1. Conceitos Fundamentais

- **Ciclo de Refrigeração:** O objetivo é transferir calor de uma fonte fria (espaço refrigerado) para uma fonte quente (ambiente), consumindo trabalho.
    
- **Fluidos Refrigerantes:** Substâncias que sofrem mudança de fase no ciclo (ex: R134a).
    
- **Controle:**
    
    - **Rotação Constante:** O compressor opera em modo liga/desliga para manter a temperatura. Menos eficiente.
        
    - **Rotação Variável (Inverter):** O compressor ajusta sua velocidade para modular a capacidade de refrigeração, economizando energia.
        

### 1.2. Equações Principais

- **Efeito Útil de Refrigeração (**Q˙​e​**):** Quantidade de calor removida do ambiente refrigerado.
    
    Q˙​e​=m˙⋅(hsaıˊda,evap​−hentrada,evap​)
    
    Onde m˙ é a vazão mássica de refrigerante e h é a entalpia.
    
- **Potência do Compressor (**W˙c​**):** Trabalho necessário para comprimir o refrigerante.
    
    - **Potência Ideal (Isentrópica):**
        
        W˙c,s​=m˙⋅(h2s​−h1​)
        
        Onde h1​ é a entalpia na entrada e h2s​ é a entalpia na saída para uma compressão isentrópica.
        
    - **Potência Real:**
        
        W˙c,real​=ηis,c​W˙c,s​​=ηis,c​m˙⋅(h2s​−h1​)​
        
        Onde ηis,c​ é a eficiência isentrópica do compressor.
        
- **Coeficiente de Desempenho (COP):** Medida da eficiência do ciclo.
    
    COP=Trabalho GastoEfeito Desejado​=W˙c​Q˙​e​​
    
    Valores mais altos de COP indicam maior eficiência.
    
- **Troca de Calor no Condensador (**Q˙​c​**):** Calor rejeitado para o ambiente.
    
    Q˙​c​=m˙⋅(hsaıˊda,comp​−hsaıˊda,cond​)

### 1.3. Fatores de Melhoria de Eficiência

- **Uso de Fluidos Auxiliares (Água):** Reduz as diferenças de temperatura necessárias nos trocadores de calor (condensador e evaporador), diminuindo a relação de pressões do compressor e, consequentemente, o trabalho de compressão, aumentando o COP.
    
- **Controle de Pressão Flutuante (**_**Sliding Pressure**_**):** Em sistemas industriais, permite que a pressão de condensação varie com a temperatura ambiente, reduzindo o trabalho do compressor em dias mais frios.
    

## 2. Turbinas a Gás (Baseado no PP02)

### 2.1. Turbina a Gás para Geração de Potência (Ciclo Brayton)

- **Componentes:** Compressor, câmara de combustão, expansor (turbina).
    
- **Parâmetros Chave:** Razão de pressões (rp​), temperatura máxima do ciclo (Tmax​), eficiências isentrópicas do compressor e da turbina.
    

#### Equações Principais:

- **Trabalho do Compressor:**
    
    W˙c​=m˙ar​⋅(h2​−h1​)=ηis,c​m˙ar​⋅(h2s​−h1​)​
- **Trabalho da Turbina:**
    
    W˙t​=(m˙ar​+m˙comb​)⋅(h3​−h4​)=(m˙ar​+m˙comb​)⋅(h3​−h4s​)⋅ηis,t​
- **Calor Adicionado na Câmara de Combustão:**
    
    Q˙​add​=m˙comb​⋅PCI=(m˙ar​+m˙comb​)⋅h3​−m˙ar​⋅h2​
    
    Onde PCI é o Poder Calorífico Inferior do combustível.
    
- **Potência Líquida e Elétrica:**
    
    undefined
- **Eficiência Térmica:**
    
    ηt​=Q˙​add​W˙el,lıˊq​​=m˙comb​⋅PCIW˙el,lıˊq​​

### 2.2. Turbina a Gás para Propulsão (Turbojato)

- **Componentes Adicionais:** Difusor (entrada) e bocal (saída).
    
- **Objetivo:** Gerar empuxo através da aceleração do ar.
    

#### Equações Principais:

- **Empuxo (**F**):**
    
    F=m˙gases​⋅vsaıˊda​−m˙ar​⋅ventrada​+(psaıˊda​−pamb​)⋅Asaıˊda​
    
    Simplificando, se psaıˊda​=pamb​:
    
    F=(m˙ar​+m˙comb​)⋅vsaıˊda​−m˙ar​⋅ventrada​
- **Consumo Específico de Combustível (SFC -** _**Specific Fuel Consumption**_**):**
    
    SFC=Fm˙comb​​[kNg/s​]
    
    Mede a eficiência do motor; quanto menor, melhor.
    
- **Eficiência Propulsiva (**ηp​**):**
    
    ηp​=Energia Cineˊtica GeradaPoteˆncia de Propulsa˜o​=21​[(m˙ar​+m˙comb​)vsaıˊda2​−m˙ar​ventrada2​]F⋅vaeronave​​

## 3. Sistemas de Compressão de Gás (Baseado no PP03)

### 3.1. Compressão Estagiada com Resfriamento Intermediário

- **Objetivo:** Reduzir o trabalho total de compressão e aumentar o rendimento volumétrico em comparação com a compressão em um único estágio para a mesma pressão final.
    
- **Compressão Politrópica:** Um processo real de compressão modelado como p⋅Vn=constante, onde o expoente n fica entre 1 (isotérmico) e k (isentrópico).
    
    T1​T2​​=(p1​p2​​)nn−1​

### 3.2. Equações Principais

- **Trabalho de Compressão (Politrópico, por estágio):**
    
    wcomp​=n−1nRT1​​[(p1​p2​​)nn−1​−1]
- **Potência Total (Dois Estágios):**
    
    W˙total​=W˙estaˊgio 1​+W˙estaˊgio 2​
- **Calor Removido no Resfriador Intermediário (**_**Intercooler**_**):**
    
    Q˙​removido​=m˙ar​⋅(hsaıˊda,estaˊgio 1​−hentrada,estaˊgio 2​)=m˙ar​cp​(Tsaıˊda,estaˊgio 1​−Tentrada,estaˊgio 2​)
    
    Este calor é transferido para um fluido auxiliar (ex: água):
    
    Q˙​removido​=m˙aˊgua​cp,aˊgua​(Tsaıˊda,aˊgua​−Tentrada,aˊgua​)

### 3.3. Enchimento de Tanque (Regime Transiente)

- **Balanço de Energia para Volume de Controle (Tanque):** A variação da energia interna no tanque é igual à entalpia da massa que entra, menos o calor perdido para o ambiente.
    
    m2​u2​−m1​u1​=(m2​−m1​)hentrada​+Q1→2​
    - m1​,u1​: massa e energia interna inicial.
        
    - m2​,u2​: massa e energia interna final.
        
    - hentrada​: entalpia do gás que entra no tanque.
        
    - Q1→2​: calor trocado com o ambiente (negativo se for perda).
        
- **Gás Real vs. Gás Ideal:**
    
    - **Gás Ideal:** pV=mRT e u,h dependem apenas de T.
        
    - **Gás Real:** É preciso usar o fator de compressibilidade (Z).
        
        pV=ZmRT
        
        Onde Z é obtido de diagramas generalizados em função da pressão reduzida (pR​=p/pc​) e temperatura reduzida (TR​=T/Tc​).