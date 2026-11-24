<p align="center">
  <img src="assets/openclaw-banner.png" alt="OpenClaw - Personal AI Assistant" width="100%">
</p>

# ðŸ¦ž Docker OpenClaw

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="48" />
  <p><strong>Arckhé AI</strong></p>
</div>


[![Docker](https://img.shields.io/badge/Docker-Ready-2496ED?logo=docker&logoColor=white)](https://www.docker.com/)
[![Node.js](https://img.shields.io/badge/Node.js-22-339933?logo=nodedotjs&logoColor=white)](https://nodejs.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Security Hardened](https://img.shields.io/badge/Security-Hardened-green?logo=shieldsdotio)](SECURITY.md)
[![Docs](https://img.shields.io/badge/Docs-docs.openclaw.ai-blue)](https://docs.openclaw.ai)
[![Discord](https://img.shields.io/badge/Discord-Join-5865F2?logo=discord&logoColor=white)](https://discord.gg/clawd)

Setup Docker para o [OpenClaw](https://openclaw.ai) â€” seu assistente pessoal de IA. Qualquer SO. Qualquer plataforma. The lobster way. ðŸ¦ž

> **OpenClaw** Ã© um assistente de IA que roda na sua prÃ³pria mÃ¡quina. Ele se conecta a LLMs (Claude, GPT, Gemini, etc.), tem ferramentas (busca na web, execuÃ§Ã£o de cÃ³digo, controle de navegador, canvas, voice) e conversa com vocÃª via Telegram, WhatsApp, Discord, Slack, webchat e mais. Este repo te dÃ¡ um setup Docker pronto pra rodar com boas prÃ¡ticas de seguranÃ§a jÃ¡ configuradas.

---

## âœ¨ Funcionalidades

- ðŸ”’ **SeguranÃ§a reforÃ§ada** â€” segue o [Checklist Top 10 de SeguranÃ§a](SECURITY.md)
- ðŸ³ **Setup em um comando** â€” `docker compose up -d`
- ðŸ” **Secrets via variÃ¡veis de ambiente** â€” sem credenciais em texto puro nos arquivos de config
- ðŸ‘¤ **Container nÃ£o-root** â€” roda como usuÃ¡rio sem privilÃ©gios `openclaw`
- ðŸ“ **Logging habilitado** â€” trilha de auditoria por padrÃ£o
- ðŸ“± **Multi-canal** â€” Telegram, WhatsApp, Discord, Slack, Signal, iMessage, Google Chat, Teams, Matrix, webchat e mais
- ðŸŽ™ï¸ **Voice Wake + Talk Mode** â€” sempre ativo para fala (macOS/iOS/Android)
- ðŸŽ¨ **Live Canvas com A2UI** â€” workspaces visuais para o agente
- ðŸŒ **Browser Control** â€” automaÃ§Ã£o de navegador com CDP
- ðŸ› ï¸ **Skills Platform** â€” skills bundled, managed e customizados
- ðŸ§  **200+ modelos via OpenRouter** â€” Claude, GPT, Gemini, Llama, DeepSeek e mais com uma Ãºnica API key
- ðŸªŸ **CompatÃ­vel com Windows** â€” `.gitattributes` forÃ§a terminaÃ§Ãµes LF, Dockerfile corrige CRLF
- ðŸ”„ **Auto-restart** â€” polÃ­tica de reinÃ­cio `unless-stopped`
- ðŸŒ **Rede segura** â€” gateway vinculado ao loopback, isolamento de rede Docker disponÃ­vel

---

## ðŸ“‹ PrÃ©-requisitos

| Plataforma | Requisito | InstalaÃ§Ã£o |
|------------|-----------|------------|
| **Windows** | Docker Desktop | [docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop/) |
| **Windows** | Git | [git-scm.com](https://git-scm.com/download/win) |
| **Mac** | Docker Desktop | [docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop/) |
| **Linux** | Docker Engine + Compose V2 | Ver instruÃ§Ãµes abaixo |

---

## ðŸ³ InstalaÃ§Ã£o do Docker

### Windows

1. **Baixe o Docker Desktop:**
   - Acesse [docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop/)
   - Clique em "Download for Windows"

2. **Execute o instalador:**
   - Abra o arquivo `.exe` baixado
   - Aceite os termos e siga o wizard de instalaÃ§Ã£o
   - O instalador vai pedir para habilitar o **WSL 2** â€” aceite

3. **Reinicie o computador** (se solicitado)

4. **Inicie o Docker Desktop:**
   - Abra pelo menu Iniciar
   - Espere atÃ© aparecer "Docker is running" (Ã­cone ðŸ³ na bandeja do sistema)

5. **Verifique a instalaÃ§Ã£o:**
   ```powershell
   docker --version
   docker compose version
   ```

> âš ï¸ **WSL 2 nÃ£o instalado?** Se o Docker Desktop pedir para instalar o WSL 2, siga as instruÃ§Ãµes na tela. Isso Ã© necessÃ¡rio para rodar containers Linux no Windows.

> âš ï¸ **Erro "WSL docker-desktop Stopped"?** Abra o Docker Desktop pelo menu Iniciar â€” ele inicia o WSL automaticamente.

### Linux (Ubuntu/Debian)

O Docker Compose V2 jÃ¡ vem integrado ao Docker Engine (comando `docker compose`, sem hÃ­fen).

1. **Instale o Docker** (script oficial):
   ```bash
   curl -fsSL https://get.docker.com | sh
   ```

2. **Inicie o serviÃ§o:**
   ```bash
   sudo systemctl start docker
   ```

3. **Habilite no boot:**
   ```bash
   sudo systemctl enable docker
   ```

4. **Verifique se estÃ¡ rodando:**
   ```bash
   sudo systemctl status docker
   ```
   > Deve mostrar `Active: active (running)`. Pressione `q` para sair.

5. **Adicione seu usuÃ¡rio ao grupo docker** (para rodar sem `sudo`):
   ```bash
   sudo usermod -aG docker $USER
   ```

6. **FaÃ§a logout e login novamente** para aplicar a mudanÃ§a

7. **Verifique a instalaÃ§Ã£o:**
   ```bash
   docker --version
   docker compose version
   docker ps  # Deve mostrar lista vazia (sem erro)
   ```

### Mac

1. **Baixe o Docker Desktop:**
   - Acesse [docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop/)
   - Escolha a versÃ£o para seu chip (Intel ou Apple Silicon)

2. **Arraste para Applications** e abra o Docker Desktop

3. **Verifique a instalaÃ§Ã£o:**
   ```bash
   docker --version
   docker compose version
   ```

---

## ðŸš€ InÃ­cio RÃ¡pido

### Passo 1: Clone o repo

**Linux / Mac:**
```bash
git clone https://github.com/linnoff88-dev/docker-openclaw.git
cd docker-openclaw
```

**Windows (CMD):**
```cmd
git clone https://github.com/linnoff88-dev/docker-openclaw.git
cd docker-openclaw
```

**Windows (PowerShell):**
```powershell
git clone https://github.com/linnoff88-dev/docker-openclaw.git
cd docker-openclaw
```

### Passo 2: Configure o ambiente

**Linux / Mac:**
```bash
cp .env.example .env
nano .env  # Fill in your API keys
```

**Windows (CMD):**
```cmd
copy .env.example .env
notepad .env
```

**Windows (PowerShell):**
```powershell
Copy-Item .env.example .env
notepad .env
```

> âš ï¸ **IMPORTANTE:** VocÃª **PRECISA** criar E editar o arquivo `.env` antes de rodar `docker compose up`. O container nÃ£o vai funcionar com os valores de exemplo.

Abra o arquivo `.env` e substitua os valores de exemplo pelas suas chaves reais:

```env
# âŒ ERRADO â€” esses sÃ£o placeholders, nÃ£o vÃ£o funcionar:
OPENROUTER_API_KEY=sk-or-your-key-here
GATEWAY_AUTH_TOKEN=your-secure-token-here

# âœ… CERTO â€” suas chaves reais:
OPENROUTER_API_KEY=sk-or-v1-abc123-your-actual-real-key
GATEWAY_AUTH_TOKEN=a1b2c3d4e5f6a1b2c3d4e5f6a1b2c3d4e5f6a1b2c3d4e5f6
DEFAULT_MODEL=openrouter/anthropic/claude-sonnet-4.5
```

### Passo 3: Gere um token seguro para o gateway

O `GATEWAY_AUTH_TOKEN` protege a API do seu gateway contra acesso nÃ£o autorizado. Gere um aleatÃ³rio:

**Linux / Mac:**
```bash
openssl rand -hex 24
```

**Windows (PowerShell):**
```powershell
-join ((1..48) | ForEach-Object { '{0:x}' -f (Get-Random -Max 16) })
```

**Ou** use qualquer string aleatÃ³ria longa (pelo menos 24 caracteres). VocÃª pode usar um gerenciador de senhas para gerar uma.

Copie o token gerado para o seu arquivo `.env` como `GATEWAY_AUTH_TOKEN`.

### Passo 4: Configure sua chave OpenRouter

Este setup usa **OpenRouter** como gateway unificado de LLMs. Com uma Ãºnica API key, vocÃª tem acesso a 200+ modelos:

| Categoria | Modelos DisponÃ­veis |
|-----------|---------------------|
| **Claude** | Opus 4.5, Sonnet 4.5, Haiku 3.5, etc. |
| **GPT** | GPT-4o, GPT-4 Turbo, o1-preview, etc. |
| **Gemini** | Gemini 2.0 Flash (FREE), Pro, etc. |
| **Open Source** | Qwen3 Coder 480B (FREE) â­, Llama 3.3 70B (FREE), etc. |

**Obtenha sua chave:**
1. Acesse [openrouter.ai](https://openrouter.ai/)
2. FaÃ§a login com Google/GitHub
3. VÃ¡ para [Keys](https://openrouter.ai/keys) e crie uma nova API key
4. Copie a key (comeÃ§a com `sk-or-v1-...`)
5. Cole no seu `.env` como `OPENROUTER_API_KEY`

**Escolha seu modelo padrÃ£o:**

Edite `DEFAULT_MODEL` no `.env` para escolher qual modelo usar.

âš ï¸ **IMPORTANTE:** O formato correto Ã© `openrouter/<provider>/<model>` (com o prefixo `openrouter/`)

```env
# OpÃ§Ã£o 1: Claude Sonnet 4.5 (melhor qualidade, recomendado) â­
DEFAULT_MODEL=openrouter/anthropic/claude-sonnet-4.5

# OpÃ§Ã£o 2: Claude Opus 4.5 (mÃ¡ximo poder)
DEFAULT_MODEL=openrouter/anthropic/claude-opus-4-5

# OpÃ§Ã£o 3: GPT-4o (excelente para cÃ³digo)
DEFAULT_MODEL=openrouter/openai/gpt-4o

# OpÃ§Ã£o 4: Qwen3 Coder 480B (GRÃTIS, melhor para cÃ³digo) ðŸ†“ â­
DEFAULT_MODEL=openrouter/qwen/qwen3-coder:free

# OpÃ§Ã£o 5: Llama 3.3 70B (GRÃTIS, open source) ðŸ†“
DEFAULT_MODEL=openrouter/meta-llama/llama-3.3-70b-instruct:free

# OpÃ§Ã£o 6: DeepSeek R1 (GRÃTIS, raciocÃ­nio avanÃ§ado) ðŸ†“
# âš ï¸ NOTA: DeepSeek R1 usa tags <think> que podem causar problemas
DEFAULT_MODEL=openrouter/deepseek/deepseek-r1
```

> âš ï¸ **ATENÃ‡ÃƒO:** NÃƒO esqueÃ§a do prefixo `openrouter/` no inÃ­cio! Sem ele o modelo nÃ£o serÃ¡ reconhecido.

> ðŸ’¡ **Dica:** VocÃª pode trocar de modelo a qualquer momento editando o `.env` e executando:
> ```bash
> docker compose down -v && docker compose up -d
> ```

> ðŸ’° **Modelos GrÃ¡tis:** Qwen3 Coder 480B, Llama 3.3 70B e DeepSeek R1 sÃ£o totalmente gratuitos no OpenRouter. Perfeito para testar!

> ðŸ“‹ **Modelos Testados:** Veja [MODELOS-TESTADOS.md](MODELOS-TESTADOS.md) para documentaÃ§Ã£o completa de modelos testados, problemas encontrados e recomendaÃ§Ãµes.

> ðŸ“Š **PreÃ§os e limites:** Consulte [openrouter.ai/models](https://openrouter.ai/models) para ver preÃ§os, limites de contexto e velocidade de cada modelo.

### Passo 5: Build e execuÃ§Ã£o

```bash
docker compose up -d
```

> ðŸ’¡ **Primeira execuÃ§Ã£o** leva alguns minutos para buildar a imagem (baixa Node.js, FFmpeg, Python, etc). As execuÃ§Ãµes seguintes iniciam instantaneamente.

> âš ï¸ **Erro no Windows `open //./pipe/dockerDesktopLinuxEngine`?** O Docker Desktop nÃ£o estÃ¡ rodando. Abra-o pelo menu Iniciar e espere atÃ© mostrar "Docker is running", depois tente novamente.

> âœ¨ **ConfiguraÃ§Ã£o automÃ¡tica:** O script `entrypoint.sh` detecta automaticamente qual provedor de LLM vocÃª configurou no `.env` e cria a configuraÃ§Ã£o ideal. VocÃª **nÃ£o precisa** editar arquivos JSON manualmente!

### Passo 6: Acesse o Webchat

Abra no seu navegador:
```
http://localhost:18789/chat
```

Quando solicitado, digite seu `GATEWAY_AUTH_TOKEN` do arquivo `.env` para autenticar.

> ðŸ’¡ **Dica:** VocÃª tambÃ©m pode acessar diretamente com: `http://localhost:18789/?token=SEU_TOKEN`

### Passo 7: Verifique o status

```bash
# Acompanhe os logs (Ctrl+C para parar)
docker compose logs -f

# Ou veja sÃ³ as Ãºltimas 50 linhas
docker compose logs --tail 50
```

VocÃª deve ver uma saÃ­da como:
```
ðŸ¦ž First run â€” creating config from template...
ðŸ”‘ Setting gateway auth token...
ðŸ“± Enabling Telegram...
ðŸŒ Setting gateway bind to lan (required for Docker port mapping)...
ðŸ“ Configuring logging...
ðŸ¦ž Starting OpenClaw...
```

### Passo 8: ConfiguraÃ§Ã£o pÃ³s-instalaÃ§Ã£o

Depois que o container estiver rodando, use esses comandos para ajustar seu setup:

```bash
# Auto-detecte e corrija problemas de config
docker exec openclaw openclaw doctor

# Verifique a saÃºde geral
docker exec openclaw openclaw gateway --verbose

# Atualize para a versÃ£o mais recente
docker exec openclaw openclaw update --channel stable
```

| Comando | O que faz |
|---------|-----------|
| `openclaw doctor` | Auto-detecta e mostra problemas de config |
| `openclaw update --channel stable` | Atualiza para a versÃ£o estÃ¡vel mais recente |
| `openclaw gateway --verbose` | Inicia gateway com logs detalhados |

---

## ðŸ’¬ Comandos de Chat

Dentro das conversas (grupo ou DM), vocÃª pode usar estes comandos:

| Comando | DescriÃ§Ã£o |
|---------|-----------|
| `/status` | Status da sessÃ£o (modelo, tokens, custo) |
| `/new` ou `/reset` | Resetar sessÃ£o |
| `/compact` | Comprimir contexto |
| `/think <level>` | Controle de thinking (off/minimal/low/medium/high/xhigh) |
| `/verbose on\|off` | Toggle de verbosidade |
| `/usage off\|tokens\|full` | RelatÃ³rio de uso |
| `/restart` | Reiniciar gateway (owner-only em grupos) |
| `/activation mention\|always` | Toggle de ativaÃ§Ã£o em grupos |

---

## ðŸ“± ConfiguraÃ§Ã£o do Telegram

O Telegram Ã© a forma mais fÃ¡cil de falar com seu OpenClaw de qualquer lugar.

### Passo a passo:

1. **Crie um bot** â€” Abra o Telegram e mande mensagem pro [@BotFather](https://t.me/BotFather)
2. **Envie `/newbot`** â€” Siga as instruÃ§Ãµes para nomear seu bot
3. **Copie o token** â€” O BotFather te dÃ¡ um token tipo `123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew11`
4. **Adicione ao `.env`:**
   ```env
   TELEGRAM_BOT_TOKEN=123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew11
   ```
5. **Reinicie o container:**
   ```bash
   docker compose restart
   ```
6. **Mande mensagem pro seu bot** no Telegram â€” ele vai te dar um **cÃ³digo de pareamento**
7. **Aprove o pareamento** dentro do container:
   ```bash
   docker exec openclaw openclaw pairing approve telegram <code>
   ```

> ðŸ’¡ O sistema de pareamento garante que sÃ³ usuÃ¡rios aprovados possam falar com seu bot. Ã‰ uma funcionalidade de seguranÃ§a â€” sem aprovaÃ§Ã£o, o bot nÃ£o responde a estranhos.

---

## ðŸ“² ConfiguraÃ§Ã£o do WhatsApp

VocÃª pode conectar o OpenClaw ao WhatsApp via pareamento por QR code.

### Passo a passo:

1. **Execute o comando de login:**
   ```bash
   docker exec -it openclaw openclaw channels login whatsapp
   ```
2. **Escaneie o QR code** com seu WhatsApp (ConfiguraÃ§Ãµes â†’ Aparelhos Conectados â†’ Conectar um Aparelho)
3. **Pronto!** Seu OpenClaw agora estÃ¡ conectado ao WhatsApp

### âš ï¸ NÃºmero Pessoal vs. NÃºmero Dedicado

**Usando seu nÃºmero pessoal:**
- O bot vai ver mensagens de todos os seus contatos
- Por padrÃ£o, a polÃ­tica de DM Ã© `pairing` â€” outros podem receber um prompt de pareamento
- **Recomendado:** Defina `dmPolicy: allowlist` com apenas o seu nÃºmero

**Usando um nÃºmero dedicado (recomendado):**
- Pegue um chip prÃ©-pago barato ou um nÃºmero do Google Voice
- SeparaÃ§Ã£o mais limpa entre mensagens pessoais e do bot

---

## ðŸ’œ ConfiguraÃ§Ã£o do Discord

1. **Crie um bot no Discord Developer Portal:**
   - Acesse [discord.com/developers/applications](https://discord.com/developers/applications)
   - Crie uma nova aplicaÃ§Ã£o
   - VÃ¡ em "Bot" â†’ "Add Bot"
   - Copie o token

2. **Adicione ao `.env`:**
   ```env
   DISCORD_BOT_TOKEN=your-discord-token-here
   ```

3. **Reinicie o container:**
   ```bash
   docker compose restart
   ```

---

## ðŸ’¼ ConfiguraÃ§Ã£o do Slack

1. **Crie um Slack App:**
   - Acesse [api.slack.com/apps](https://api.slack.com/apps)
   - Crie um novo app
   - Adicione os scopes necessÃ¡rios (chat:write, etc.)
   - Instale no seu workspace
   - Copie o Bot Token (`xoxb-...`) e App Token (`xapp-...`)

2. **Adicione ao `.env`:**
   ```env
   SLACK_BOT_TOKEN=xoxb-your-bot-token
   SLACK_APP_TOKEN=xapp-your-app-token
   ```

3. **Reinicie o container:**
   ```bash
   docker compose restart
   ```

---

## ðŸ”’ SeguranÃ§a

Este setup Docker implementa **7 de 10** medidas de hardening de seguranÃ§a automaticamente. Veja o [SECURITY.md](SECURITY.md) para o checklist completo.

### O que o Docker faz automaticamente:
| ProteÃ§Ã£o | Status |
|----------|--------|
| Gateway vinculado apenas ao `127.0.0.1` (lado do host) | âœ… AutomÃ¡tico |
| PolÃ­tica de DM requer aprovaÃ§Ã£o de pareamento | âœ… AutomÃ¡tico |
| Arquivos de config com `chmod 600` | âœ… AutomÃ¡tico |
| Container roda como usuÃ¡rio nÃ£o-root | âœ… AutomÃ¡tico |
| Sem escalaÃ§Ã£o de privilÃ©gios (`no-new-privileges`) | âœ… AutomÃ¡tico |
| Logging e diagnÃ³sticos habilitados | âœ… AutomÃ¡tico |
| Secrets via variÃ¡veis de ambiente | âœ… AutomÃ¡tico |

### Auditoria de seguranÃ§a:
```bash
docker exec openclaw openclaw doctor
```

---

## ðŸ“¦ Volumes

Volumes Docker persistem seus dados entre reinÃ­cios e rebuilds do container.

| Volume | Caminho no Container | Finalidade |
|--------|---------------------|------------|
| `openclaw-data` | `/home/openclaw/.openclaw` | Config, dados de sessÃ£o, tokens de auth, info de pareamento |
| `openclaw-workspace` | `/home/openclaw/workspace` | Workspace do agente â€” AGENTS.md, SOUL.md, skills, arquivos de projeto |
| `openclaw-logs` | `/home/openclaw/logs` | Arquivos de log (NÃƒO em /tmp â€” sobrevive a reinÃ­cios) |

### FaÃ§a backup dos seus dados:
```bash
# Backup de todos os volumes
docker run --rm -v openclaw-data:/data -v $(pwd):/backup alpine tar czf /backup/openclaw-data.tar.gz -C /data .
docker run --rm -v openclaw-workspace:/data -v $(pwd):/backup alpine tar czf /backup/openclaw-workspace.tar.gz -C /data .
```

### Resetar tudo:
```bash
docker compose down -v  # âš ï¸ Apaga TODOS os dados incluindo config e workspace
```

---

## ðŸ› ï¸ Comandos Ãšteis

```bash
# === Ciclo de vida ===
docker compose up -d              # Start in background
docker compose down               # Stop and remove container
docker compose restart            # Restart
docker compose stop               # Stop without removing

# === Logs ===
docker compose logs -f            # Follow logs (Ctrl+C to stop)
docker compose logs --tail 100    # Last 100 lines

# === Acesso ao shell ===
docker compose exec openclaw bash  # Open shell inside container

# === OpenClaw CLI ===
docker exec openclaw openclaw doctor            # Check for issues
docker exec openclaw openclaw update --channel stable  # Update to latest

# === Atualizar OpenClaw ===
docker compose build --no-cache   # Rebuild image (pulls latest openclaw)
docker compose up -d              # Restart with new image

# === Limpeza ===
docker system prune -a            # Remove unused images (reclaim disk space)
```

---

## ðŸ–¥ï¸ Acesso ao Webchat (Remoto)

O gateway Ã© vinculado ao `127.0.0.1` (apenas loopback). Para acessar o webchat de outra mÃ¡quina, use um **tÃºnel SSH**:

```bash
# Na sua mÃ¡quina local (a que tem o navegador):
ssh -L 18789:localhost:18789 user@your-server-ip

# Depois abra no navegador:
# http://127.0.0.1:18789/chat
```

Esta Ã© a forma mais segura de acessar a interface web remotamente â€” sem portas expostas, todo trÃ¡fego criptografado via SSH.

### Alternativa: Tailscale (recomendado para uso frequente)

O OpenClaw tem suporte nativo a Tailscale. Configure `gateway.tailscale.mode`:

- `off` â€” sem automaÃ§Ã£o (padrÃ£o)
- `serve` â€” HTTPS apenas na tailnet
- `funnel` â€” HTTPS pÃºblico (requer autenticaÃ§Ã£o por senha)

```bash
# No seu servidor:
curl -fsSL https://tailscale.com/install.sh | sh
sudo tailscale up

# Acesse o webchat via: http://<tailscale-ip>:18789/chat
```

---

## ðŸ”§ SoluÃ§Ã£o de Problemas

### Problemas no Windows

| Erro | Causa | SoluÃ§Ã£o |
|------|-------|---------|
| `open //./pipe/dockerDesktopLinuxEngine: O sistema nÃ£o pode encontrar o arquivo` | Docker Desktop nÃ£o estÃ¡ rodando | Abra o Docker Desktop pelo menu Iniciar, espere por "Docker is running" |
| `.env not found` | Arquivo de config faltando | Execute `copy .env.example .env` e depois `notepad .env` |
| `WSL docker-desktop Stopped` | WSL nÃ£o iniciou | Abra o Docker Desktop â€” ele inicia o WSL automaticamente |
| Build trava ou falha | RAM insuficiente | Docker Desktop â†’ Settings â†’ Resources â†’ aumente para 4GB+ |
| `exec entrypoint.sh: no such file or directory` | TerminaÃ§Ãµes de linha CRLF do Windows | Clone o repo novamente: `git config --global core.autocrlf input` e depois `git clone` |

### Problemas no Linux / Mac

| Erro | Causa | SoluÃ§Ã£o |
|------|-------|---------|
| `permission denied` | NÃ£o estÃ¡ no grupo docker | `sudo usermod -aG docker $USER` e depois **faÃ§a logout e login novamente** |
| `port already in use` | Outro serviÃ§o na porta 18789 | Mude a porta no `docker-compose.yml` ou pare o outro serviÃ§o |
| `no space left on device` | Disco cheio | `docker system prune -a` para limpar imagens antigas |

### Problemas de TÃºnel SSH / Acesso Remoto

Se vocÃª nÃ£o consegue acessar o webchat localmente na sua mÃ¡quina apÃ³s criar um tÃºnel SSH, siga estes passos:

**1. Remova a chave SSH antiga (se o IP do servidor mudou):**
```bash
ssh-keygen -R seu-servidor-ip
```

**2. Teste a conexÃ£o SSH:**
```bash
ssh -o StrictHostKeyChecking=accept-new -o BatchMode=yes usuario@seu-servidor-ip "echo 'ConexÃ£o SSH OK!' && hostname"
```

> ðŸ’¡ Se falhar, adicione sua chave pÃºblica ao `~/.ssh/authorized_keys` do servidor.

**3. Crie o tÃºnel SSH:**
```bash
# TÃºnel em foreground (fecha quando vocÃª sair do terminal)
ssh -L 18789:127.0.0.1:18789 usuario@seu-servidor-ip

# TÃºnel em background (roda silenciosamente)
ssh -f -N -L 18789:127.0.0.1:18789 usuario@seu-servidor-ip
```

**4. Acesse o webchat:**
```
http://127.0.0.1:18789/chat
```

| Problema | Causa | SoluÃ§Ã£o |
|----------|-------|---------|
| `WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED` | IP do servidor mudou ou reinstalou | `ssh-keygen -R seu-servidor-ip` e reconecte |
| `Permission denied (publickey)` | Chave SSH nÃ£o configurada | Adicione sua chave pÃºblica ao servidor: `ssh-copy-id usuario@servidor` |
| `Connection refused` na porta 18789 | TÃºnel nÃ£o criado ou container parado | Verifique se o tÃºnel estÃ¡ ativo e se o container estÃ¡ rodando |
| `bind: Address already in use` | Porta local jÃ¡ em uso | Use outra porta: `ssh -L 18790:127.0.0.1:18789 ...` e acesse via `http://127.0.0.1:18790/chat` |

### Problemas de ConfiguraÃ§Ã£o

| Problema | Causa | SoluÃ§Ã£o |
|----------|-------|---------|
| **"Unknown model: anthropic/claude-sonnet-4.5"** | Falta o prefixo `openrouter/` | Use `openrouter/anthropic/claude-sonnet-4.5` (sempre inclua o prefixo `openrouter/`) |
| **Bot nÃ£o responde apÃ³s mudar o modelo** | Config corrompida ou modelo invÃ¡lido | Execute `docker compose down -v` (âš ï¸ apaga dados), depois `docker compose up -d` para comeÃ§ar do zero |
| **MudanÃ§as no .env nÃ£o aplicadas** | `docker compose restart` nÃ£o recarrega variÃ¡veis de ambiente | Use `docker compose down && docker compose up -d` para recarregar o `.env` |

---

## ðŸ”„ MigraÃ§Ã£o do Moltbot/Clawdbot

Se vocÃª estÃ¡ vindo do setup antigo `docker-moltbot` ou `docker-clawdbot`, aqui estÃ¡ o que mudou:

### O que Ã© diferente:

| Antigo (Moltbot/Clawdbot) | Novo (OpenClaw) |
|---------------------------|-----------------|
| Pacote: `clawdbot` / `moltbot` | Pacote: `openclaw` |
| CLI: `clawdbot` / `moltbot` | CLI: `openclaw` |
| Dir de config: `~/.clawdbot` / `~/.moltbot` | Dir de config: `~/.openclaw` |
| Docs: `docs.molt.bot` | Docs: `docs.openclaw.ai` |
| Container: `moltbot` | Container: `openclaw` |

### Passos da migraÃ§Ã£o:

1. **FaÃ§a backup dos seus dados:**
   ```bash
   # Do setup antigo
   cd docker-moltbot
   docker run --rm -v moltbot-data:/data -v $(pwd):/backup alpine tar czf /backup/moltbot-data-backup.tar.gz -C /data .
   ```

2. **Pare o container antigo:**
   ```bash
   docker compose down
   ```

3. **Clone o novo repo:**
   ```bash
   git clone https://github.com/linnoff88-dev/docker-openclaw.git
   cd docker-openclaw
   ```

4. **Copie seu .env:**
   ```bash
   cp ../docker-moltbot/.env .env
   ```

5. **Inicie o novo container:**
   ```bash
   docker compose up -d
   ```

---

## ðŸ’» Requisitos

| Recurso | MÃ­nimo | Recomendado |
|---------|--------|-------------|
| **RAM** | 2 GB | 4 GB (com Whisper) |
| **Disco** | 5 GB | 10+ GB |
| **CPU** | 1 core | 2+ cores |
| **Docker** | Engine 24+ / Compose v2+ | Ãšltima versÃ£o estÃ¡vel |
| **SO** | Linux, macOS, Windows 10+ | Ubuntu 22.04+ / macOS 13+ |
| **Rede** | Acesso Ã  internet | Banda larga estÃ¡vel |

---

## ðŸ¤ Contribuindo

PRs sÃ£o bem-vindos! Siga o checklist de seguranÃ§a em [SECURITY.md](SECURITY.md).

1. FaÃ§a fork do repo
2. Crie uma branch de feature: `git checkout -b my-feature`
3. FaÃ§a commit das suas mudanÃ§as: `git commit -m 'Add my feature'`
4. FaÃ§a push: `git push origin my-feature`
5. Abra um Pull Request

---

## ðŸ“œ LicenÃ§a

[MIT](LICENSE) â€” use como quiser.

---

<p align="center">
  <a href="https://openclaw.ai">openclaw.ai</a> â€¢
  <a href="https://docs.openclaw.ai">DocumentaÃ§Ã£o</a> â€¢
  <a href="https://discord.gg/clawd">Discord</a> â€¢
  <a href="https://github.com/openclaw/openclaw">GitHub</a>
</p>

---

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="32" />
  <p><strong>Arckhé AI</strong></p>
</div>