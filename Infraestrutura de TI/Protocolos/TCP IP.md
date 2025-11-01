# Protocolo TCP IP

O Protocolo TCP (*Transmission Control Protocol*) é o processo conhecido como *Three Way Handshake*, que seria como um aperto de mão de três etapas. Para a web, a comunicação ocorre através do protocolo HTTP usando a porta 80 (inseguro) / 8080 (porta alternativa) ou HTTPS 443 (segura).

> TCP trabalha na camada de transporte e IP na camada de rede.
### O que é o Three Way Handshake?
É o processo que estabelece uma conexão confiável entre dois dispositivos através do protocolo TCP. Ele garante que cliente e servidor estejam prontos para trocar dados, minimizando erros de transmissão. Esse processo consiste de três etapas:
1. **SYN (Synchronize):** O cliente envia um pedido para iniciar a conexão, que contém:
	SYN = 1
	Número de sequência inicial, que é um número aleatório
	"Olá, servidor! Eu quero iniciar uma conexão, o meu número é `x`."

2. **SYN-ACK (Synchronize-Acknowledge):** O servidor responde confirmando o recebimento.
	SYN = 1 (O servidor também quer sincronizar)
	ACK = 1 (Confirma que recebeu o SYN do cliente)
	O servidor escolhe seu próprio número inicial e passa para o cliente (Seq = y)
	Confirma que recebeu o número de sequência do cliente (Ack = x + 1)
	"Recebi seu pedido `x`, aqui está meu número inicial `y`."

3. **ACK (Acknowledge):** O cliente confirma que recebeu a resposta e a conexão é estabelecida.
	ACK = 1 (Confirmação da resposta do servidor)
	Próximo número de sequência que o cliente usará. (Seq = x + 1)
	Confirma o número de sequência do servidor. (Ack = y + 1)
	"Recebi seu número `y`, vamos trocar dados."

![Syn Syn-Ack Ack](imgs/syn-synack-ack.jpeg)

- **SPORT:** Source Port = Porta de Origem 
	É uma porta qualquer entre **49152 e 65535** (faixa de portas efêmeras ou temporárias)
- **DPORT:** Destination Port = Porta de Destino
	É **fixa e conhecida**, pois representa o tipo de serviço solicitado.

Esses campos fazem parte do **cabeçalho TCP ou UDP**, e **identificam quais aplicações estão se comunicando** dentro dos dispositivos.

| Serviço                         | Porta Padrão (DPORT) |
| ------------------------------- | :------------------: |
| HTTP (web)                      |          80          |
| HTTPS (web segura)              |         443          |
| FTP (transferência de arquivos) |          21          |
| SSH (acesso remoto seguro)      |          22          |
| DNS (resolução de nomes)        |          53          |
| SMTP (envio de e-mails)         |          25          |
### Camadas

| **Modelo OSI**             | **Modelo Híbrido (TCP/IP V2)** | **Arquitetura TCP/IP**      | **Principais Protocolos**                                 |
| -------------------------- | ------------------------------ | --------------------------- | --------------------------------------------------------- |
| 7 – Camada de Aplicação    | 5 – Camada de Aplicação        | 4 – Camada de Aplicação     | _HTTP(S), FTP, SMTP, DNS, Telnet, POP3, IMAP, SNMP, DHCP_ |
| 6 – Camada de Apresentação |                                |                             | _SSL, TLS, MIME, XDR, ASN 1, ASCII, PGP_                  |
| 5 – Camada de Sessão       |                                |                             | _NetBIOS, SAP, PPTP, RTP, SOCKS_                          |
| 4 – Camada de Transporte   | 4 – Camada de Transporte       | 3 – Camada de Transporte    | _TCP, UDP, SCTP_                                          |
| 3 – Camada de Rede         | 3 – Camada de Rede             | 2 – Camada de Rede          | _IP, ICMP, IGMP_                                          |
| 2 – Camada de Enlace       | 2 – Camada de Enlace           |                             | _Ethernet, Wi-Fi, WiMAX, PPP, ARP, VLAN, MAC_             |
| 1 – Camada Física          | 1 – Camada Física              | 1 – Camada de Acesso à Rede | _Infrared, Bluetooth, USB_                                |
### Problemas de Cibersegurança

😈 [Ataque DDoS](Ataque%20DDoS.md) de inundação SYN se aproveita de uma vulnerabilidade no handshake TCP/IP para sobrecarregar um servidor com conexões TCP.

