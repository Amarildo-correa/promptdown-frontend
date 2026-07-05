# Componente: Ícone

## Descrição

Ícone vetorial (SVG) usado dentro de botões e células. Estilo de traço uniforme, sem preenchimento. Puramente visual — nunca captura o clique.

## Especificação (`.icon`)

| Propriedade        | Valor                 |
| ------------------ | --------------------- |
| Dimensão           | `18×18px`             |
| `stroke`           | `var(--muted)`        |
| `fill`             | `none`                |
| `stroke-width`     | `1.5`                 |
| `stroke-linecap`   | `round`               |
| `stroke-linejoin`  | `round`               |
| `pointer-events`   | `none`                |

## Exceção de traço

O ícone hambúrguer do menu usa `stroke-width="2"` (definido no próprio `<svg>`), levemente mais espesso que o padrão `1.5`.

## Inventário de ícones presentes

| Ícone            | Onde                | Significado          |
| ---------------- | ------------------- | -------------------- |
| Hambúrguer       | `.c-menu`           | Menu                 |
| Olho             | `.c-eye`            | Visualizar prompt    |
| Chevrons `<>`    | `.sb-item`          | Ver código-fonte     |
| Quadrado + `i`   | `.sb-item`          | Informações          |
| Duplo quadrado   | `.sb-item`          | Copiar prompt        |
| Balão            | `.sb-item`          | Comentar             |

> Os glifos `↑` e `↓` das setas de navegação são caracteres de texto, não SVGs. Ver [button.md](./button.md).

## Acessibilidade

`pointer-events: none` garante que o clique atravesse o ícone e seja capturado pela célula clicável. O significado acessível é fornecido pelo `aria-label` do botão que contém o ícone, não pelo SVG.
