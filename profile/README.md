# Spech

Infraestrutura **VoIP, SIP e mídia em tempo real** construída principalmente com **PHP + Swoole**.

A Spech desenvolve uma stack própria para sinalização SIP, transporte RTP, processamento de áudio e aplicações de telefonia, com foco em **controle do protocolo, desempenho, observabilidade e poucas camadas intermediárias**.

[Website](https://spechshop.com) · [SpechPhone](https://phone.spechshop.com)

---

## Ecossistema

### SipSwoole

Plataforma SIP/B2BUA da Spech e base da infraestrutura de telefonia em produção.

- Sinalização SIP em UDP e TCP
- Registro e autenticação SIP
- Controle de diálogos e transações
- Roteamento de chamadas e trunks
- Proxy e processamento de mídia RTP
- Workers de mídia distribuídos
- CDR, billing e controle operacional
- Arquitetura assíncrona baseada em Swoole

O SipSwoole é desenvolvido como o núcleo operacional da plataforma; componentes reutilizáveis e ferramentas relacionadas são publicados separadamente nesta organização.

### [libspech](https://github.com/spechshop/libspech)

Biblioteca VoIP SIP/RTP para PHP, construída sobre corrotinas Swoole.

Permite criar aplicações que fazem e recebem chamadas, processam mídia RTP, enviam DTMF, gravam áudio e controlam sessões SIP diretamente em PHP.

Principais protocolos e recursos:

- SIP / SDP
- RTP / RTCP
- Digest Authentication
- DTMF via RFC 2833
- PCMA / PCMU / G.729 / Opus
- Callbacks de eventos e mídia em tempo real

### [pcg729](https://github.com/spechshop/pcg729)

Runtime PHP voltado ao ecossistema de mídia da Spech.

O projeto parte do Static PHP CLI e reúne em um único runtime as extensões necessárias para aplicações VoIP, incluindo Swoole e codecs/processamento de áudio nativos.

Entre os componentes utilizados pelo ecossistema estão:

- PHP 8.x
- Swoole
- BCG729
- Opus
- Reamostragem PCM

### [SpechPhone](https://github.com/spechshop/softphone)

Softphone web open source integrado à `libspech`.

A arquitetura utiliza SIP e RTP diretamente no backend, com uma ponte de mídia em tempo real para o navegador, sem transformar a infraestrutura SIP existente em uma stack WebRTC.

Demo: [phone.spechshop.com](https://phone.spechshop.com)

### [LIPC / File Manager](https://github.com/spechshop/filemanager)

Ambiente web de desenvolvimento e gerenciamento de arquivos usado como tooling no ecossistema Spech, com editor Monaco, terminal PTY, WebSocket e integração com agentes de desenvolvimento.

---

## Stack técnica

```text
Application / Control
        │
        ▼
   PHP 8.x + Swoole
        │
   ┌────┴────┐
   │         │
  SIP       RTP
UDP/TCP   Media workers
   │         │
   └────┬────┘
        │
        ▼
 Native audio codecs
 G.729 · Opus · G.711
```

Tecnologias utilizadas nos projetos incluem:

- PHP 8.x
- Swoole 6
- C / extensões nativas PHP
- SIP, SDP, RTP e RTCP
- UDP e TCP
- PCMA, PCMU, G.729 e Opus
- PostgreSQL, Redis e SQLite conforme o componente
- Linux

---

## Princípios de engenharia

- **Fluxo explícito:** sinalização e mídia devem ser rastreáveis e compreensíveis.
- **Controle do protocolo:** evitar abstrações que escondam comportamento relevante de SIP/RTP.
- **I/O assíncrono:** utilizar corrotinas e event loops no caminho crítico de rede.
- **Mídia isolada:** separar processamento RTP do plano de sinalização sempre que necessário.
- **Dependências conscientes:** adicionar infraestrutura somente quando ela resolve um problema real.
- **Código auditável:** comportamento de rede e estado de chamadas devem poder ser inspecionados.

---

## Open source

Parte da tecnologia desenvolvida pela Spech é disponibilizada publicamente nesta organização.

Cada repositório possui seus próprios termos de licença, estágio de maturidade e documentação. Consulte o arquivo `LICENSE` do projeto antes de utilizar ou redistribuir o código.

---

Desenvolvido e mantido por **Lotus / [berzersks](https://github.com/berzersks)**.
