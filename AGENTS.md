# AGENTS.md

Contexto de carregamento único para agentes de IA neste repositório. Referências detalhadas ficam em `design-system/references/` e são carregadas sob demanda.

## Projeto

O repositório `promptdown-frontend` é um **multirepo** dedicado exclusivamente ao desenvolvimento do frontend da aplicação PromptDown.

Este repositório contém apenas a interface da aplicação, incluindo páginas, componentes, estilos, gerenciamento de estado e integração com a API por meio de um contrato. Toda a comunicação com o backend é realizada através da `API_BASE_URL`, mantendo o frontend desacoplado da implementação do servidor.

O contrato da API é sincronizado para `api/` a partir do repositório oficial de contratos. A sincronização é **automatizada via GitHub Actions** ([`.github/workflows/sync-contract.yml`](.github/workflows/sync-contract.yml)), que executa um **Git Subtree** pull agendado/sob demanda — basta um `git pull` neste repositório para obter a revisão correspondente. O agente MUST NOT editar `api/` manualmente para "corrigir" o contrato; alterações de contrato pertencem ao repositório de origem (proteção reforçada por [`.github/CODEOWNERS`](.github/CODEOWNERS)).

Fallback manual (quando necessário rodar localmente): `git subtree pull --prefix=api contracts main --squash` (nunca `add` — o subtree já existe).
Remote ausente? `git remote add contracts https://github.com/Amarildo-correa/promptdown-contracts.git`.

## Estado atual do repositório

Estágio de **scaffolding + documentação**, não de implementação. Status detalhado (o que está vazio,
por quê, decisões recentes e todos pendentes) vive em [`.specs/project/STATE.md`](.specs/project/STATE.md)
— consulte antes de assumir que uma função, componente ou estilo existe: a árvore de diretórios
sozinha não é evidência de implementação.

## Estrutura do repositório

Árvore ASCII completa e atual (todo arquivo versionado, mais os diretórios vazios de `public/assets/`) —
única fonte da árvore neste repositório, não reproduzida em nenhum outro documento. Anotações inline
marcam só o que precisa de atenção imediata (vazio, somente leitura, entry point); justificativas e
ressalvas mais longas ficam em tabela em [`.specs/codebase/STRUCTURE.md`](.specs/codebase/STRUCTURE.md).
Status de implementação (o que está vazio e por quê) vive em [`.specs/project/STATE.md`](.specs/project/STATE.md).

