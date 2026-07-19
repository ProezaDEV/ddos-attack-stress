<div align="center">

<img src="assets/banner.png" width="100%" alt="ALERT · DDOS-ATTACK" />

# ddos-attack-stress

**Teste de carga HTTP autorizado** · visual dark · Rust

[![Rust](https://img.shields.io/badge/Rust-1.70+-0a0a0a?style=for-the-badge&logo=rust&logoColor=ef4444)](https://www.rust-lang.org/)
[![License](https://img.shields.io/badge/License-MIT-7f1d1d?style=for-the-badge)](LICENSE)
[![Autor](https://img.shields.io/badge/Autor-ProezaDEV-ef4444?style=for-the-badge&logo=github&logoColor=white)](https://github.com/ProezaDEV)

</div>

---

> [!WARNING]
> **Somente alvos autorizados.**  
> Use apenas em sistemas **seus** ou com **permissão explícita**.  
> Uso contra terceiros sem autorização é ilegal.

## Sobre

Ferramenta de **stress / load test HTTP** criada por **ProezaDEV**.  
Serve para medir como **seu** serviço se comporta sob concorrência.

| Recurso | Detalhe |
| :--- | :--- |
| Load HTTP | GET / POST / PUT / HEAD em paralelo |
| Métricas | ok / falha / bytes / req/s |
| Segurança | exige `--i-am-authorized` para rodar |

## Requisitos

- Rust 1.70+
- URL HTTP(S) que você tem permissão para testar

## Build

```bash
cargo build --release
```

Binário: `target/release/stress` (Windows: `stress.exe`)

## Uso

```bash
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
| `-c, --concurrency` | Workers em paralelo (padrão: 32) |
| `-r, --requests` | Total de requests (padrão: 1000) |
| `-m, --method` | GET / POST / PUT / HEAD |
| `--timeout` | Timeout em segundos |
| `--i-am-authorized` | **Obrigatório** — confirma autorização |

Sem `--i-am-authorized`, o programa **não executa**.

## Aviso legal

- Não use para atacar sites, APIs ou infraestrutura de terceiros.
- Responsabilidade pelo uso é de quem executa.

## Autor

**ProezaDEV**  
Criação própria · Full Stack · Ethical Hacking

---

<div align="center">

**ddos-attack-stress** · by ProezaDEV

</div>
