# State

**Last Updated:** 2026-07-06
**Current Work:** Nenhuma feature em implementação — repositório em estágio de **scaffolding + documentação**.

---

## Recent Decisions (Last 60 days)

### AD-001: Sincronização de `api/` automatizada via GitHub Actions + CODEOWNERS (2026-07-05)

**Decisão:** `api/` (contrato OpenAPI) passa a ser sincronizada por
[`.github/workflows/sync-contract.yml`](../../.github/workflows/sync-contract.yml) (Git Subtree
agendado/sob demanda), em vez de só um comando manual documentado em `AGENTS.md`. Proteção reforçada
por [`.github/CODEOWNERS`](../../.github/CODEOWNERS), exigindo revisão em qualquer PR que toque `api/`.
**Reason:** a spec de arquitetura do repo exige sync automática via GitHub Actions; o processo manual
divergia disso e já havia um caso de edição manual de `api/` (remoção de `api/README.md`) no histórico.
**Trade-off:** nenhum custo relevante — o comando manual de subtree continua documentado como fallback.
**Impact:** `api/` deve ser tratado como somente leitura; qualquer mudança de contrato vem do repositório
`promptdown-contracts`, nunca editada localmente.

### AD-002: Remoção do JSON Server do plano de scaffolding (2026-07-05)

**Decisão:** não haverá mock de API (JSON Server, `db.json`/`routes.json`) dentro deste repositório,
nem dentro nem fora de `api/`.
**Reason:** `api/` deve ser cópia somente-leitura do contrato; um mock server com banco de dados local
contraria os MUST NOT de backend/banco de dados da arquitetura do frontend. Confirmado pela decisão
posterior de que o backend real será um multirepo separado (ver AD-006).
**Trade-off:** sem backend real rodando, não é possível testar o CRUD ponta a ponta no navegador
(alternativas futuras: MSW ou fixtures estáticas, se necessário).
**Impact:** `src/js/services/records/records.service.js` deve assumir sempre um backend real via
`API_BASE_URL`, nunca um mock local.

### AD-003: Produto-alvo é o CRUD de _records_ (2026-07-05)

**Decisão:** o produto implementado neste frontend é o **admin CRUD de records** (`RecordForm`,
`RecordTable`, `Modal`, `Toast`), não o visualizador de prompts em estilo "terminal/mosaico" que o
Design System documentava originalmente.
**Reason:** havia duas visões de produto conflitantes no repo (Design System descrevia um visualizador
read-only; `STRUCTURE.md`/`src/js` descreviam um CRUD). Precisavam ser reconciliadas em uma só.
**Trade-off:** nenhum — a estética de terminal/mosaico é preservada como **fundação visual** (tokens,
malha de células, tipografia monoespaçada); os componentes de CRUD serão desenhados sobre essa base,
não a substituem.
**Impact:** `design-system/DESIGN.md` foi reenquadrado (mosaico = base de layout, não produto final);
os docs vazios de `form.md`/`table.md`/`modal.md`/`toast.md`/`patterns/*` são "a implementar", não
"não se aplica".

### AD-004: `src/js/services/` organizado por domínio (2026-07-05)

**Decisão:** `services/` segue organização por domínio (`records/records.service.js`), espelhando o
padrão já usado em `src/pages/records/records.page.js`. `http.js` é exceção e fica na raiz de
`services/` por ser wrapper genérico de `fetch`, compartilhado por todos os domínios.
**Reason:** consistência com um padrão já estabelecido no próprio repo (`pages/records/`), não
antecipação de domínios futuros inexistentes.
**Trade-off:** nenhum — custo é só um nível extra de pasta.
**Impact:** ao criar um segundo domínio (ex.: `prompts`), replicar o mesmo padrão em ambas as árvores
(`pages/prompts/` e `services/prompts/`).

### AD-005: Árvore de diretórios vive só em `AGENTS.md` (2026-07-06)

