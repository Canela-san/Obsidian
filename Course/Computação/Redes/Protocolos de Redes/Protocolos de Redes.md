tudo depende do quanto importante é a conexão, por isso os equipamentos são separados por níveis, cada nível deve usar diferentes protocos/infra estruturas:

Nivel 0:
[[IO-link]]
[[HART (Highway Addressable Remote Transducer)]]
[[Modbus RTU]]
[[PROFIBUS]]

| **Característica** | **HART**                           | **Modbus RTU**                  | **PROFIBUS (DP)**                         | **IO-Link**                           |
| ------------------ | ---------------------------------- | ------------------------------- | ----------------------------------------- | ------------------------------------- |
| **Topologia**      | Ponto a Ponto / Barramento (lento) | Barramento (Mestre/Escravo)     | Barramento, Árvore, Estrela               | **Estritamente Ponto a Ponto**        |
| **Meio Físico**    | Cabo de par trançado (2 fios)      | RS-485 (2 ou 4 fios)            | RS-485 especial (Cabo Roxo)               | Cabo de sensor padrão (3 fios)        |
| **Sinal**          | Híbrido (Analógico + Digital)      | Digital (Serial)                | Digital (Serial)                          | Digital                               |
| **Foco Principal** | Instrumentação de Processo         | Integração Geral de Baixo Custo | Controle de Manufatura de Alta Velocidade | Última milha (Inteligência do Sensor) |

nivel 1:
