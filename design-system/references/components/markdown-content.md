# Componente: Conteúdo Markdown

## Descrição

Bloco que exibe o texto do prompt preservando a **sintaxe markdown visível** (`#`, crases, `**`, `-`) e colorindo os marcadores com a cor de destaque. Não é markdown renderizado: os símbolos permanecem à vista, reforçando a estética de editor de código.

Vive em `.body-block` (padding `18px 14px`, fonte `13px`, `line-height: 1.9`).

## Elementos

| Classe        | Papel                                  | Cor             |
| ------------- | -------------------------------------- | --------------- |
| `.md-h1`      | Cabeçalho (`# Objetivo`)               | `var(--accent)` |
| `.md-p`       | Parágrafo                              | `var(--text)`   |
| `.md-code`    | Trecho inline entre crases (`` `x` ``) | `var(--text)`   |
| `.md-strong`  | Ênfase entre `**` (`**escalável**`)    | `var(--accent)` |
| `.md-list`    | Lista sem marcador nativo              | —               |
| `.md-dash`    | Traço `-` do item                      | `var(--accent)` |
| `.md-li-text` | Texto do item de lista                 | `var(--accent)` |

## Estrutura da lista

`.md-list` remove o marcador nativo (`list-style: none`). Cada item é `flex` com `gap: 7px`, unindo um traço (`.md-dash`) e o texto (`.md-li-text`). O traço é literal, não gerado por CSS.

## Regras

- A sintaxe markdown é conteúdo literal, não deve ser interpretada/renderizada.
- Marcadores estruturais (`#`, `-`, `**`) e cabeçalho recebem `--accent`; prosa recebe `--text`.
- `.md-code` mantém `--text` (não recebe destaque de cor), diferenciando-se apenas pelas crases visíveis.

## Relacionados

- Escala tipográfica em [tokens.md](../tokens.md).