```
.
├── .editorconfig
├── .env.example
├── .gitignore
├── .github/
│   ├── CODEOWNERS                          # protege api/ (revisão obrigatória)
│   └── workflows/
│       └── sync-contract.yml               # sincroniza api/ via Git Subtree
├── .specs/
│   ├── project/
│   │   └── STATE.md                        # memória: decisões, status, todos
│   └── codebase/
│       └── STRUCTURE.md                    # regras de organização, ressalvas
├── .vscode/
│   ├── markdown-preview.css
│   └── settings.json
├── AGENTS.md                               # este arquivo — contexto único p/ agentes de IA
├── CLAUDE.md                               # ponteiro para AGENTS.md
├── README.md
├── package.json
├── package-lock.json
├── api/                                    # somente leitura — sync automático, não editar
│   ├── CHANGELOG.md
│   └── openapi.yaml                        # stub — a expandir pelo repo de contratos
├── design-system/
│   ├── DESIGN.md                           # índice do Design System
│   └── references/
│       ├── tokens.md
│       ├── themes.md                       # vazio
│       ├── conventions.md
│       ├── layout/
│       │   └── mosaic-grid.md
│       ├── components/
│       │   ├── button.md
│       │   ├── icon.md
│       │   ├── avatar.md
│       │   ├── brand.md
│       │   ├── markdown-content.md
│       │   ├── form.md                     # vazio
│       │   ├── table.md                    # vazio
│       │   ├── modal.md                    # vazio
│       │   └── toast.md                    # vazio
│       └── patterns/
│           ├── crud-form-flow.md           # vazio
│           ├── confirmation-modal.md       # vazio
│           └── feedback-toast.md           # vazio
├── public/
│   ├── favicon.svg                         # vazio
│   └── assets/                             # vazio, sem arquivos ainda
│       ├── images/
│       ├── icons/
│       └── fonts/
├── src/                                    # tudo abaixo é placeholder vazio (scaffolding)
│   ├── index.html                          # entry point único da SPA
│   ├── js/
│   │   ├── main.js                         # bootstrap (único <script type="module">)
│   │   ├── config/
│   │   │   └── constants.js
│   │   ├── services/
│   │   │   ├── http.js                     # wrapper genérico de fetch
│   │   │   └── records/
│   │   │       └── records.service.js
│   │   ├── components/
│   │   │   ├── RecordForm.js
│   │   │   ├── RecordTable.js
│   │   │   ├── Modal.js
│   │   │   └── Toast.js
│   │   ├── state/
│   │   │   └── store.js
│   │   └── utils/
│   │       ├── dom.js
│   │       ├── validators.js
│   │       └── formatters.js
│   ├── pages/
│   │   └── records/
│   │       └── records.page.js
│   └── styles/
│       ├── main.css                        # orquestrador (@import na ordem ITCSS)
│       ├── settings/
│       │   ├── tokens.css                  # Design Tokens — fonte da verdade dos valores CSS
│       │   └── themes.css
│       ├── base/
│       │   ├── reset.css
│       │   └── typography.css
│       ├── layout/
│       │   ├── grid.css
│       │   └── page.css
│       ├── components/
│       │   ├── button.css
│       │   ├── form.css
│       │   ├── table.css
│       │   ├── modal.css
│       │   └── toast.css
│       └── utilities/
│           └── helpers.css
└── tests/                                  # vazio — sem runner configurado ainda p/ rodar
    ├── unit/
    │   ├── validators.test.js
    │   └── formatters.test.js
    └── integration/
        └── records.service.test.js
```

O CSS segue ITCSS (`settings → base → layout → components → utilities`, via `@import` em `src/styles/main.css`). Convenções de arquitetura vanilla aplicáveis quando o roteamento/SPA for implementado: roteamento via History API (`pushState`/`popstate`, nunca hash routing); views retornam um contrato de lifecycle (`{ destroy }` ou `null`) e limpam subscriptions antes de trocar de view; `import()` dinâmico sempre com string literal estática.

## Design System — guardrails

> Índice e especificação completa em [`design-system/DESIGN.md`](design-system/DESIGN.md). Valores atômicos (cor, dimensão, tipografia) vivem **apenas** em [`tokens.md`](design-system/references/tokens.md); prefixos de classe e o texto normativo das proibições, em [`conventions.md`](design-system/references/conventions.md). Carregue esses arquivos ao gerar CSS/HTML.
>
> O bloco abaixo é um **resumo derivado** — as travas que os LLMs mais violam. Em caso de divergência, a fonte acima prevalece.

O agente MUST NOT, ao gerar código do frontend:

- usar `background-color` diferente de `var(--bg)` em qualquer célula do mosaico (a separação é só por borda);
- usar `box-shadow`, gradiente (`linear-gradient`/`radial-gradient`/`conic-gradient`) ou `border-radius` em células do layout / `.app`;
- reduzir `height` de célula clicável abaixo de `var(--touch)` (56px);
- criar classes fora dos prefixos `c-` / `sb-` / `md-` / `px` sem antes documentar o novo prefixo em `conventions.md`;
- renderizar markdown no corpo do prompt — os símbolos (`#`, `**`, `` ` ``, `-`) MUST permanecer como texto literal.

Token ambíguo: `--touch` e `--side` valem ambos `56px` mas NÃO são intercambiáveis — `--touch` SHALL ser usado só para `height` de célula clicável; `--side`, só para `width` de coluna lateral.

## Escopo de escrita

O agente MUST documentar apenas o que existe no código. MUST NOT inventar componentes, tokens ou padrões. Arquivos de referência vazios (`themes.md`, `form.md`, `table.md`, `modal.md`, `toast.md`, `patterns/*`) MUST permanecer vazios enquanto não houver conteúdo correspondente no frontend.
