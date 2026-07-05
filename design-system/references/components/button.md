# Componente: Botão de Ícone

## Descrição

Célula quadrada clicável contendo um único ícone ou glifo centralizado. É o único tipo de botão presente em `promptdown.html`. Não há botão com rótulo textual. A área clicável é a **célula inteira** do mosaico, não o ícone.

## Variantes

Todas compartilham o mesmo modelo (célula centralizada + alvo de toque + borda + estado `:active`). Diferem em posição, glifo e dimensão.

| Variante         | Classe      | Dimensão  | Conteúdo         | Rótulo (`aria-label`)   |
| ---------------- | ----------- | --------- | ---------------- | ----------------------- |
| Menu             | `.c-menu`   | `56×68px` | Ícone hambúrguer | "Menu"                  |
| Visualizar       | `.c-eye`    | `56×56px` | Ícone olho       | "Visualizar prompt"     |
| Ação (rail)      | `.sb-item`  | `56×56px` | Ícone SVG        | Ação específica\*       |
| Navegação (seta) | `.sb-arrow` | `56×56px` | Glifo `↑` / `↓`  | "Rolar para cima/baixo" |

\* Ações do rail presentes: "Ver código-fonte" (`<>`), "Informações" (`ⓘ`), "Copiar prompt" (duplo quadrado), "Comentar" (balão).

## Propriedades

| Propriedade    | Valor no arquivo       | Descrição                                         |
| -------------- | ---------------------- | ------------------------------------------------- |
| Alvo de toque  | `--touch` / `--header` | Mínimo `56px`; menu tem `68px` de altura.         |
| Alinhamento    | `flex` + center        | Ícone centralizado nos dois eixos.                |
| Borda          | `1px solid var(--bd)`  | Separação no mosaico; sentido conforme a posição. |
| `touch-action` | `manipulation`         | Remove atraso de 300ms.                           |

## Estados

Não há `hover` (mobile-first). Não há estado desabilitado no arquivo.

| Estado    | Visual                        | Comportamento                |
| --------- | ----------------------------- | ---------------------------- |
| Default   | Ícone em `--muted` / `--text` | —                            |
| `:active` | `opacity` reduzida            | Feedback de pressão ao toque |

Valores de `opacity` no `:active`:

| Variante                | `opacity` |
| ----------------------- | --------- |
| `.c-menu`, `.c-eye`     | `0.6`     |
| `.sb-item`, `.sb-arrow` | `0.55`    |

## Acessibilidade

- **Role:** `role="button"` em todas as variantes.
- **Teclado:** `tabindex="0"` torna cada botão focável na ordem do DOM.
- **Leitor de tela:** anunciado pelo `aria-label` correspondente.
- **Ícone:** `pointer-events: none` no SVG garante que o clique seja registrado na célula inteira; ver [icon.md](./icon.md).

## Dimensionamento do alvo (WCAG 2.5.5)

O mínimo de `44×44px` é elevado para `56px` porque os botões são adjacentes e separados apenas por borda, sem espaçamento de respiro. Isso evita que a polpa do dedo acione dois botões vizinhos. Token: `--touch`. Ver [tokens.md](../tokens.md).

## Faça / Não faça

| ✅ Faça                                    | ❌ Não faça                                        |
| ------------------------------------------ | -------------------------------------------------- |
| Manter a célula inteira como área clicável | Restringir o clique apenas ao ícone                |
| Fornecer `aria-label` para cada botão      | Deixar botão de ícone sem rótulo acessível         |
| Manter altura mínima `--touch` (56px)      | Reduzir o alvo abaixo de 56px em botões adjacentes |
| Usar `:active` para feedback               | Introduzir sombra ou gradiente no estado           |
