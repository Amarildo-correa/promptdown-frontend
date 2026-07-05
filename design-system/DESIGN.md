# Design System — PromptDown

Documentação do Design System extraída de `promptdown.html`. Cada arquivo tem responsabilidade única; valores literais vivem apenas em `tokens.md` e são referenciados pelos demais.

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

Documenta **apenas** o que existe em `promptdown.html`. Os arquivos abaixo fazem parte da estrutura do repositório mas **não têm correspondência** no arquivo atual e foram mantidos vazios:

| Documento vazio                             | Motivo                                                     |
| ------------------------------------------- | ---------------------------------------------------------- |
| `references/themes.md`                      | Não há tema claro/escuro nem `[data-theme]`; paleta única. |
| `references/components/form.md`             | Não há formulários.                                        |
| `references/components/table.md`            | Não há tabelas.                                            |
| `references/components/modal.md`            | Não há modais.                                             |
| `references/components/toast.md`            | Não há notificações.                                       |
| `references/patterns/crud-form-flow.md`     | Não há fluxo CRUD.                                         |
| `references/patterns/confirmation-modal.md` | Não há modal de confirmação.                               |
| `references/patterns/feedback-toast.md`     | Não há toasts.                                             |

Documentos criados fora da estrutura original, por representarem conceitos presentes no arquivo e ainda não contemplados: `layout/mosaic-grid.md`, `components/icon.md`, `components/avatar.md`, `components/brand.md`, `components/markdown-content.md`.
