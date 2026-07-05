| Caminho         | Tipo    | Descrição                                   |
| --------------- | ------- | ------------------------------------------- |
| `README.md`     | Arquivo | Visão geral, setup e comandos.              |
| `AGENTS.md`     | Arquivo | Instruções e regras para agentes de IA.     |
| `package.json`  | Arquivo | Scripts (JSON Server, servidor estático).   |
| `.gitignore`    | Arquivo | Arquivos e diretórios ignorados pelo Git.   |
| `.editorconfig` | Arquivo | Consistência de formatação entre editores.  |
| `.env.example`  | Arquivo | Exemplo de configuração da URL base da API. |

## `api/`

| Caminho            | Tipo    | Descrição                                   |
| ------------------ | ------- | ------------------------------------------- |
| `api/db.json`      | Arquivo | Registros permanentes (JSON Server).        |
| `api/routes.json`  | Arquivo | Rewrites de rotas do JSON Server.           |
| `api/openapi.yaml` | Arquivo | Contrato OpenAPI (fonte da verdade da API). |

## `public/`

| Caminho                 | Tipo      | Descrição             |
| ----------------------- | --------- | --------------------- |
| `public/favicon.svg`    | Arquivo   | Favicon da aplicação. |
| `public/assets/images/` | Diretório | Imagens estáticas.    |
| `public/assets/icons/`  | Diretório | Ícones da aplicação.  |
| `public/assets/fonts/`  | Diretório | Fontes tipográficas.  |

## `src/`

### Entrada

| Caminho          | Tipo    | Descrição                 |
| ---------------- | ------- | ------------------------- |
| `src/index.html` | Arquivo | Entry point único da SPA. |

### `src/styles/`

| Caminho                            | Tipo    | Descrição                                                      |
| ---------------------------------- | ------- | -------------------------------------------------------------- |
| `src/styles/main.css`              | Arquivo | Orquestrador contendo apenas `@import` na ordem correta.       |
| `src/styles/settings/tokens.css`   | Arquivo | Design Tokens (`--color-*`, `--space-*`, `--font-*`).          |
| `src/styles/settings/themes.css`   | Arquivo | Temas claro/escuro via `[data-theme]`.                         |
| `src/styles/base/reset.css`        | Arquivo | Normalização cross-browser.                                    |
| `src/styles/base/typography.css`   | Arquivo | Escala tipográfica global.                                     |
| `src/styles/layout/grid.css`       | Arquivo | Containers e grid utilitário.                                  |
| `src/styles/layout/page.css`       | Arquivo | Estrutura da página (header, main e footer).                   |
| `src/styles/components/button.css` | Arquivo | Estilos de botões.                                             |
| `src/styles/components/form.css`   | Arquivo | Estilos de formulários.                                        |
| `src/styles/components/table.css`  | Arquivo | Estilos de tabelas.                                            |
| `src/styles/components/modal.css`  | Arquivo | Estilos de modais.                                             |
| `src/styles/components/toast.css`  | Arquivo | Estilos de notificações.                                       |
| `src/styles/utilities/helpers.css` | Arquivo | Classes utilitárias (`.visually-hidden`, `.is-loading`, etc.). |

### `src/js/`

#### Bootstrap

| Caminho          | Tipo    | Descrição                                                |
| ---------------- | ------- | -------------------------------------------------------- |
| `src/js/main.js` | Arquivo | Bootstrap da aplicação (único `<script type="module">`). |

#### Configuração

| Caminho                      | Tipo    | Descrição                                      |
| ---------------------------- | ------- | ---------------------------------------------- |
| `src/js/config/constants.js` | Arquivo | Constantes globais (API, endpoints, timeouts). |

#### Services

| Caminho                              | Tipo    | Descrição                                                 |
| ------------------------------------ | ------- | --------------------------------------------------------- |
| `src/js/services/http.js`            | Arquivo | Wrapper do `fetch` (headers, erros e JSON).               |
| `src/js/services/records.service.js` | Arquivo | CRUD (`getAll`, `getById`, `create`, `update`, `remove`). |

