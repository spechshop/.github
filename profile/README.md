# spechshop

**spechshop** é um conjunto de projetos voltados a **VoIP, SIP e processamento de mídia em tempo real**.

O foco do ecossistema é **controle técnico**, **previsibilidade** e **desempenho**, evitando dependências externas pesadas e abstrações opacas.

---

## Escopo

Os repositórios da spechshop cobrem:

- Sinalização SIP
- Proxy e roteamento RTP
- Processamento de áudio em tempo real
- Transcodificação e reamostragem
- Workers de mídia dedicados
- Integração com Web e aplicações internas

A arquitetura prioriza processos explícitos e fluxo de dados observável.

---

## Componentes

### spechshop (core)
- Servidor SIP próprio
- Workers RTP isolados por chamada
- Discadora automática
- Painel web e controle operacional

### libspech
- Biblioteca base de controle de chamadas
- Estado previsível e desacoplado
- Integração direta com workers de mídia

### Extensões nativas
Extensões PHP escritas em C para tarefas críticas de áudio:
- G.729
- Opus
- Reamostragem de PCM
- Utilitários RTP e DTMF (RFC 2833)

### Workers de mídia
- UDP direto
- Aprendizado automático de origem (comedia)
- Transcodificação em tempo real
- Emissão RTP com SSRC próprio
- Encaminhamento controlado de pacotes

---

## Tecnologias

- PHP 8.x
- Swoole (coroutines, UDP, TCP)
- C (extensões PHP)
- SIP / RTP
- Opus, G.729, PCMA, PCMU
- SQLite / JSON
- Linux

---

## Diretrizes

- Clareza de fluxo > abstração excessiva
- Processos explícitos
- Estado controlável
- Dependências mínimas
- Código auditável

---

## Licenciamento

Cada repositório possui seu próprio arquivo `LICENSE`.

O uso, redistribuição ou aplicação comercial dependem dos termos definidos em cada projeto.

---

## Autor

Desenvolvido e mantido por **Lotus / berzersks**.
