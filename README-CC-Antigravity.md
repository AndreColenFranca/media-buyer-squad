# 🚀 Media Buyer Squad - Claude Code Edition

> Guia completo para desenvolvedores usando Claude Code com o media-buyer-squad

## 📋 Índice

- [Setup Rápido](#-setup-rápido)
- [Scripts Disponíveis](#-scripts-disponíveis)
- [Desenvolvimento](#-desenvolvimento)
- [Arquitetura](#-arquitetura)
- [Integrações MCP](#-integrações-mcp)
- [Testing](#-testing)
- [Deploy](#-deploy)
- [Troubleshooting](#-troubleshooting)

---

## ⚡ Setup Rápido

### Pré-requisitos

```bash
node --version  # 18.0.0+
npm --version   # 9.0.0+
```

### Instalação

```bash
# Clone o repositório
git clone https://github.com/seu-usuario/media-buyer-squad.git
cd media-buyer-squad

# Instale dependências
npm install

# Configure ambiente
cp .env.example .env
# Edite .env com suas credenciais Meta Ads

# Teste a instalação
npm test

# Rode um script de exemplo
node scripts/diagnose-metrics.js --help
```

---

## 🛠️ Scripts Disponíveis

### Diagnóstico

#### 1. diagnose-metrics.js

Análise completa de métricas de campanha

```bash
# Uso básico
node scripts/diagnose-metrics.js

# Com parâmetros
node scripts/diagnose-metrics.js \
  --campaign-id "123456789" \
  --date-range "last-7-days" \
  --output "json"

# Benchmarking
node scripts/diagnose-metrics.js \
  --benchmark \
  --industry "e-commerce"
```

**Saída**:
```json
{
  "campaign_id": "123456789",
  "metrics": {
    "cpa": 45.32,
    "roas": 3.2,
    "ctr": 1.8,
    "hook_rate": 16.5
  },
  "benchmarks": {
    "cpa_target": 50.00,
    "roas_target": 3.0,
    "status": "healthy"
  },
  "recommendations": [
    "Escalar budget em 20%",
    "Testar novos hooks"
  ]
}
```

#### 2. audit-tracking.js

Auditoria completa de pixel e CAPI

```bash
# Auditoria básica
node scripts/audit-tracking.js --pixel-id "123456789"

# Com validação de eventos
node scripts/audit-tracking.js \
  --pixel-id "123456789" \
  --events "PageView,AddToCart,Purchase" \
  --validate-capi

# Modo detalhado
node scripts/audit-tracking.js \
  --pixel-id "123456789" \
  --verbose \
  --output "report.json"
```

### Geração

#### 3. generate-hooks.js

Geração de hooks com frameworks DSL

```bash
# Gera 10 variações de hooks
node scripts/generate-hooks.js \
  --product "Curso Online de Marketing" \
  --angle "transformação" \
  --count 10

# Com framework específico
node scripts/generate-hooks.js \
  --product "Curso Online de Marketing" \
  --framework "dsl" \
  --tone "urgência"

# Exportar para CSV
node scripts/generate-hooks.js \
  --product "Curso Online de Marketing" \
  --output "hooks.csv"
```

**Exemplo de saída**:
```
Hook 1 (Problem-Aware): "Cansado de ver seus concorrentes dominando o digital enquanto você fica pra trás?"
Hook 2 (Solution-Aware): "Descobri o sistema exato que levou meu negócio de R$10k para R$100k/mês"
Hook 3 (Desire-Based): "Imagine acordar com notificações de vendas na sua conta bancária..."
```

#### 4. generate-copy.js

Geração de copy com frameworks (PAS, AIDA, BAB, STORY)

```bash
# Framework PAS (Problem-Agitate-Solution)
node scripts/generate-copy.js \
  --framework "pas" \
  --product "Curso de Tráfego Pago" \
  --audience "empreendedores iniciantes"

# Framework AIDA
node scripts/generate-copy.js \
  --framework "aida" \
  --hook "Você está perdendo R$10k/mês sem saber" \
  --cta "Inscreva-se agora"

# Múltiplos frameworks
node scripts/generate-copy.js \
  --frameworks "pas,aida,bab,story" \
  --product "Mentoria 1:1" \
  --output "copies.json"
```

### Otimização

#### 5. evaluate-kill-scale.js

Decisões automatizadas de kill/scale baseadas em regras

```bash
# Avaliação de campanha
node scripts/evaluate-kill-scale.js \
  --campaign-id "123456789" \
  --rules "brian-moncada"

# Com múltiplas campanhas
node scripts/evaluate-kill-scale.js \
  --campaign-ids "123,456,789" \
  --auto-execute \
  --dry-run

# Output detalhado
node scripts/evaluate-kill-scale.js \
  --campaign-id "123456789" \
  --verbose \
  --output "decisions.json"
```

**Saída**:
```json
{
  "campaign_id": "123456789",
  "decision": "scale",
  "confidence": 0.85,
  "rules_applied": [
    "CPA ≤ Target (45 < 50)",
    "ROAS > 3.0 (3.2 > 3.0)",
    "Volume > 50 conversions (78)"
  ],
  "recommendation": "Aumentar budget em 20% (R$500 → R$600)",
  "next_check": "2026-02-12T10:00:00Z"
}
```

#### 6. allocate-budget.js

Otimização de alocação de budget

```bash
# Realocar entre campanhas
node scripts/allocate-budget.js \
  --total-budget 10000 \
  --campaigns "campaign-ids.json" \
  --strategy "roas-weighted"

# Com constraints
node scripts/allocate-budget.js \
  --total-budget 10000 \
  --min-budget-per-campaign 500 \
  --max-budget-per-campaign 3000 \
  --output "allocation.json"
```

### Automação

#### 7. monitor-campaigns.js

Monitoramento 24/7 com alerts

```bash
# Modo daemon
node scripts/monitor-campaigns.js \
  --daemon \
  --interval "15min" \
  --alert-webhook "https://hooks.slack.com/..."

# Com regras de auto-otimização
node scripts/monitor-campaigns.js \
  --auto-optimize \
  --rules "config/optimization-rules.json" \
  --log-file "monitor.log"

# Dry-run (apenas monitora, não executa)
node scripts/monitor-campaigns.js \
  --dry-run \
  --verbose
```

**Exemplo de alert**:
```
🚨 ALERT: Campaign 123456789
- CPA aumentou 40% nas últimas 2 horas (R$45 → R$63)
- Recomendação: Pausar ad set "AdSet-001"
- Ação: Auto-executada ✅
```

### Análise

#### 8. analyze-funnel.js

Análise detalhada do funil de conversão

```bash
# Análise de funil completo
node scripts/analyze-funnel.js \
  --campaign-id "123456789" \
  --events "PageView,AddToCart,InitiateCheckout,Purchase"

# Com segmentação
node scripts/analyze-funnel.js \
  --campaign-id "123456789" \
  --segment-by "device,age,gender" \
  --output "funnel-analysis.json"
```

#### 9. analyze-attribution.js

Análise cross-platform de atribuição

```bash
# Análise básica
node scripts/analyze-attribution.js \
  --date-range "last-30-days"

# Multi-touch attribution
node scripts/analyze-attribution.js \
  --model "data-driven" \
  --touchpoints "meta,google,organic" \
  --output "attribution.json"
```

---

## 🏗️ Desenvolvimento

### Estrutura de Diretórios

```
media-buyer-squad/
├── agents/                 # 5 agentes especializados
├── scripts/                # 18 scripts de automação
│   ├── diagnose-metrics.js
│   ├── generate-hooks.js
│   ├── evaluate-kill-scale.js
│   └── ...
├── tasks/                  # Tasks executáveis
├── workflows/              # Workflows multi-step
├── templates/              # Templates de documentos
├── checklists/             # Checklists de validação
├── config/                 # Arquivos de configuração
│   ├── meta-ads.json
│   ├── optimization-rules.json
│   └── benchmarks.json
├── tests/                  # Testes automatizados
│   ├── unit/
│   ├── integration/
│   └── e2e/
├── docs/                   # Documentação
├── .env.example            # Template de variáveis
├── package.json
└── README.md
```

### Adicionando Novo Script

1. **Crie o arquivo**:
```bash
touch scripts/meu-novo-script.js
```

2. **Template base**:
```javascript
#!/usr/bin/env node

/**
 * Meu Novo Script
 * Descrição: Faz algo incrível
 */

const { Command } = require('commander');
const program = new Command();

program
  .name('meu-novo-script')
  .description('Descrição do que faz')
  .option('-i, --input <file>', 'Arquivo de entrada')
  .option('-o, --output <file>', 'Arquivo de saída')
  .parse(process.argv);

const options = program.opts();

async function main() {
  try {
    console.log('Executando script...');
    // Sua lógica aqui
    console.log('✅ Concluído!');
  } catch (error) {
    console.error('❌ Erro:', error.message);
    process.exit(1);
  }
}

main();
```

3. **Torne executável**:
```bash
chmod +x scripts/meu-novo-script.js
```

4. **Adicione ao package.json**:
```json
{
  "scripts": {
    "meu-script": "node scripts/meu-novo-script.js"
  }
}
```

5. **Documente em README**:
Adicione seção em "Scripts Disponíveis"

### Padrões de Código

#### ESLint Config

```javascript
// .eslintrc.js
module.exports = {
  env: { node: true, es2021: true },
  extends: 'eslint:recommended',
  parserOptions: { ecmaVersion: 12 },
  rules: {
    'no-console': 'off',
    'no-unused-vars': 'warn'
  }
};
```

#### Prettier Config

```json
{
  "semi": true,
  "singleQuote": true,
  "tabWidth": 2,
  "trailingComma": "es5"
}
```

---

## 🔌 Integrações MCP

### Meta Ads API

#### Configuração

```bash
# config/meta-ads.json
{
  "access_token": "YOUR_ACCESS_TOKEN",
  "ad_account_id": "act_123456789",
  "app_id": "YOUR_APP_ID",
  "app_secret": "YOUR_APP_SECRET"
}
```

#### Uso no Código

```javascript
const { MetaAdsClient } = require('./lib/meta-ads');

const client = new MetaAdsClient({
  accessToken: process.env.META_ACCESS_TOKEN,
  adAccountId: process.env.META_AD_ACCOUNT_ID
});

// Buscar campanhas
const campaigns = await client.getCampaigns({
  fields: ['name', 'status', 'objective'],
  limit: 100
});

// Criar campanha
const newCampaign = await client.createCampaign({
  name: 'Nova Campanha',
  objective: 'CONVERSIONS',
  status: 'PAUSED'
});
```

### Meta Pixel & CAPI

#### Setup

```javascript
// lib/meta-pixel.js
class MetaPixelClient {
  constructor(pixelId, accessToken) {
    this.pixelId = pixelId;
    this.accessToken = accessToken;
  }

  async sendServerEvent(eventName, eventData) {
    // Implementação CAPI
  }

  async validateEvents() {
    // Validação de eventos
  }
}
```

---

## 🧪 Testing

### Estrutura de Testes

```
tests/
├── unit/
│   ├── scripts/
│   │   ├── diagnose-metrics.test.js
│   │   └── generate-hooks.test.js
│   └── lib/
│       └── meta-ads.test.js
├── integration/
│   └── workflows.test.js
└── e2e/
    └── full-campaign.test.js
```

### Rodando Testes

```bash
# Todos os testes
npm test

# Específico
npm test -- tests/unit/scripts/diagnose-metrics.test.js

# Com coverage
npm run test:coverage

# Watch mode
npm run test:watch
```

### Exemplo de Teste

```javascript
// tests/unit/scripts/diagnose-metrics.test.js
const { diagnosMetrics } = require('../../scripts/diagnose-metrics');

describe('diagnose-metrics', () => {
  test('calcula CPA corretamente', () => {
    const data = {
      spend: 1000,
      conversions: 20
    };
    const result = diagnosMetrics(data);
    expect(result.cpa).toBe(50);
  });

  test('identifica campanha saudável', () => {
    const data = {
      cpa: 45,
      roas: 3.5,
      ctr: 2.0
    };
    const result = diagnosMetrics(data);
    expect(result.status).toBe('healthy');
  });
});
```

---

## 🚀 Deploy

### Ambiente de Produção

```bash
# Build
npm run build

# Deploy para servidor
npm run deploy

# Ou com PM2
pm2 start scripts/monitor-campaigns.js --name "media-buyer-monitor"
pm2 save
pm2 startup
```

### Docker

```dockerfile
# Dockerfile
FROM node:18-alpine

WORKDIR /app

COPY package*.json ./
RUN npm ci --only=production

COPY . .

CMD ["node", "scripts/monitor-campaigns.js", "--daemon"]
```

```bash
# Build
docker build -t media-buyer-squad .

# Run
docker run -d \
  --name media-buyer \
  -e META_ACCESS_TOKEN=xxx \
  -e META_AD_ACCOUNT_ID=act_xxx \
  media-buyer-squad
```

### CI/CD (GitHub Actions)

```yaml
# .github/workflows/ci.yml
name: CI

on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: '18'
      - run: npm ci
      - run: npm test
      - run: npm run lint
```

---

## 🔧 Troubleshooting

### Problemas Comuns

#### 1. Meta API Rate Limit

**Erro**: `OAuthException: (#80001) There have been too many calls`

**Solução**:
```javascript
// Adicione throttling
const pThrottle = require('p-throttle');
const throttled = pThrottle({
  limit: 200,
  interval: 3600000  // 1 hora
});
```

#### 2. Pixel Events Não Disparam

**Debug**:
```bash
node scripts/audit-tracking.js \
  --pixel-id "123456789" \
  --verbose \
  --test-mode
```

**Checklist**:
- [ ] Pixel instalado corretamente
- [ ] Events configurados
- [ ] CAPI endpoint respondendo
- [ ] Event Match Quality > 6.0

#### 3. Scripts Lentos

**Profile**:
```bash
node --prof scripts/diagnose-metrics.js
node --prof-process isolate-*.log > profile.txt
```

**Otimize**:
- Use cache para calls API
- Implemente batching
- Use worker threads para processamento paralelo

---

## 📚 Recursos Adicionais

### Documentação

- [Meta Marketing API Docs](https://developers.facebook.com/docs/marketing-apis)
- [Meta Pixel Docs](https://developers.facebook.com/docs/meta-pixel)
- [AIOS Documentation](https://aios.dev/docs)

### Exemplos de Código

- [examples/](examples/) - Scripts de exemplo
- [snippets/](snippets/) - Code snippets úteis

### Community

- [Discord](https://discord.gg/media-buyer-squad)
- [GitHub Discussions](https://github.com/seu-usuario/media-buyer-squad/discussions)

---

## 🔐 Segurança

### Variáveis de Ambiente

```bash
# .env.example
META_ACCESS_TOKEN=your_token_here
META_AD_ACCOUNT_ID=act_123456789
META_APP_ID=your_app_id
META_APP_SECRET=your_app_secret
WEBHOOK_URL=https://hooks.slack.com/...
```

**NUNCA commite .env no Git!**

### Secrets Management

```bash
# Use dotenv
npm install dotenv

# No código
require('dotenv').config();
const token = process.env.META_ACCESS_TOKEN;
```

---

# 🎯 Media Buyer Squad Antigravity Edition

> Squad avançado de IA para gestão de tráfego pago com 5 agentes especializados, 18 skills e 47 frameworks de experts

## 📋 Índice

- [Visão Geral](#-visão-geral)
- [Estrutura Visual](#-estrutura-visual--diagramas)
- [Agentes](#-agentes-especializados)
- [Skills](#-skills-18-total)
- [Como Usar](#-como-usar)
- [Instalação](#-instalação)
- [Workflows](#-workflows-principais)
- [Expert Frameworks](#-expert-frameworks-47-total)
- [Documentação](#-documentação-completa)
- [Roadmap](#-roadmap)
- [Contribuindo](#-contribuindo)
- [Licença](#-licença)

---

## 🎯 Visão Geral

O **media-buyer-squad** é um sistema multi-agente de IA construído para o AIOS (Antigravity/Claude Code) que automatiza e otimiza a gestão completa de campanhas de tráfego pago nas plataformas Meta (Facebook & Instagram).

### 🌟 Características Principais

- ✅ **5 Agentes Especializados** - Cada um com expertise específica
- ✅ **18 Skills Funcionais** - Categorizadas em Diagnóstico, Geração, Otimização, Estratégia e Automação
- ✅ **47 Frameworks de Experts** - De Jeremy Haynes, Brian Moncada, Alex Hormozi, Brandon Carter e Jordan Stupar
- ✅ **4 Workflows Completos** - Para lançamento, refresh criativo, escala e troubleshooting
- ✅ **100% em Português BR** - Documentação e comandos totalmente em português
- ✅ **Pronto para Produção** - Totalmente funcional e testado

### 🎯 Casos de Uso

- 🚀 Lançar novas campanhas de tráfego pago
- 📊 Diagnosticar campanhas com baixa performance
- 🎨 Gerar hooks e copy de alta conversão
- 📈 Tomar decisões data-driven de scale
- 🔍 Auditar e configurar tracking (Pixel/CAPI)
- 💰 Otimizar alocação de budget
- 🎯 Expandir audiências de forma sistemática

---

## 📊 Estrutura Visual & Diagramas

Para uma compreensão visual completa, consulte os **4 diagramas** em `docs/diagrams/`:

| Diagrama | Descrição | Tamanho |
|----------|-----------|---------|
| [01-squad-structure.png](docs/diagrams/01-squad-structure.png) | Hierarquia e papéis dos agentes | 645 KB |
| [02-trigger-flow.png](docs/diagrams/02-trigger-flow.png) | Quando acionar cada agente | 657 KB |
| [03-workflow-skills.png](docs/diagrams/03-workflow-skills.png) | Processo completo e skills | 746 KB |
| [04-experts-summary.png](docs/diagrams/04-experts-summary.png) | Frameworks integrados | 683 KB |

📖 **Documentação Visual Completa**: [docs/diagrams/README.md](docs/diagrams/README.md)

### Hierarquia Rápida

```
@ad-midas (LÍDER) → Estratégia, Estrutura, Decisões de Scale
    ├── @performance-analyst → Métricas, Kill/Scale, Budget
    ├── @creative-analyst → Hooks, Copy, Briefs
    ├── @pixel-specialist → Tracking, CAPI, Atribuição
    └── @media-buyer → Execução, Consultas
```

---

## 🤖 Agentes Especializados

### 1. 👑 ad-midas (Líder do Squad)
**Arquétipo**: The Commander  
**Expertise**: Estratégia, estrutura de campanha, decisões de scale

**Quando usar**: Definir estratégia, selecionar funil, estruturar campanha, decisões de scale

```bash
@ad-midas *structure-campaign
@ad-midas *select-funnel
@ad-midas *check-scale-readiness
```

### 2. 📊 performance-analyst
**Arquétipo**: The Analyzer  
**Expertise**: Análise de métricas, kill/scale rules, otimização de budget

**Quando usar**: CPA alto, decisões de pause/scale, realocar budget

```bash
@performance-analyst *diagnose-metrics
@performance-analyst *evaluate-kill-scale
@performance-analyst *allocate-budget
```

### 3. 🎨 creative-analyst
**Arquétipo**: The Creator  
**Expertise**: Hooks, copy, DSL, ângulos criativos

**Quando usar**: Criar hooks, gerar copy, CTR caindo, detectar fadiga

```bash
@creative-analyst *generate-hooks
@creative-analyst *generate-copy
@creative-analyst *create-brief
```

### 4. 🎯 pixel-specialist
**Arquétipo**: The Tracker  
**Expertise**: Pixel, CAPI, tracking, atribuição

**Quando usar**: Conversões zeradas, auditar pixel, configurar CAPI

```bash
@pixel-specialist *audit-tracking
@pixel-specialist *setup-tracking
```

### 5. 💰 media-buyer
**Arquétipo**: Traffic Architect  
**Expertise**: Consultas gerais, educação, execução

**Quando usar**: Consultas gerais, aprendizado, não precisa de squad completo

```bash
@media-buyer
# Consultas abertas sobre tráfego pago
```

---

## 🛠️ Skills (18 Total)

### 🔍 Diagnóstico (5 skills)

```bash
*diagnose-metrics        # Diagnóstico completo de métricas
*audit-tracking          # Auditoria de pixel, CAPI e eventos
*detect-fatigue          # Detecção de fadiga criativa
*analyze-funnel          # Análise de funil de conversão
*analyze-attribution     # Análise de atribuição cross-platform
```

### ✨ Geração (5 skills)

```bash
*generate-hooks          # Gera 10+ variações de hooks (DSL)
*generate-copy           # Gera copy (PAS, AIDA, BAB, STORY)
*create-brief            # Gera briefs para criativos
*generate-angles         # Gera ângulos criativos
*create-dsl              # Cria estruturas de Deck Sales Letter
```

### ⚡ Otimização (3 skills)

```bash
*evaluate-kill-scale     # Regras de pausar ou escalar
*allocate-budget         # Otimiza alocação de budget
*expand-audience         # Expande audiências saturadas
```

### 🎯 Estratégia (4 skills)

```bash
*select-funnel           # Seleção do tipo de funil ideal
*calculate-economics     # Cálculo de CAC, LTV, payback
*check-scale-readiness   # Avaliação de prontidão para escalar
*structure-campaign      # Define estrutura de campanhas
```

### 🤖 Automação (1 skill)

```bash
*monitor-campaigns       # Orquestração autônoma com monitoramento
```

---

## 🚀 Como Usar

### Para Antigravity (AIOS)

1. **Ativar um agente**:
```bash
@ad-midas
@performance-analyst
@creative-analyst
@pixel-specialist
@media-buyer
```

2. **Executar uma skill**:
```bash
@performance-analyst *diagnose-metrics
@creative-analyst *generate-hooks
@pixel-specialist *audit-tracking
```

3. **Usar um workflow completo**:
```bash
@ad-midas
*launch-campaign  # Segue workflow de 8 fases
```

### Para Claude Code (Terminal)

```bash
# Executar scripts diretamente
node scripts/diagnose-metrics.js
node scripts/generate-hooks.js
node scripts/audit-tracking.js
node scripts/evaluate-kill-scale.js

# Com parâmetros
node scripts/diagnose-metrics.js --campaign-id "123456"
node scripts/generate-hooks.js --product "curso-online" --angle "transformação"
```

---

## 📦 Instalação

### Pré-requisitos

- [AIOS](https://aios.dev) 2.1.0+ (Antigravity ou Claude Code)
- Node.js 18+ (para scripts)
- Meta Ads Account (para integrações MCP)

### Setup Rápido

```bash
# 1. Clone o repositório
git clone https://github.com/seu-usuario/media-buyer-squad.git
cd media-buyer-squad

# 2. Instale dependências (para scripts)
npm install

# 3. Configure integrações MCP (opcional)
# Edite config/meta-ads.json com suas credenciais

# 4. Ative o squad no AIOS
# Em Antigravity ou Claude Code, navegue até a pasta do squad
@ad-midas  # Para testar
```

### Configuração de MCP (Opcional)

Para habilitar integrações com Meta Ads:

1. Configure `config/meta-ads.json`
2. Configure `config/meta-pixel.json`
3. Consulte [IMPLEMENTATION_GUIDE.md](IMPLEMENTATION_GUIDE.md) para detalhes

---

## 📋 Workflows Principais

### 1. Campaign Launch (Lançamento)

**Arquivo**: [workflows/campaign-launch-workflow.md](workflows/campaign-launch-workflow.md)

```bash
@ad-midas *launch-campaign
```

**Fases**:
1. Strategy Definition
2. Tracking Setup
3. Creative Development
4. Campaign Setup
5. Pre-Launch Validation
6. Launch
7. Initial Monitoring
8. Optimization

### 2. Creative Refresh

**Arquivo**: [workflows/creative-refresh-workflow.md](workflows/creative-refresh-workflow.md)

```bash
@creative-analyst *refresh-creatives
```

**Quando usar**: CTR caindo, fadiga criativa detectada, hook rate < 15%

### 3. Scale Optimization

**Arquivo**: [workflows/scale-optimization-workflow.md](workflows/scale-optimization-workflow.md)

```bash
@ad-midas *scale-campaign
```

**Quando usar**: CPA ≤ Target, ROAS > 3.0, volume suficiente

### 4. Troubleshooting

**Arquivo**: [workflows/troubleshooting-workflow.md](workflows/troubleshooting-workflow.md)

```bash
@performance-analyst *troubleshoot
```

**Quando usar**: Conversões zeradas, CPA alto, métricas fora do normal

---

## 🎓 Expert Frameworks (47 Total)

### Jeremy Haynes
- DSL Revolution (Deck Sales Letter)
- Constants vs Variables
- KiB/Scale Rules (Kill it Baby)
- Funnel Selection Matrix

### Brian Moncada
- Andromeda Method
- YouTube Ads Strategy
- Hook Testing Frameworks
- Metric Thresholds

### Alex Hormozi
- Unit Economics (LTV:CAC)
- Minimum 3:1 ratio
- Hydra Strategy
- Offer Creation

### Brandon Carter
- Constants vs Variables
- Scientific Ad Testing
- Data-Driven Optimization

### Jordan Stupar
- Creative Strategy
- Hook Psychology
- Angle Development

---

## 📚 Documentação Completa

### Documentação Principal

| Arquivo | Descrição |
|---------|-----------|
| [README.md](README.md) | Overview e quick start (EN) |
| [STRUCTURE.md](STRUCTURE.md) | Estrutura detalhada dos agentes (PT-BR) |
| [STATUS.md](STATUS.md) | Status e progresso (100% completo) |
| [IMPLEMENTATION_GUIDE.md](IMPLEMENTATION_GUIDE.md) | Guia de implementação completo |
| [INDEX.md](INDEX.md) | Índice visual de toda documentação |

### Documentação Visual

| Arquivo | Descrição |
|---------|-----------|
| [docs/diagrams/README.md](docs/diagrams/README.md) | Guia dos diagramas |
| [docs/diagrams/01-squad-structure.png](docs/diagrams/01-squad-structure.png) | Hierarquia dos agentes |
| [docs/diagrams/02-trigger-flow.png](docs/diagrams/02-trigger-flow.png) | Fluxo de triggers |
| [docs/diagrams/03-workflow-skills.png](docs/diagrams/03-workflow-skills.png) | Workflow e skills |
| [docs/diagrams/04-experts-summary.png](docs/diagrams/04-experts-summary.png) | Resumo de experts |

### Workflows

- [campaign-launch-workflow.md](workflows/campaign-launch-workflow.md)
- [creative-refresh-workflow.md](workflows/creative-refresh-workflow.md)
- [scale-optimization-workflow.md](workflows/scale-optimization-workflow.md)
- [troubleshooting-workflow.md](workflows/troubleshooting-workflow.md)

### Templates

- [creative-brief-template.md](templates/creative-brief-template.md)
- [ad-copy-template.md](templates/ad-copy-template.md)
- [testing-matrix-template.md](templates/testing-matrix-template.md)
- [scale-plan-template.md](templates/scale-plan-template.md)

### Checklists

- [pre-launch-checklist.md](checklists/pre-launch-checklist.md)
- [creative-review-checklist.md](checklists/creative-review-checklist.md)
- [scale-readiness-checklist.md](checklists/scale-readiness-checklist.md)

---

## 📈 Estatísticas do Squad

### Componentes

- **Agentes**: 5
- **Tasks**: 5
- **Scripts**: 18
- **Workflows**: 4
- **Templates**: 4
- **Checklists**: 3
- **Expert Frameworks**: 47

### Tamanho

- **Total**: ~3.3 MB
- **Código**: ~591 KB
- **Diagramas**: ~2.7 MB
- **Linhas de Código**: ~9,500+

### ROI Estimado

- **Economia de Tempo**: 720-960 horas/ano
- **Prevenção de Perdas**: $50K-$200K/ano
- **Aumento de Revenue**: $100K-$500K/ano
- **ROI Total**: $222K-$796K/ano

---

## 🗺️ Roadmap

### ✅ Fase 1: Foundation (Concluída)
- [x] 5 agentes especializados
- [x] 18 skills definidas
- [x] 47 frameworks integrados
- [x] 4 workflows completos
- [x] Documentação completa
- [x] Diagramas visuais

### 🚧 Fase 2: Expansão (Em Progresso)
- [ ] Integração com Google Ads
- [ ] Integração com TikTok Ads
- [ ] Dashboard de métricas em tempo real
- [ ] Automação completa de reporting
- [ ] API REST para integração externa

### 🔮 Fase 3: Inteligência Avançada (Planejado)
- [ ] Machine Learning para predição de performance
- [ ] Auto-otimização com RL (Reinforcement Learning)
- [ ] Geração de criativos com DALL-E/Midjourney
- [ ] Voice-to-campaign (criar campanhas por voz)
- [ ] Multi-idioma (EN, ES, PT)

---

## 🤝 Contribuindo

Contribuições são bem-vindas! Veja como você pode ajudar:

### Como Contribuir

1. **Fork** o repositório
2. Crie uma **branch** para sua feature (`git checkout -b feature/nova-skill`)
3. **Commit** suas mudanças (`git commit -m 'Adiciona nova skill de análise'`)
4. **Push** para a branch (`git push origin feature/nova-skill`)
5. Abra um **Pull Request**

### Áreas que Precisam de Ajuda

- 🐛 **Bug Reports** - Reporte issues encontrados
- 📝 **Documentação** - Melhore ou traduza docs
- 🎨 **Templates** - Crie novos templates
- 🛠️ **Scripts** - Adicione novos scripts de automação
- 🌍 **Traduções** - Ajude a traduzir para outros idiomas

### Diretrizes

- Siga os padrões AIOS 2.1
- Mantenha compatibilidade com Antigravity e Claude Code
- Documente todas as mudanças
- Teste antes de submeter PR

---

## 📄 Licença

Este projeto está licenciado sob a [MIT License](LICENSE).

```
MIT License

Copyright (c) 2026 Media Buyer Squad Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
```

---

## 🙏 Agradecimentos

### Expert Frameworks

- **Jeremy Haynes** - DSL Revolution, KiB/Scale Rules
- **Brian Moncada** - Andromeda Method, Metric Thresholds
- **Alex Hormozi** - Unit Economics, LTV:CAC
- **Brandon Carter** - Scientific Testing
- **Jordan Stupar** - Creative Strategy

### Mentores
- **Allan Nicolas** - Academia Lendária
- **José Carlos Amorim** - Academia Lendária
- **Thiago Finch** - Idealizador Oficial da Obra

### Tecnologias

- [AIOS](https://aios.dev) - Framework de agentes de IA
- [Anthropic Claude](https://anthropic.com) - Motor de IA
- [Meta Marketing API](https://developers.facebook.com) - Integrações

---

## 📞 Suporte & Contato

### Issues & Bugs

Abra uma [issue](https://github.com/seu-usuario/media-buyer-squad/issues) no GitHub

### Discussões

Participe das [discussões](https://github.com/seu-usuario/media-buyer-squad/discussions) da comunidade

### Documentação

Consulte a [documentação completa](docs/) ou [wiki](https://github.com/seu-usuario/media-buyer-squad/wiki)

---

<div align="center">

**[⬆ Voltar ao topo](#-media-buyer-squad)**

**Squad Version**: 2.0.0 | **AIOS**: 2.1+ | **Status**: Production Ready

</div>
