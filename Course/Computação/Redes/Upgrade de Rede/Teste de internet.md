---
tags: - redes - isp - comparativo - homelab data: 2026-04-05
---
# Comparativo de Desempenho: Alares vs. Terra Fibra (Vivo)

> [!info] Contexto do Teste
> Este documento registra os testes de estresse realizados em ambas as operadoras simultaneamente na mesma infraestrutura (via cabo de rede genérico limitado a 100 Mbps no Pop!_OS). O objetivo foi determinar a melhor provedora para jogos online, focando em **latência (ping)**, **jitter (estabilidade)** e **perda de pacotes (packet loss)**. Plano de ambas: 700 Mbps.

## Metodologia

Foram utilizados testes via terminal Linux (`ping` e `mtr`) disparando 500 pacotes para servidores de DNS públicos (Google e Cloudflare). A escolha dessas ferramentas visa ignorar o limite do cabo de 100 Mbps e testar a saúde bruta da rota e infraestrutura de rede.

---

## 📊 Resumo dos Dados Coletados

### Teste 1: Ping (ICMP) - 500 Pacotes
Medição direta de tempo de resposta e estabilidade.

| Operadora       | Destino              | Perda de Pacotes | Ping Médio (avg) | Jitter / Variação (mdev) |
| :-------------- | :------------------- | :--------------- | :--------------- | :----------------------- |
| **Alares**      | Google (8.8.8.8)     | 0%               | 8.781 ms         | **0.492 ms**             |
| **Alares**      | Cloudflare (1.1.1.1) | 0.4%             | 9.236 ms         | **0.942 ms**             |
| **Terra Fibra** | Google (8.8.8.8)     | 0%               | 15.296 ms        | 0.670 ms                 |
| **Terra Fibra** | Cloudflare (1.1.1.1) | 0%               | 18.079 ms        | **9.080 ms** ⚠️          |


### Teste 2: Rastreio de Rota (MTR) - 500 Ciclos
Mapeamento dos "saltos" (hops) até o servidor DNS do Google (8.8.4.4) para identificar gargalos internos na infraestrutura da operadora.

| Operadora       | Latência no Destino Final | Jitter no Destino (StDev) | Anomalias na Rota (Gargalos)                                                                                                                          |
| :-------------- | :------------------------ | :------------------------ | :---------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Alares**      | 8.5 ms                    | **0.7 ms**                | Nenhuma. (Hop 2 com 100% loss é falso positivo por bloqueio de ICMP no roteador interno).                                                             |
| **Terra Fibra** | 14.4 ms                   | 0.9 ms                    | **Problemas na rede interna:** Hops 5 e 6 com perda real de pacotes (0.8% e 1.4%). Hop 4 apresentou pico de latência de 975.6 ms e StDev de 120.3 ms. |
|                 |                           |                           |                                                                                                                                                       |

---

## 🔎 Análise Técnica

### 1. Latência Bruta (Ping)
A **Alares** demonstrou um roteamento muito superior, entregando praticamente **metade da latência** da Terra Fibra em ambos os servidores testados. Em jogos online, uma diferença de ~9ms contra ~18ms na base da conexão é substancial.

### 2. Jitter e Estabilidade
O Jitter mede o desvio padrão da latência. Para jogos, a previsibilidade da conexão é vital.
* A **Alares** manteve a latência "cravada", com variações menores que 1 ms (mdev de 0.492 e 0.942).
* A **Terra Fibra** apresentou instabilidade severa na rota para a Cloudflare, com um jitter de `9.080 ms` e picos máximos de mais de 50 ms. Essa oscilação constante (rubberbanding) prejudica o registro de ações em tempo real.

### 3. Saúde da Rota e Perda de Pacotes
> [!warning] Alerta na Terra Fibra
> O teste de MTR revelou gargalos críticos na rede interna da Terra Fibra/Vivo. Os saltos `152-255-182-186.user.vivo` e `152-255-182-215.user.vivo` registraram perda real de pacotes e picos de latência absurdos (quase 1 segundo de atraso no Hop 4). Isso indica provável congestionamento na infraestrutura local da operadora.

Embora a Alares tenha apresentado uma perda minúscula (0.4%) no ping direto para a Cloudflare, a saúde geral do seu MTR foi exemplar, com comunicação limpa e estável até o destino final.

---

## 🏆 Veredito e Ações

> [!success] Vencedora: Alares
> A **Alares** superou a Terra Fibra em todos os critérios cruciais para aplicações em tempo real e jogos competitivos, entregando menor latência, rotas mais limpas e estabilidade de conexão (baixo jitter).

**Próximos Passos (Checklist):**
- [x] Rodar testes de estresse isolados via terminal.
- [x] Documentar dados e comparar.
- [ ] Cancelar contrato da Terra Fibra.
- [ ] Adquirir e instalar cabos de rede Cat5e ou Cat6 para substituir o cabeamento atual (gargalo de 100 Mbps) e liberar o limite real do plano de 700 Mbps.