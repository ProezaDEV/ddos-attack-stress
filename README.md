<div align="center">

<img src="assets/banner.png" width="100%" alt="ALERT · DDOS-ATTACK stress banner" />

# ddos-attack-stress

**Authorized HTTP load / stress tester** · dark lab aesthetic · Rust

[![Rust](https://img.shields.io/badge/Rust-1.70+-0a0a0a?style=for-the-badge&logo=rust&logoColor=ef4444)](https://www.rust-lang.org/)
[![License](https://img.shields.io/badge/License-MIT-7f1d1d?style=for-the-badge)](LICENSE)
[![Auth](https://img.shields.io/badge/Use-Authorized%20targets%20only-ef4444?style=for-the-badge)](#aviso-legal)

</div>

---

> [!WARNING]
> **Uso autorizado apenas.**  
> Esta ferramenta existe para medir carga em **sistemas seus** ou com **permissão explícita por escrito**.  
> Usar contra terceiros sem autorização é ilegal. O autor não se responsabiliza por abuso.

## O que é

Ferramenta **legítima de stress / load test HTTP** em Rust.  
Útil para ver como **sua** API ou site se comporta sob concorrência — sem spoofing, sem amplificação DNS, sem bypass de WAF/Cloudflare.

| Capacidade | Detalhe |
| :--- | :--- |
| HTTP load | GET / POST / PUT / HEAD concorrentes |
| Métricas | ok / fail / bytes / req/s |
| Gate de segurança | exige `--i-am-authorized` |

## Requisitos

- Rust 1.70+
- Alvo HTTP(S) que você tem permissão para testar

## Build

```bash
cargo build --release
```

Binário: `target/release/stress` (Windows: `stress.exe`)

## Uso

```bash
# Exemplo — somente em host autorizado
./target/release/stress \
  --url https://seu-servidor.local/health \
  --concurrency 32 \
  --requests 1000 \
  --method GET \
  --i-am-authorized
```

### Flags

| Flag | Descrição |
| :--- | :--- |
| `--url` | URL do alvo autorizado |
| `-c, --concurrency` | Workers paralelos (padrão: 32) |
| `-r, --requests` | Total de requests (padrão: 1000) |
| `-m, --method` | GET / POST / PUT / HEAD |
| `--timeout` | Timeout em segundos |
| `--i-am-authorized` | **Obrigatório** — confirma autorização |

Sem `--i-am-authorized`, o programa **recusa** executar.

## Aviso legal

- Não use para atacar sites, jogos, APIs ou infraestrutura alheia.
- Não é ferramenta de DDoS ofensivo (sem flood UDP, spoofing, reflection, evasion).
- Para aprendizado e hardening dos **seus** serviços.

## Autor

**ProezaDEV** · Full Stack · Ethical Hacking · PUC Minas

---

<div align="center">

**ddos-attack-stress** · authorized load only

</div>
