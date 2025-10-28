# Ataque DDoS de Inundação SYN

## SYN Flood DDoS Attack
Um ataque distribuído de negação de serviço de SYN é um tipo de ataque DDoS (*Domain Denial of Service*) direcionado ao protocolo TCP na Camada 4 do modelo OSI, com o objetivo de interromper as atividades de um dispositivo de rede, balanceador de carga, dispositivo de gerenciamento de sessões ou servidor através da inundação de solicitações para se conectar a seus recursos.

Conhecido como "ataque meio-aberto", um ataque de inundação SYN se aproveita de uma vulnerabilidade no handshake TCP/IP para sobrecarregar um servidor com conexões TCP, impedindo que ele forneça serviços para tráfego e conexões legítimas.

![Syn Flood Attack](syn-flood-attack.webp)
## Tipos e Variações dos Ataques DDoS de Inundação SYN

### Half-Open Connections
Busca enviar muitos pacotes TCP com SYN (iniciar conexão) e não completar o handshake (não responder ao SYN-ACK), deixando o servidor com muitas conexões meio-abertas e esgotando a fila de backlog. Pode acontecer exaustão de recursos como memória e tabelas de conexão, assim como a negação de serviço para usuários legítimos.
#### Como combater o problema de Half-Open Connections?
1. **SYN Cookies:** o servidor não reserva recursos até receber o ACK final, as informações do SYN são codificada em um cookie (campo do número de sequência).
2. **Firewall:** Limitar conexões SYN por IP (*Rate Limiting*) ou globalmente através de iptables, nftables etc.
3. **Filtrar por IP:** Um ataque de origem única pode ser bloqueado.
4. **Proteção em Nível de Rede / Nuvem:** Usar firewall de borda ou serviços que mitigam ataques DDoS, como: Cloudflare, AWS Shield, Azure DDoS Protection, etc. Esses serviços têm infraestrutura para detectar e descartar um ataque de SYN Flood antes que chegue ao servidor.
### SYN Flood com IP Spoofing
Busca falsificar o endereço IP de origem dos SYN para que o servidor envie SYN-ACK para alvos falsos, que não respondem, tornando mais difícil de rastrear e bloquear, pois amplifica a dificuldade de filtragem por origem.

**Soluções:** Filtros anti-spoof ou uRPF (*Unicast Reverse Path Forwarding*)
### SYN-ACK Flood
Busca enviar desta vez um grande volume de pacotes SYN-ACK diretamente ao alvo, forçando-o a processar estados inesperados e consumir recursos, ocorrendo a sobrecarga do processamento de pacotes e de verificação de estados TCP.

### Distributed SYN Flood (botnet)
Múltiplos hosts distribuídos enviam SYNs em massa, tornando o tráfego volumoso e vindo de muitas fontes (difícil de bloquear por IP).

### Low and Slow SYN Flood / Pulsed Attack
Busca mandar os SYNs em taxas baixas ou em rajadas periódicas para driblar detecção por thresholds rígidos, podendo driblar detecção baseada em picos.

### Fragmented SYN / IP fragmentation abuse
Fragmenta pacotes ou explora fragmentação IP/TCP para complicar a reassemblagem e o processamento no alvo.

