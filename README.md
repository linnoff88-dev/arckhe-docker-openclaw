<p align="center">
  <img src="assets/openclaw-banner.png" alt="OpenClaw - Personal AI Assistant" width="100%">
</p>

# ê°Å¸Â¦Å¾ Docker OpenClaw

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

Setup Docker para o [OpenClaw](https://openclaw.ai) ê¢â¬â seu assistente pessoal de IA. Qualquer SO. Qualquer plataforma. The lobster way. ê°Å¸Â¦Å¾

> **OpenClaw** êÂ© um assistente de IA que roda na sua prêÂ³pria mêÂ¡quina. Ele se conecta a LLMs (Claude, GPT, Gemini, etc.), tem ferramentas (busca na web, execuêÂ§êÂ£o de cêÂ³digo, controle de navegador, canvas, voice) e conversa com vocêÂª via Telegram, WhatsApp, Discord, Slack, webchat e mais. Este repo te dêÂ¡ um setup Docker pronto pra rodar com boas prêÂ¡ticas de seguranêÂ§a jêÂ¡ configuradas.

---

## ê¢ÅÂ¨ Funcionalidades

- ê°Å¸ââ **SeguranêÂ§a reforêÂ§ada** ê¢â¬â segue o [Checklist Top 10 de SeguranêÂ§a](SECURITY.md)
- ê°Å¸ÂÂ³ **Setup em um comando** ê¢â¬â `docker compose up -d`
- ê°Å¸âÂ **Secrets via variêÂ¡veis de ambiente** ê¢â¬â sem credenciais em texto puro nos arquivos de config
- ê°Å¸âÂ¤ **Container nêÂ£o-root** ê¢â¬â roda como usuêÂ¡rio sem privilêÂ©gios `openclaw`
- ê°Å¸âÂ **Logging habilitado** ê¢â¬â trilha de auditoria por padrêÂ£o
- ê°Å¸âÂ± **Multi-canal** ê¢â¬â Telegram, WhatsApp, Discord, Slack, Signal, iMessage, Google Chat, Teams, Matrix, webchat e mais
- ê°Å¸Å½â¢ê¯Â¸Â **Voice Wake + Talk Mode** ê¢â¬â sempre ativo para fala (macOS/iOS/Android)
- ê°Å¸Å½Â¨ **Live Canvas com A2UI** ê¢â¬â workspaces visuais para o agente
- ê°Å¸ÅÂ **Browser Control** ê¢â¬â automaêÂ§êÂ£o de navegador com CDP
- ê°Å¸âºÂ ê¯Â¸Â **Skills Platform** ê¢â¬â skills bundled, managed e customizados
- ê°Å¸Â§Â  **200+ modelos via OpenRouter** ê¢â¬â Claude, GPT, Gemini, Llama, DeepSeek e mais com uma êÂºnica API key
- ê°Å¸ÂªÅ¸ **CompatêÂ­vel com Windows** ê¢â¬â `.gitattributes` forêÂ§a terminaêÂ§êÂµes LF, Dockerfile corrige CRLF
- ê°Å¸ââ **Auto-restart** ê¢â¬â polêÂ­tica de reinêÂ­cio `unless-stopped`
- ê°Å¸ÅÂ **Rede segura** ê¢â¬â gateway vinculado ao loopback, isolamento de rede Docker disponêÂ­vel

---

## ê°Å¸ââ¹ PrêÂ©-requisitos

| Plataforma | Requisito | InstalaêÂ§êÂ£o |
|------------|-----------|------------|
| **Windows** | Docker Desktop | [docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop/) |
| **Windows** | Git | [git-scm.com](https://git-scm.com/download/win) |
| **Mac** | Docker Desktop | [docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop/) |
| **Linux** | Docker Engine + Compose V2 | Ver instruêÂ§êÂµes abaixo |

---

## ê°Å¸ÂÂ³ InstalaêÂ§êÂ£o do Docker

### Windows

1. **Baixe o Docker Desktop:**
   - Acesse [docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop/)
   - Clique em "Download for Windows"

2. **Execute o instalador:**
   - Abra o arquivo `.exe` baixado
   - Aceite os termos e siga o wizard de instalaêÂ§êÂ£o
   - O instalador vai pedir para habilitar o **WSL 2** ê¢â¬â aceite

3. **Reinicie o computador** (se solicitado)

4. **Inicie o Docker Desktop:**
   - Abra pelo menu Iniciar
   - Espere atêÂ© aparecer "Docker is running" (êÂ­cone ê°Å¸ÂÂ³ na bandeja do sistema)

5. **Verifique a instalaêÂ§êÂ£o:**
   ```powershell
   docker --version
   docker compose version
   ```

> ê¢Å¡Â ê¯Â¸Â **WSL 2 nêÂ£o instalado?** Se o Docker Desktop pedir para instalar o WSL 2, siga as instruêÂ§êÂµes na tela. Isso êÂ© necessêÂ¡rio para rodar containers Linux no Windows.

> ê¢Å¡Â ê¯Â¸Â **Erro "WSL docker-desktop Stopped"?** Abra o Docker Desktop pelo menu Iniciar ê¢â¬â ele inicia o WSL automaticamente.

### Linux (Ubuntu/Debian)

O Docker Compose V2 jêÂ¡ vem integrado ao Docker Engine (comando `docker compose`, sem hêÂ­fen).

1. **Instale o Docker** (script oficial):
   ```bash
   curl -fsSL https://get.docker.com | sh
   ```

2. **Inicie o serviêÂ§o:**
   ```bash
   sudo systemctl start docker
   ```

3. **Habilite no boot:**
   ```bash
   sudo systemctl enable docker
   ```

4. **Verifique se estêÂ¡ rodando:**
   ```bash
   sudo systemctl status docker
   ```
   > Deve mostrar `Active: active (running)`. Pressione `q` para sair.

5. **Adicione seu usuêÂ¡rio ao grupo docker** (para rodar sem `sudo`):
   ```bash
   sudo usermod -aG docker $USER
   ```

6. **FaêÂ§a logout e login novamente** para aplicar a mudanêÂ§a

7. **Verifique a instalaêÂ§êÂ£o:**
   ```bash
   docker --version
   docker compose version
   docker ps  # Deve mostrar lista vazia (sem erro)
   ```

### Mac

1. **Baixe o Docker Desktop:**
   - Acesse [docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop/)
   - Escolha a versêÂ£o para seu chip (Intel ou Apple Silicon)

2. **Arraste para Applications** e abra o Docker Desktop

3. **Verifique a instalaêÂ§êÂ£o:**
   ```bash
   docker --version
   docker compose version
   ```

---

## ê°Å¸Å¡â¬ InêÂ­cio RêÂ¡pido

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

> ê¢Å¡Â ê¯Â¸Â **IMPORTANTE:** VocêÂª **PRECISA** criar E editar o arquivo `.env` antes de rodar `docker compose up`. O container nêÂ£o vai funcionar com os valores de exemplo.

Abra o arquivo `.env` e substitua os valores de exemplo pelas suas chaves reais:

```env
# ê¢ÂÅ ERRADO ê¢â¬â esses sêÂ£o placeholders, nêÂ£o vêÂ£o funcionar:
OPENROUTER_API_KEY=sk-or-your-key-here
GATEWAY_AUTH_TOKEN=your-secure-token-here

# ê¢Åâ¦ CERTO ê¢â¬â suas chaves reais:
OPENROUTER_API_KEY=sk-or-v1-abc123-your-actual-real-key
GATEWAY_AUTH_TOKEN=a1b2c3d4e5f6a1b2c3d4e5f6a1b2c3d4e5f6a1b2c3d4e5f6
DEFAULT_MODEL=openrouter/anthropic/claude-sonnet-4.5
```

### Passo 3: Gere um token seguro para o gateway

O `GATEWAY_AUTH_TOKEN` protege a API do seu gateway contra acesso nêÂ£o autorizado. Gere um aleatêÂ³rio:

**Linux / Mac:**
```bash
openssl rand -hex 24
```

**Windows (PowerShell):**
```powershell
-join ((1..48) | ForEach-Object { '{0:x}' -f (Get-Random -Max 16) })
```

**Ou** use qualquer string aleatêÂ³ria longa (pelo menos 24 caracteres). VocêÂª pode usar um gerenciador de senhas para gerar uma.

Copie o token gerado para o seu arquivo `.env` como `GATEWAY_AUTH_TOKEN`.

### Passo 4: Configure sua chave OpenRouter

Este setup usa **OpenRouter** como gateway unificado de LLMs. Com uma êÂºnica API key, vocêÂª tem acesso a 200+ modelos:

| Categoria | Modelos DisponêÂ­veis |
|-----------|---------------------|
| **Claude** | Opus 4.5, Sonnet 4.5, Haiku 3.5, etc. |
| **GPT** | GPT-4o, GPT-4 Turbo, o1-preview, etc. |
| **Gemini** | Gemini 2.0 Flash (FREE), Pro, etc. |
| **Open Source** | Qwen3 Coder 480B (FREE) ê¢Â­Â, Llama 3.3 70B (FREE), etc. |

**Obtenha sua chave:**
1. Acesse [openrouter.ai](https://openrouter.ai/)
2. FaêÂ§a login com Google/GitHub
3. VêÂ¡ para [Keys](https://openrouter.ai/keys) e crie uma nova API key
4. Copie a key (comeêÂ§a com `sk-or-v1-...`)
5. Cole no seu `.env` como `OPENROUTER_API_KEY`

**Escolha seu modelo padrêÂ£o:**

Edite `DEFAULT_MODEL` no `.env` para escolher qual modelo usar.

ê¢Å¡Â ê¯Â¸Â **IMPORTANTE:** O formato correto êÂ© `openrouter/<provider>/<model>` (com o prefixo `openrouter/`)

```env
# OpêÂ§êÂ£o 1: Claude Sonnet 4.5 (melhor qualidade, recomendado) ê¢Â­Â
DEFAULT_MODEL=openrouter/anthropic/claude-sonnet-4.5

# OpêÂ§êÂ£o 2: Claude Opus 4.5 (mêÂ¡ximo poder)
DEFAULT_MODEL=openrouter/anthropic/claude-opus-4-5

# OpêÂ§êÂ£o 3: GPT-4o (excelente para cêÂ³digo)
DEFAULT_MODEL=openrouter/openai/gpt-4o

# OpêÂ§êÂ£o 4: Qwen3 Coder 480B (GRêÂTIS, melhor para cêÂ³digo) ê°Å¸â â ê¢Â­Â
DEFAULT_MODEL=openrouter/qwen/qwen3-coder:free

# OpêÂ§êÂ£o 5: Llama 3.3 70B (GRêÂTIS, open source) ê°Å¸â â
DEFAULT_MODEL=openrouter/meta-llama/llama-3.3-70b-instruct:free

# OpêÂ§êÂ£o 6: DeepSeek R1 (GRêÂTIS, raciocêÂ­nio avanêÂ§ado) ê°Å¸â â
# ê¢Å¡Â ê¯Â¸Â NOTA: DeepSeek R1 usa tags <think> que podem causar problemas
DEFAULT_MODEL=openrouter/deepseek/deepseek-r1
```

> ê¢Å¡Â ê¯Â¸Â **ATENêâ¡êÆO:** NêÆO esqueêÂ§a do prefixo `openrouter/` no inêÂ­cio! Sem ele o modelo nêÂ£o serêÂ¡ reconhecido.

> ê°Å¸âÂ¡ **Dica:** VocêÂª pode trocar de modelo a qualquer momento editando o `.env` e executando:
> ```bash
> docker compose down -v && docker compose up -d
> ```

> ê°Å¸âÂ° **Modelos GrêÂ¡tis:** Qwen3 Coder 480B, Llama 3.3 70B e DeepSeek R1 sêÂ£o totalmente gratuitos no OpenRouter. Perfeito para testar!

> ê°Å¸ââ¹ **Modelos Testados:** Veja [MODELOS-TESTADOS.md](MODELOS-TESTADOS.md) para documentaêÂ§êÂ£o completa de modelos testados, problemas encontrados e recomendaêÂ§êÂµes.

> ê°Å¸âÅ  **PreêÂ§os e limites:** Consulte [openrouter.ai/models](https://openrouter.ai/models) para ver preêÂ§os, limites de contexto e velocidade de cada modelo.

### Passo 5: Build e execuêÂ§êÂ£o

```bash
docker compose up -d
```

> ê°Å¸âÂ¡ **Primeira execuêÂ§êÂ£o** leva alguns minutos para buildar a imagem (baixa Node.js, FFmpeg, Python, etc). As execuêÂ§êÂµes seguintes iniciam instantaneamente.

> ê¢Å¡Â ê¯Â¸Â **Erro no Windows `open //./pipe/dockerDesktopLinuxEngine`?** O Docker Desktop nêÂ£o estêÂ¡ rodando. Abra-o pelo menu Iniciar e espere atêÂ© mostrar "Docker is running", depois tente novamente.

> ê¢ÅÂ¨ **ConfiguraêÂ§êÂ£o automêÂ¡tica:** O script `entrypoint.sh` detecta automaticamente qual provedor de LLM vocêÂª configurou no `.env` e cria a configuraêÂ§êÂ£o ideal. VocêÂª **nêÂ£o precisa** editar arquivos JSON manualmente!

### Passo 6: Acesse o Webchat

Abra no seu navegador:
```
http://localhost:18789/chat
```

Quando solicitado, digite seu `GATEWAY_AUTH_TOKEN` do arquivo `.env` para autenticar.

> ê°Å¸âÂ¡ **Dica:** VocêÂª tambêÂ©m pode acessar diretamente com: `http://localhost:18789/?token=SEU_TOKEN`

### Passo 7: Verifique o status

```bash
# Acompanhe os logs (Ctrl+C para parar)
docker compose logs -f

# Ou veja sêÂ³ as êÂºltimas 50 linhas
docker compose logs --tail 50
```

VocêÂª deve ver uma saêÂ­da como:
```
ê°Å¸Â¦Å¾ First run ê¢â¬â creating config from template...
ê°Å¸ââ Setting gateway auth token...
ê°Å¸âÂ± Enabling Telegram...
ê°Å¸ÅÂ Setting gateway bind to lan (required for Docker port mapping)...
ê°Å¸âÂ Configuring logging...
ê°Å¸Â¦Å¾ Starting OpenClaw...
```

### Passo 8: ConfiguraêÂ§êÂ£o pêÂ³s-instalaêÂ§êÂ£o

Depois que o container estiver rodando, use esses comandos para ajustar seu setup:

```bash
# Auto-detecte e corrija problemas de config
docker exec openclaw openclaw doctor

# Verifique a saêÂºde geral
docker exec openclaw openclaw gateway --verbose

# Atualize para a versêÂ£o mais recente
docker exec openclaw openclaw update --channel stable
```

| Comando | O que faz |
|---------|-----------|
| `openclaw doctor` | Auto-detecta e mostra problemas de config |
| `openclaw update --channel stable` | Atualiza para a versêÂ£o estêÂ¡vel mais recente |
| `openclaw gateway --verbose` | Inicia gateway com logs detalhados |

---

## ê°Å¸âÂ¬ Comandos de Chat

Dentro das conversas (grupo ou DM), vocêÂª pode usar estes comandos:

| Comando | DescriêÂ§êÂ£o |
|---------|-----------|
| `/status` | Status da sessêÂ£o (modelo, tokens, custo) |
| `/new` ou `/reset` | Resetar sessêÂ£o |
| `/compact` | Comprimir contexto |
| `/think <level>` | Controle de thinking (off/minimal/low/medium/high/xhigh) |
| `/verbose on\|off` | Toggle de verbosidade |
| `/usage off\|tokens\|full` | RelatêÂ³rio de uso |
| `/restart` | Reiniciar gateway (owner-only em grupos) |
| `/activation mention\|always` | Toggle de ativaêÂ§êÂ£o em grupos |

---

## ê°Å¸âÂ± ConfiguraêÂ§êÂ£o do Telegram

O Telegram êÂ© a forma mais fêÂ¡cil de falar com seu OpenClaw de qualquer lugar.

### Passo a passo:

1. **Crie um bot** ê¢â¬â Abra o Telegram e mande mensagem pro [@BotFather](https://t.me/BotFather)
2. **Envie `/newbot`** ê¢â¬â Siga as instruêÂ§êÂµes para nomear seu bot
3. **Copie o token** ê¢â¬â O BotFather te dêÂ¡ um token tipo `123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew11`
4. **Adicione ao `.env`:**
   ```env
   TELEGRAM_BOT_TOKEN=123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew11
   ```
5. **Reinicie o container:**
   ```bash
   docker compose restart
   ```
6. **Mande mensagem pro seu bot** no Telegram ê¢â¬â ele vai te dar um **cêÂ³digo de pareamento**
7. **Aprove o pareamento** dentro do container:
   ```bash
   docker exec openclaw openclaw pairing approve telegram <code>
   ```

> ê°Å¸âÂ¡ O sistema de pareamento garante que sêÂ³ usuêÂ¡rios aprovados possam falar com seu bot. êâ° uma funcionalidade de seguranêÂ§a ê¢â¬â sem aprovaêÂ§êÂ£o, o bot nêÂ£o responde a estranhos.

---

## ê°Å¸âÂ² ConfiguraêÂ§êÂ£o do WhatsApp

VocêÂª pode conectar o OpenClaw ao WhatsApp via pareamento por QR code.

### Passo a passo:

1. **Execute o comando de login:**
   ```bash
   docker exec -it openclaw openclaw channels login whatsapp
   ```
2. **Escaneie o QR code** com seu WhatsApp (ConfiguraêÂ§êÂµes ê¢â â Aparelhos Conectados ê¢â â Conectar um Aparelho)
3. **Pronto!** Seu OpenClaw agora estêÂ¡ conectado ao WhatsApp

### ê¢Å¡Â ê¯Â¸Â NêÂºmero Pessoal vs. NêÂºmero Dedicado

**Usando seu nêÂºmero pessoal:**
- O bot vai ver mensagens de todos os seus contatos
- Por padrêÂ£o, a polêÂ­tica de DM êÂ© `pairing` ê¢â¬â outros podem receber um prompt de pareamento
- **Recomendado:** Defina `dmPolicy: allowlist` com apenas o seu nêÂºmero

**Usando um nêÂºmero dedicado (recomendado):**
- Pegue um chip prêÂ©-pago barato ou um nêÂºmero do Google Voice
- SeparaêÂ§êÂ£o mais limpa entre mensagens pessoais e do bot

---

## ê°Å¸âÅ ConfiguraêÂ§êÂ£o do Discord

1. **Crie um bot no Discord Developer Portal:**
   - Acesse [discord.com/developers/applications](https://discord.com/developers/applications)
   - Crie uma nova aplicaêÂ§êÂ£o
   - VêÂ¡ em "Bot" ê¢â â "Add Bot"
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

## ê°Å¸âÂ¼ ConfiguraêÂ§êÂ£o do Slack

1. **Crie um Slack App:**
   - Acesse [api.slack.com/apps](https://api.slack.com/apps)
   - Crie um novo app
   - Adicione os scopes necessêÂ¡rios (chat:write, etc.)
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

## ê°Å¸ââ SeguranêÂ§a

Este setup Docker implementa **7 de 10** medidas de hardening de seguranêÂ§a automaticamente. Veja o [SECURITY.md](SECURITY.md) para o checklist completo.

### O que o Docker faz automaticamente:
| ProteêÂ§êÂ£o | Status |
|----------|--------|
| Gateway vinculado apenas ao `127.0.0.1` (lado do host) | ê¢Åâ¦ AutomêÂ¡tico |
| PolêÂ­tica de DM requer aprovaêÂ§êÂ£o de pareamento | ê¢Åâ¦ AutomêÂ¡tico |
| Arquivos de config com `chmod 600` | ê¢Åâ¦ AutomêÂ¡tico |
| Container roda como usuêÂ¡rio nêÂ£o-root | ê¢Åâ¦ AutomêÂ¡tico |
| Sem escalaêÂ§êÂ£o de privilêÂ©gios (`no-new-privileges`) | ê¢Åâ¦ AutomêÂ¡tico |
| Logging e diagnêÂ³sticos habilitados | ê¢Åâ¦ AutomêÂ¡tico |
| Secrets via variêÂ¡veis de ambiente | ê¢Åâ¦ AutomêÂ¡tico |

### Auditoria de seguranêÂ§a:
```bash
docker exec openclaw openclaw doctor
```

---

## ê°Å¸âÂ¦ Volumes

Volumes Docker persistem seus dados entre reinêÂ­cios e rebuilds do container.

| Volume | Caminho no Container | Finalidade |
|--------|---------------------|------------|
| `openclaw-data` | `/home/openclaw/.openclaw` | Config, dados de sessêÂ£o, tokens de auth, info de pareamento |
| `openclaw-workspace` | `/home/openclaw/workspace` | Workspace do agente ê¢â¬â AGENTS.md, SOUL.md, skills, arquivos de projeto |
| `openclaw-logs` | `/home/openclaw/logs` | Arquivos de log (NêÆO em /tmp ê¢â¬â sobrevive a reinêÂ­cios) |

### FaêÂ§a backup dos seus dados:
```bash
# Backup de todos os volumes
docker run --rm -v openclaw-data:/data -v $(pwd):/backup alpine tar czf /backup/openclaw-data.tar.gz -C /data .
docker run --rm -v openclaw-workspace:/data -v $(pwd):/backup alpine tar czf /backup/openclaw-workspace.tar.gz -C /data .
```

### Resetar tudo:
```bash
docker compose down -v  # ê¢Å¡Â ê¯Â¸Â Apaga TODOS os dados incluindo config e workspace
```

---

## ê°Å¸âºÂ ê¯Â¸Â Comandos êÅ¡teis

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

## ê°Å¸âÂ¥ê¯Â¸Â Acesso ao Webchat (Remoto)

O gateway êÂ© vinculado ao `127.0.0.1` (apenas loopback). Para acessar o webchat de outra mêÂ¡quina, use um **têÂºnel SSH**:

```bash
# Na sua mêÂ¡quina local (a que tem o navegador):
ssh -L 18789:localhost:18789 user@your-server-ip

# Depois abra no navegador:
# http://127.0.0.1:18789/chat
```

Esta êÂ© a forma mais segura de acessar a interface web remotamente ê¢â¬â sem portas expostas, todo trêÂ¡fego criptografado via SSH.

### Alternativa: Tailscale (recomendado para uso frequente)

O OpenClaw tem suporte nativo a Tailscale. Configure `gateway.tailscale.mode`:

- `off` ê¢â¬â sem automaêÂ§êÂ£o (padrêÂ£o)
- `serve` ê¢â¬â HTTPS apenas na tailnet
- `funnel` ê¢â¬â HTTPS pêÂºblico (requer autenticaêÂ§êÂ£o por senha)

```bash
# No seu servidor:
curl -fsSL https://tailscale.com/install.sh | sh
sudo tailscale up

# Acesse o webchat via: http://<tailscale-ip>:18789/chat
```

---

## ê°Å¸âÂ§ SoluêÂ§êÂ£o de Problemas

### Problemas no Windows

| Erro | Causa | SoluêÂ§êÂ£o |
|------|-------|---------|
| `open //./pipe/dockerDesktopLinuxEngine: O sistema nêÂ£o pode encontrar o arquivo` | Docker Desktop nêÂ£o estêÂ¡ rodando | Abra o Docker Desktop pelo menu Iniciar, espere por "Docker is running" |
| `.env not found` | Arquivo de config faltando | Execute `copy .env.example .env` e depois `notepad .env` |
| `WSL docker-desktop Stopped` | WSL nêÂ£o iniciou | Abra o Docker Desktop ê¢â¬â ele inicia o WSL automaticamente |
| Build trava ou falha | RAM insuficiente | Docker Desktop ê¢â â Settings ê¢â â Resources ê¢â â aumente para 4GB+ |
| `exec entrypoint.sh: no such file or directory` | TerminaêÂ§êÂµes de linha CRLF do Windows | Clone o repo novamente: `git config --global core.autocrlf input` e depois `git clone` |

### Problemas no Linux / Mac

| Erro | Causa | SoluêÂ§êÂ£o |
|------|-------|---------|
| `permission denied` | NêÂ£o estêÂ¡ no grupo docker | `sudo usermod -aG docker $USER` e depois **faêÂ§a logout e login novamente** |
| `port already in use` | Outro serviêÂ§o na porta 18789 | Mude a porta no `docker-compose.yml` ou pare o outro serviêÂ§o |
| `no space left on device` | Disco cheio | `docker system prune -a` para limpar imagens antigas |

### Problemas de TêÂºnel SSH / Acesso Remoto

Se vocêÂª nêÂ£o consegue acessar o webchat localmente na sua mêÂ¡quina apêÂ³s criar um têÂºnel SSH, siga estes passos:

**1. Remova a chave SSH antiga (se o IP do servidor mudou):**
```bash
ssh-keygen -R seu-servidor-ip
```

**2. Teste a conexêÂ£o SSH:**
```bash
ssh -o StrictHostKeyChecking=accept-new -o BatchMode=yes usuario@seu-servidor-ip "echo 'ConexêÂ£o SSH OK!' && hostname"
```

> ê°Å¸âÂ¡ Se falhar, adicione sua chave pêÂºblica ao `~/.ssh/authorized_keys` do servidor.

**3. Crie o têÂºnel SSH:**
```bash
# TêÂºnel em foreground (fecha quando vocêÂª sair do terminal)
ssh -L 18789:127.0.0.1:18789 usuario@seu-servidor-ip

# TêÂºnel em background (roda silenciosamente)
ssh -f -N -L 18789:127.0.0.1:18789 usuario@seu-servidor-ip
```

**4. Acesse o webchat:**
```
http://127.0.0.1:18789/chat
```

| Problema | Causa | SoluêÂ§êÂ£o |
|----------|-------|---------|
| `WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED` | IP do servidor mudou ou reinstalou | `ssh-keygen -R seu-servidor-ip` e reconecte |
| `Permission denied (publickey)` | Chave SSH nêÂ£o configurada | Adicione sua chave pêÂºblica ao servidor: `ssh-copy-id usuario@servidor` |
| `Connection refused` na porta 18789 | TêÂºnel nêÂ£o criado ou container parado | Verifique se o têÂºnel estêÂ¡ ativo e se o container estêÂ¡ rodando |
| `bind: Address already in use` | Porta local jêÂ¡ em uso | Use outra porta: `ssh -L 18790:127.0.0.1:18789 ...` e acesse via `http://127.0.0.1:18790/chat` |

### Problemas de ConfiguraêÂ§êÂ£o

| Problema | Causa | SoluêÂ§êÂ£o |
|----------|-------|---------|
| **"Unknown model: anthropic/claude-sonnet-4.5"** | Falta o prefixo `openrouter/` | Use `openrouter/anthropic/claude-sonnet-4.5` (sempre inclua o prefixo `openrouter/`) |
| **Bot nêÂ£o responde apêÂ³s mudar o modelo** | Config corrompida ou modelo invêÂ¡lido | Execute `docker compose down -v` (ê¢Å¡Â ê¯Â¸Â apaga dados), depois `docker compose up -d` para comeêÂ§ar do zero |
| **MudanêÂ§as no .env nêÂ£o aplicadas** | `docker compose restart` nêÂ£o recarrega variêÂ¡veis de ambiente | Use `docker compose down && docker compose up -d` para recarregar o `.env` |

---

## ê°Å¸ââ MigraêÂ§êÂ£o do Moltbot/Clawdbot

Se vocêÂª estêÂ¡ vindo do setup antigo `docker-moltbot` ou `docker-clawdbot`, aqui estêÂ¡ o que mudou:

### O que êÂ© diferente:

| Antigo (Moltbot/Clawdbot) | Novo (OpenClaw) |
|---------------------------|-----------------|
| Pacote: `clawdbot` / `moltbot` | Pacote: `openclaw` |
| CLI: `clawdbot` / `moltbot` | CLI: `openclaw` |
| Dir de config: `~/.clawdbot` / `~/.moltbot` | Dir de config: `~/.openclaw` |
| Docs: `docs.molt.bot` | Docs: `docs.openclaw.ai` |
| Container: `moltbot` | Container: `openclaw` |

### Passos da migraêÂ§êÂ£o:

1. **FaêÂ§a backup dos seus dados:**
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

## ê°Å¸âÂ» Requisitos

| Recurso | MêÂ­nimo | Recomendado |
|---------|--------|-------------|
| **RAM** | 2 GB | 4 GB (com Whisper) |
| **Disco** | 5 GB | 10+ GB |
| **CPU** | 1 core | 2+ cores |
| **Docker** | Engine 24+ / Compose v2+ | êÅ¡ltima versêÂ£o estêÂ¡vel |
| **SO** | Linux, macOS, Windows 10+ | Ubuntu 22.04+ / macOS 13+ |
| **Rede** | Acesso êÂ  internet | Banda larga estêÂ¡vel |

---

## ê°Å¸Â¤Â Contribuindo

PRs sêÂ£o bem-vindos! Siga o checklist de seguranêÂ§a em [SECURITY.md](SECURITY.md).

1. FaêÂ§a fork do repo
2. Crie uma branch de feature: `git checkout -b my-feature`
3. FaêÂ§a commit das suas mudanêÂ§as: `git commit -m 'Add my feature'`
4. FaêÂ§a push: `git push origin my-feature`
5. Abra um Pull Request

---

## ê°Å¸âÅ LicenêÂ§a

[MIT](LICENSE) ê¢â¬â use como quiser.

---

<p align="center">
  <a href="https://openclaw.ai">openclaw.ai</a> ê¢â¬Â¢
  <a href="https://docs.openclaw.ai">DocumentaêÂ§êÂ£o</a> ê¢â¬Â¢
  <a href="https://discord.gg/clawd">Discord</a> ê¢â¬Â¢
  <a href="https://github.com/openclaw/openclaw">GitHub</a>
</p>

---

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="32" />
  <p><strong>Arckhé AI</strong></p>
</div>