# VTEX AI Engineering Agent

Ambiente de copiloto de engenharia especializado no ecossistema VTEX, construído sobre o Claude Code com VTEX Developer MCP e VTEX Skills.

## O que é

Este repositório configura o Claude Code como um agente de engenharia VTEX completo, capaz de:

- Consultar documentação oficial e especificações de API em tempo real via MCP
- Aplicar contexto específico de plataforma via 46 skills oficiais da VTEX
- Identificar a arquitetura do projeto (VTEX IO, FastStore, Store Framework, Headless)
- Implementar, revisar e testar código respeitando as convenções de cada stack
- Operar com autonomia controlada — sem deploy ou operações destrutivas sem autorização explícita

## Pré-requisitos

- [Node.js](https://nodejs.org/) v18 ou superior
- [Claude Code](https://claude.ai/code) instalado globalmente
- [VTEX CLI](https://developers.vtex.com/docs/guides/vtex-io-documentation-vtex-io-cli-install) instalado globalmente (opcional)

## Instalação

```bash
git clone https://github.com/felipe-ssilva/vtex-ai-engineering-agent.git
cd vtex-ai-engineering-agent
```

O repositório já inclui as skills instaladas e o MCP configurado. Abra o Claude Code neste diretório:

```bash
claude
```

O VTEX Developer MCP e as 46 skills são carregados automaticamente.

## Estrutura

```
.
├── CLAUDE.md                  # Instruções permanentes do agente
├── .mcp.json                  # Configuração do VTEX Developer MCP
├── skills-lock.json           # Lock file das skills instaladas
├── .claude/skills/            # Skills linkadas para o Claude Code
└── .agents/skills/            # Skills instaladas (fonte)
    ├── faststore-storefront/
    ├── vtex-io-*/
    ├── payment-*/
    ├── marketplace-*/
    ├── headless-*/
    └── ...
```

## VTEX Developer MCP

Conecta o agente à documentação oficial e às especificações OpenAPI da VTEX em tempo real.

| Tool | Descrição |
|------|-----------|
| `search_documentation` | Busca semântica no Developer Portal e Help Center |
| `fetch_document` | Recupera artigo completo por URL |
| `search_endpoints` | Busca endpoints nas definições OpenAPI |
| `get_endpoint_details` | Especificação OpenAPI completa de um endpoint |

Configurado em `.mcp.json`, carregado automaticamente ao abrir o Claude Code neste diretório.

## VTEX Skills (46)

Contexto persistente com regras e padrões específicos de cada área da plataforma.

| Categoria | Skills |
|-----------|--------|
| **Architecture** | `architecture-well-architected-commerce` |
| **FastStore** | `faststore-storefront` |
| **Headless** | `headless-bff-architecture`, `headless-caching-strategy`, `headless-checkout-proxy`, `headless-intelligent-search` |
| **Marketplace** | `marketplace-catalog-sync`, `marketplace-fulfillment`, `marketplace-order-hook`, `marketplace-rate-limiting` |
| **Master Data** | `masterdata-storage-strategy` |
| **Payment** | `payment-async-flow`, `payment-idempotency`, `payment-pci-security`, `payment-ppp-pos`, `payment-provider-framework`, `payment-provider-protocol` |
| **Sales App** | `sales-app-extensibility` |
| **VTEX IO** | `vtex-io-admin-react`, `vtex-io-app-contract`, `vtex-io-app-settings`, `vtex-io-application-performance`, `vtex-io-auth-and-policies`, `vtex-io-auth-tokens-and-context`, `vtex-io-client-integration`, `vtex-io-data-access-patterns`, `vtex-io-events-and-workers`, `vtex-io-graphql-api`, `vtex-io-http-routes`, `vtex-io-masterdata`, `vtex-io-masterdata-strategy`, `vtex-io-messages-and-i18n`, `vtex-io-observability-and-ops`, `vtex-io-rbac`, `vtex-io-react-apps`, `vtex-io-render-runtime-and-blocks`, `vtex-io-rootpath`, `vtex-io-security-boundaries`, `vtex-io-service-apps`, `vtex-io-service-configuration-apps`, `vtex-io-service-paths-and-cdn`, `vtex-io-service-runtime`, `vtex-io-session-apps`, `vtex-io-storefront-react`, `vtex-io-storefront-theme-app`, `vtex-io-storefront-theme-versioning` |

## Atualizar skills

```bash
npx skills add vtex/skills --all
```

## Referências

- [VTEX AI Developer Toolkit](https://developers.vtex.com/docs/guides/vtex-ai-developer-toolkit-overview)
- [VTEX Developer MCP](https://developers.vtex.com/docs/guides/vtex-developer-mcp)
- [VTEX Skills](https://developers.vtex.com/docs/guides/vtex-skills)
- [Claude Code](https://claude.ai/code)
