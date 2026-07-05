# Layout: Mosaico de Blocos

> Elemento de assinatura de `promptdown.html`. Toda a interface é uma malha de células retangulares divididas **apenas por borda**, sem cor de fundo de separação.

## Princípio

- Um único fundo (`--bg`) para toda a tela.
- A separação entre células é feita exclusivamente por `1px solid var(--bd)`.
- Sem preenchimento de fundo nas sobreposições, sem sombra, sem gradiente.
- Cantos retos (sem `border-radius`).

## Rails fixos

As colunas laterais têm largura fixa; a coluna central é fluida (`1fr`).

| Rail                      | Token      | Valor  |
| ------------------------- | ---------- | ------ |
| Coluna lateral            | `--side`   | `56px` |
| Altura header             | `--header` | `68px` |
| Altura de célula clicável | `--touch`  | `56px` |

## Estrutura vertical (`.app`)

Container flex em coluna, com borda externa `1px solid var(--bd)` e altura mínima `100svh`:

```
┌─────────────────────────────────────┐
│ .header        (grid 56 | 1fr | 56)  │  68px
├─────────────────────────────────────┤
│ .author-row    (grid 56 | 1fr | 56)  │  56px
├──────────────────────────┬──────────┤
│ .content-col             │ .sidebar │
│   .title-block           │  -col    │
│   .body-block            │  (rail)  │  1fr (cresce)
│                          │          │
└──────────────────────────┴──────────┘
```

## Grids em faixa

| Seção         | `grid-template-columns` | Células                   |
| ------------- | ----------------------- | ------------------------- |
| `.header`     | `56px 1fr 56px`         | logo · marca · menu       |
| `.author-row` | `56px 1fr 56px`         | avatar · info · olho      |
| `.body-grid`  | `1fr 56px`              | conteúdo · rail de ícones |

## Regras de borda

- `.header`, `.author-row`: `border-bottom`.
- Células internas (`.c-logo`, `.c-brand`, `.c-avatar`, `.c-author-info`, `.content-col`): `border-right`.
- Itens do rail (`.sb-item`): `border-bottom`; setas (`.sb-arrow`): `border-top`.
- Espaçador (`.sb-spacer`): cresce (`flex-grow: 1`) empurrando as setas para o rodapé e mantém `border-bottom`.

O resultado é que cada célula fica cercada sem duplicar linhas: bordas são atribuídas em um único sentido por vizinhança.

## Relacionados

- Valores em [tokens.md](../tokens.md).
- Convenções de nomenclatura em [conventions.md](../conventions.md).
