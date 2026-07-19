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
- Conexão de rede estável
- (Opcional) máquina com vários cores para concorrência alta

## Instalação

### Build rápido
```bash
git clone https://github.com/ProezaDEV/ddos-attack-stress.git
cd ddos-attack-stress
cargo build --release
```

Binário: `target/release/stress` (Windows: `stress.exe`)

### Build manual
```bash
cargo clean
cargo build --release
```

---

## Uso

> Sempre inclua `--i-am-authorized`. Sem essa flag, o programa **não executa**.

### Padrão básico
```bash
./target/release/stress \
  --url https://seu-servidor.local/health \
  --concurrency 32 \
  --requests 1000 \
  --method GET \
  --i-am-authorized
```

### 1. Load leve (smoke test)
Bom para validar se o endpoint aguenta um pouco de tráfego.
```bash
./target/release/stress \
  --url https://seu-servidor.local/ \
  -c 8 \
  -r 200 \
  -m GET \
  --timeout 5 \
  --i-am-authorized
```

### 2. Load médio (API)
Simula vários clientes batendo na API ao mesmo tempo.
```bash
./target/release/stress \
  --url https://api.seu-dominio.local/v1/status \
  -c 32 \
  -r 2000 \
  -m GET \
  --timeout 10 \
  --i-am-authorized
```

### 3. Load alto (stress)
Pressão maior — monitore CPU/RAM do **seu** servidor.
```bash
./target/release/stress \
  --url https://seu-servidor.local/health \
  -c 100 \
  -r 10000 \
  -m GET \
  --timeout 15 \
  --i-am-authorized
```

### 4. Método POST
Útil para endpoints de criação / formulário (no **seu** backend).
```bash
./target/release/stress \
  --url https://api.seu-dominio.local/v1/echo \
  -c 20 \
  -r 500 \
  -m POST \
  --i-am-authorized
```

### 5. Método PUT
```bash
./target/release/stress \
  --url https://api.seu-dominio.local/v1/items/1 \
  -c 16 \
  -r 400 \
  -m PUT \
  --i-am-authorized
```

### 6. Método HEAD
Testa só headers (menos payload).
```bash
./target/release/stress \
  --url https://seu-servidor.local/ \
  -c 40 \
  -r 3000 \
  -m HEAD \
  --i-am-authorized
```

### 7. Timeout curto (rede instável / latência)
```bash
./target/release/stress \
  --url https://seu-servidor.local/slow \
  -c 24 \
  -r 800 \
  -m GET \
  --timeout 3 \
  --i-am-authorized
```

### 8. Windows (PowerShell)
```powershell
.\target\release\stress.exe `
  --url https://seu-servidor.local/health `
  -c 32 `
  -r 1000 `
  -m GET `
  --i-am-authorized
```

---

## Flags

| Flag | Descrição |
| :--- | :--- |
| `--url` | URL do alvo autorizado |
| `-c, --concurrency` | Workers em paralelo (padrão: `32`) |
| `-r, --requests` | Total de requests (padrão: `1000`) |
| `-m, --method` | `GET` / `POST` / `PUT` / `HEAD` |
| `--timeout` | Timeout por request em segundos (padrão: `10`) |
| `--i-am-authorized` | **Obrigatório** — confirma autorização |

---

## Dicas de performance

1. Comece com pouca concorrência (`-c 8`) e vá subindo.
2. Acompanhe CPU, memória e logs do **seu** serviço durante o teste.
3. Se aparecer muita falha, reduza `-c` / `-r` ou aumente `--timeout`.
4. Prefira testar em staging / localhost antes de produção.

## Troubleshooting

**Recusou executar**
- Falta `--i-am-authorized`.

**Muitos `failed`**
- Alvo fora do ar, timeout baixo ou concorrência alta demais.

**Erro de compilação**
```bash
rustup update
cargo clean && cargo build --release
```

---

## Aviso legal

### Uso permitido
- Testar infraestrutura **sua**
- Ambiente de lab / staging com permissão
- Aprendizado de performance e hardening

### Uso proibido
- Atacar sistemas sem autorização
- Derrubar serviços de terceiros
- Qualquer atividade ilegal

## Autor

**ProezaDEV**  
Criação própria · Full Stack · Ethical Hacking

---

<div align="center">

**ddos-attack-stress** · by ProezaDEV

</div>
