É o "idioma universal" da automação. Desenvolvido no final dos anos 70, é um protocolo aberto, simples e incrivelmente difundido.

- **Como funciona:** Opera em uma topologia estrita de **Mestre/Escravo** sobre uma rede serial física, geralmente RS-485. O Mestre pergunta, o Escravo responde. Um escravo nunca fala sem ser requisitado.
    
- **Vantagem:** É extremamente leve e qualquer equipamento de qualquer fabricante no mundo praticamente tem suporte a ele. É excelente para interligar sistemas díspares.
    
- **Desvantagem:** É um protocolo "burro" para os padrões atuais. Ele transmite apenas registradores puros (números em hexadecimal), sem contexto. Você precisa saber previamente se aquele registrador significa temperatura, pressão ou status de erro. Além disso, é mais lento e suscetível a ruídos em cabos muito longos se não for bem aterrado.