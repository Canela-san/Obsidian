Um protocolo determinístico e de alta velocidade criado na Europa, projetado especificamente para ser a espinha dorsal de fábricas inteiras com milhares de I/Os.

- **Como funciona:** Ele mistura duas lógicas. Entre os controladores (Mestres), ele usa passagem de bastão (_Token Passing_), onde cada Mestre tem um tempo garantido para falar. Entre o Controlador e os I/Os remotos (Escravos), ele usa _Polling_ (varredura contínua e previsível).
    
- **Vantagem:** É extremamente robusto, rápido (até 12 Mbps na versão DP) e possui diagnósticos ricos na própria camada de protocolo. Se um cabo romper ou um sensor falhar, o CLP sabe exatamente qual nó da rede apresentou problema.
    
- **Variantes:** Existe o **PROFIBUS DP** (Descentralized Periphery) para manufatura discreta rápida, e o **PROFIBUS PA** (Process Automation) que leva energia e dados no mesmo cabo para áreas com risco de explosão.