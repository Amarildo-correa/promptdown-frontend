# Design System — PromptDown

Cada arquivo tem responsabilidade única; valores literais vivem apenas em `tokens.md` e são referenciados pelos demais.

## Produto

O produto-alvo é o **admin CRUD de _records_** do PromptDown (ver `.specs/codebase/STRUCTURE.md` e `src/js/`). O Design System descrito aqui é a **fundação visual** desse produto: a estética de terminal e o layout em mosaico definem a base sobre a qual os componentes de CRUD (formulário, tabela, modal, toast) serão construídos. O mosaico é, portanto, um **caso de layout** — não o produto inteiro.

## Fundamentos

Estética de terminal, mobile-first. Fundo escuro único, cor sólida (sem gradiente), sem sombra. A interface é um **mosaico de blocos** dividido somente por bordas. Fonte monoespaçada em toda a tela.

## Índice

### Referências base

| Documento                                                | Responsabilidade                                                               |
| -------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [references/tokens.md](./references/tokens.md)           | Cor, dimensão/alvo de toque, tipografia, borda, espaçamento. Fonte da verdade. |
| [references/conventions.md](./references/conventions.md) | Nomenclatura de classes, grid, mobile-first, reset, acessibilidade.            |

### Layout

| Documento                                                              | Responsabilidade                                  |
| ---------------------------------------------------------------------- | ------------------------------------------------- |
| [references/layout/mosaic-grid.md](./references/layout/mosaic-grid.md) | Malha de células dividida por borda (assinatura). |

### Componentes

| Documento                                                                                | Responsabilidade                                     |
| ---------------------------------------------------------------------------------------- | ---------------------------------------------------- |
| [references/components/button.md](./references/components/button.md)                     | Botões de ícone (variantes, estados, alvo de toque). |
| [references/components/icon.md](./references/components/icon.md)                         | Especificação dos ícones SVG.                        |
| [references/components/avatar.md](./references/components/avatar.md)                     | Marcador de identidade do autor.                     |
| [references/components/brand.md](./references/components/brand.md)                       | Logotipo textual e selo em pixels.                   |
| [references/components/markdown-content.md](./references/components/markdown-content.md) | Exibição do prompt com sintaxe markdown visível.     |

## Escopo desta documentação

Documenta **apenas** o que já existe implementado (hoje, a fundação de layout extraída de `promptdown.html`). Os arquivos abaixo compõem o Design System do produto CRUD mas estão **vazios porque ainda não há UI correspondente implementada** — devem ser preenchidos junto com a implementação (guardrail em `AGENTS.md`: documentar só o que existe no código):

| Documento vazio                             | Motivo                                                                                     |
| ------------------------------------------- | ------------------------------------------------------------------------------------------ |
| `references/themes.md`                      | Tema claro/escuro (`[data-theme]`) planejado; ainda não implementado (paleta única atual). |
| `references/components/form.md`             | Formulário do CRUD planejado; ainda não implementado.                                      |
| `references/components/table.md`            | Tabela de registros planejada; ainda não implementada.                                     |
| `references/components/modal.md`            | Modal de confirmação planejado; ainda não implementado.                                    |
| `references/components/toast.md`            | Notificações planejadas; ainda não implementadas.                                          |
| `references/patterns/crud-form-flow.md`     | Fluxo CRUD planejado; ainda não implementado.                                              |
| `references/patterns/confirmation-modal.md` | Padrão de confirmação planejado; ainda não implementado.                                   |
| `references/patterns/feedback-toast.md`     | Fluxo de feedback via toast planejado; ainda não implementado.                             |

Documentos criados fora da estrutura original, por representarem conceitos presentes no arquivo e ainda não contemplados: `layout/mosaic-grid.md`, `components/icon.md`, `components/avatar.md`, `components/brand.md`, `components/markdown-content.md`.
