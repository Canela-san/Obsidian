
IO-Link **não é um _fieldbus_ (barramento de campo)**, mas sim a evolução digital do cabeamento ponto a ponto padrão. É o que há de mais moderno para garantir máxima qualidade de dados nos sensores.

- **Como funciona:** Ele substitui o cabo simples de 24V (que antes apenas mandava um sinal "ligado/desligado" ou analógico) por uma comunicação serial bidirecional digital em um cabo padrão de 3 fios não blindado. O sensor IO-Link se conecta a um "Mestre IO-Link", e este Mestre se comunica com o CLP via PROFINET ou EtherNet/IP.
    
- **Vantagem:** Traz o diagnóstico para a ponta. Você pode reparametrizar um sensor remotamente se a receita de produção mudar, ou o próprio sensor pode avisar ao sistema: _"Estou funcionando, mas minha lente está ficando suja, agende manutenção"_.