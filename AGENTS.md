# AGENTS.md

Contexto de carregamento único para agentes de IA neste repositório. Referências detalhadas ficam em `design-system/references/` e são carregadas sob demanda.

## Projeto

O repositório `promptdown-frontend` é um **multirepo** dedicado exclusivamente ao desenvolvimento do frontend da aplicação PromptDown.

Este repositório contém apenas a interface da aplicação, incluindo páginas, componentes, estilos, gerenciamento de estado e integração com a API por meio de um contrato. Toda a comunicação com o backend é realizada através da `API_BASE_URL`, mantendo o frontend desacoplado da implementação do servidor.

O contrato da API é sincronizado para `api/` a partir do repositório oficial de contratos. A sincronização é **automatizada via GitHub Actions** ([`.github/workflows/sync-contract.yml`](.github/workflows/sync-contract.yml)), que executa um **Git Subtree** pull agendado/sob demanda — basta um `git pull` neste repositório para obter a revisão correspondente. O agente MUST NOT editar `api/` manualmente para "corrigir" o contrato; alterações de contrato pertencem ao repositório de origem (proteção reforçada por [`.github/CODEOWNERS`](.github/CODEOWNERS)).

Fallback manual (quando necessário rodar localmente): `git subtree pull --prefix=api contracts main --squash` (nunca `add` — o subtree já existe).
Remote ausente? `git remote add contracts https://github.com/Amarildo-correa/promptdown-contracts.git`.

## Estado atual do repositório

Estágio de **scaffolding + documentação**, não de implementação:

- Todos os arquivos em `src/` (JS e CSS) e `public/favicon.svg` existem mas estão **vazios** — placeholders da árvore de arquivos planejada, não código funcional.
- Todos os arquivos em `tests/` estão **vazios**.
- `package.json` está **vazio** (sem scripts, sem dependências declaradas ainda).
- O conteúdo real e atual do projeto vive em `design-system/references/` (documentação do Design System) e `api/openapi.yaml` (contrato via subtree).

O agente MUST conferir se o arquivo correspondente tem conteúdo antes de assumir que uma função, componente ou estilo existe — a árvore de diretórios sozinha não é evidência de implementação.

## Arquitetura alvo (quando implementada)

O inventário completo de arquivos e responsabilidades é [`.specs/project/STRUCTURE.md`](.specs/project/STRUCTURE.md) (fonte da verdade). Pontos de entrada essenciais:

| Caminho                          | Responsabilidade                                  |
| -------------------------------- | ------------------------------------------------- |
| `src/index.html`                 | Entry point único da SPA.                         |
| `src/js/main.js`                 | Bootstrap (único `<script type="module">`).       |
| `src/styles/settings/tokens.css` | Design Tokens (fonte da verdade dos valores CSS). |
| `api/openapi.yaml`               | Contrato da API (somente leitura — via subtree).  |
| `design-system/DESIGN.md`        | Índice do Design System.                          |

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