#### Components

| Caminho                            | Tipo    | Descrição                          |
| ---------------------------------- | ------- | ---------------------------------- |
| `src/js/components/RecordForm.js`  | Arquivo | Formulário de criação e edição.    |
| `src/js/components/RecordTable.js` | Arquivo | Tabela de listagem com ações.      |
| `src/js/components/Modal.js`       | Arquivo | Modal de confirmação.              |
| `src/js/components/Toast.js`       | Arquivo | Feedback visual de sucesso e erro. |

#### State

| Caminho                 | Tipo    | Descrição                         |
| ----------------------- | ------- | --------------------------------- |
| `src/js/state/store.js` | Arquivo | Estado central simples (Pub/Sub). |

#### Utils

| Caminho                      | Tipo    | Descrição                        |
| ---------------------------- | ------- | -------------------------------- |
| `src/js/utils/dom.js`        | Arquivo | Helpers para manipulação do DOM. |
| `src/js/utils/validators.js` | Arquivo | Validação de formulários.        |
| `src/js/utils/formatters.js` | Arquivo | Datas, moeda e máscaras.         |

### `src/pages/`

| Caminho                             | Tipo    | Descrição                                                         |
| ----------------------------------- | ------- | ----------------------------------------------------------------- |
| `src/pages/records/records.page.js` | Arquivo | View da página de registros (caso evolua para múltiplas páginas). |

## `tests/`

### Unit

| Caminho                         | Tipo    | Descrição                          |
| ------------------------------- | ------- | ---------------------------------- |
| `tests/unit/validators.test.js` | Arquivo | Testes unitários das validações.   |
| `tests/unit/formatters.test.js` | Arquivo | Testes unitários dos formatadores. |

### Integration

| Caminho                                     | Tipo    | Descrição                                   |
| ------------------------------------------- | ------- | ------------------------------------------- |
| `tests/integration/records.service.test.js` | Arquivo | Testes de integração da camada de serviços. |

## `design-system/`

### Entrada

| Caminho                   | Tipo    | Descrição                              |
| ------------------------- | ------- | -------------------------------------- |
| `design-system/DESIGN.md` | Arquivo | Visão geral e índice do Design System. |

### References

| Caminho                                   | Tipo    | Descrição                             |
| ----------------------------------------- | ------- | ------------------------------------- |
| `design-system/references/tokens.md`      | Arquivo | Especificação dos Design Tokens.      |
| `design-system/references/themes.md`      | Arquivo | Regras para temas claro/escuro.       |
| `design-system/references/conventions.md` | Arquivo | Convenções CSS, nomenclatura e ITCSS. |

### Componentes

| Caminho                                         | Tipo    | Descrição                                |
| ----------------------------------------------- | ------- | ---------------------------------------- |
| `design-system/references/components/button.md` | Arquivo | Botões (estados, variantes e tamanhos).  |
| `design-system/references/components/form.md`   | Arquivo | Inputs, labels e estados de validação.   |
| `design-system/references/components/table.md`  | Arquivo | Tabelas, cabeçalhos, linhas e paginação. |
| `design-system/references/components/modal.md`  | Arquivo | Modais e gerenciamento de foco.          |
| `design-system/references/components/toast.md`  | Arquivo | Notificações temporárias.                |

### Patterns

| Caminho                                                   | Tipo    | Descrição                                      |
| --------------------------------------------------------- | ------- | ---------------------------------------------- |
| `design-system/references/patterns/crud-form-flow.md`     | Arquivo | Fluxo visual de criação e edição de registros. |
| `design-system/references/patterns/confirmation-modal.md` | Arquivo | Padrão UX para confirmação de exclusão.        |
| `design-system/references/patterns/feedback-toast.md`     | Arquivo | Fluxo de feedback utilizando toasts.           |