**Decisão:** a árvore ASCII completa do repositório é mantida em um único lugar
([`AGENTS.md`](../../AGENTS.md#estrutura-do-repositório)). `STRUCTURE.md` não a reproduz — contém
apenas tabelas para casos que precisam de explicação mais longa (regras, justificativas de
organização).
**Reason:** manter duas árvores (uma em cada arquivo) é redundante e consome desnecessariamente a
janela de contexto de agentes de IA.
**Trade-off:** nenhum.
**Impact:** qualquer atualização estrutural do repo deve ser refletida primeiro em `AGENTS.md`.

### AD-006: Backend será um multirepo separado (2026-07-06)

**Decisão:** o backend do PromptDown (Node.js + PostgreSQL em Docker) será construído em um
repositório separado, comunicando com este frontend exclusivamente via o contrato
`api/openapi.yaml` (sincronizado de `promptdown-contracts`, ver AD-001).
**Reason:** confirma e reforça a arquitetura já auditada — `promptdown-frontend` deve ser só arquivos
estáticos de frontend, sem nenhuma peça de backend/banco de dados.
**Trade-off:** para testar o CRUD end-to-end no navegador é necessário ter o backend rodando
localmente (ou um mock externo a este repo) — não há mock embutido aqui (ver AD-002).
**Impact:** ao sugerir testes de integração com API, assumir o backend real via `API_BASE_URL`, nunca
um mock dentro deste repositório.

---

## Active Blockers

_Nenhum blocker ativo no momento._

---

## Lessons Learned

_Nenhuma lição registrada ainda._

---

## Status de scaffolding (placeholders vazios)

Estágio de **scaffolding + documentação**, não de implementação. Antes de assumir que uma função,
componente ou estilo existe, confira se o arquivo correspondente tem conteúdo — a árvore de
diretórios sozinha não é evidência de implementação.

| Área                                                                  | Motivo do vazio                                                        |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| Todo `src/**` (JS e CSS)                                              | Scaffolding — árvore planejada, sem código funcional ainda.            |
| Todo `tests/**`                                                       | Scaffolding — sem testes escritos nem suíte com casos reais ainda.     |
| `public/favicon.svg`                                                  | Placeholder de scaffolding.                                            |
| `design-system/references/themes.md`                                  | Tema claro/escuro ainda não implementado no CRUD de _records_.        |
| `design-system/references/components/{form,table,modal,toast}.md`    | Componentes do CRUD ainda não implementados.                          |
| `design-system/references/patterns/*`                                 | Fluxos que dependem dos componentes acima — ainda não implementados.   |
| `api/openapi.yaml`                                                    | Stub — a expandir no repositório `promptdown-contracts` (upstream).   |

Esses arquivos **devem permanecer vazios** enquanto não houver conteúdo correspondente no frontend
(guardrail em `AGENTS.md` → "Escopo de escrita": não documentar/inventar componentes inexistentes).

---

## Quick Tasks Completed

| #   | Description                                                              | Date       | Commit | Status  |
| --- | ------------------------------------------------------------------------- | ---------- | ------ | ------- |
| 001 | Auditoria de conformidade arquitetural + correções (sync, .env, DS, etc.) | 2026-07-05 | —      | ✅ Done |
| 002 | Reorganização de `services/` por domínio                                 | 2026-07-05 | —      | ✅ Done |
| 003 | Árvore ASCII em AGENTS.md + enxugamento de STRUCTURE.md                  | 2026-07-06 | —      | ✅ Done |

---

## Deferred Ideas

- [ ] Criar `.specs/project/PROJECT.md` (visão, metas, escopo) — gap real de AI-First, fora do escopo
      desta correção de `.specs/`.
- [ ] Criar `.specs/project/ROADMAP.md` (features/milestones).
- [ ] Avaliar MSW ou fixtures estáticas para testar o CRUD sem depender do backend real rodando.
- [ ] Expandir `api/openapi.yaml` no repositório `promptdown-contracts` (paths, schemas, security).

---

## Todos

- [ ] Implementar `src/js/services/http.js` e `records/records.service.js` (camada de comunicação).
- [ ] Implementar UI (componentes, páginas, estado, roteamento SPA).
- [ ] Escrever testes reais em `tests/unit/` e `tests/integration/` (hoje vazios — gate falha por
      "No test suite found").
