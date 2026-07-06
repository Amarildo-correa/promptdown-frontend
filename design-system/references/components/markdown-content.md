# Componente: Conteúdo Markdown

## Descrição

Bloco que exibe o texto do prompt preservando a **sintaxe markdown visível** (`#`, crases, `**`, `-`) e colorindo os marcadores com a cor de destaque. Não é markdown renderizado: os símbolos permanecem à vista, reforçando a estética de editor de código.

Vive em `.body-block` (padding, escala tipográfica e `line-height` em [tokens.md](../tokens.md)).

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

`.md-list` remove o marcador nativo (`list-style: none`). Cada item é `flex`, unindo um traço (`.md-dash`) e o texto (`.md-li-text`) com o `gap` definido em [tokens.md](../tokens.md). O traço é literal, não gerado por CSS.

## Regras

- A sintaxe markdown é conteúdo literal, não deve ser interpretada/renderizada.
- Marcadores estruturais (`#`, `-`, `**`) e cabeçalho recebem `--accent`; prosa recebe `--text`.
- `.md-code` mantém `--text` (não recebe destaque de cor), diferenciando-se apenas pelas crases visíveis.

## Markup de referência

```html
<div class="body-block">
  <p class="md-h1"># Objetivo</p>
  <p class="md-p">
    Texto com <span class="md-code">`inline code`</span> e
    <span class="md-strong">**ênfase**</span>.
  </p>
  <ul class="md-list">
    <li><span class="md-dash">-</span><span class="md-li-text">Item</span></li>
  </ul>
</div>
```

## Regras normativas (RFC 2119)

Esta é a zona de maior risco de alucinação: o LLM tende a renderizar markdown em vez de exibi-lo.

- O agente MUST NOT renderizar markdown; os símbolos (`#`, `**`, `` ` ``, `-`) MUST aparecer como texto literal.
- O agente MUST NOT usar `<h1>`–`<h6>` para cabeçalhos; SHALL usar `<p class="md-h1">`.
- O agente MUST NOT usar `<strong>` ou `<em>` para ênfase; SHALL usar `<span class="md-strong">`.
- O agente MUST NOT usar `<code>` para trecho inline; SHALL usar `<span class="md-code">` mantendo as crases visíveis.
- O agente MUST manter `list-style: none` em `.md-list`; o traço `-` SHALL ser texto literal em `.md-dash`, nunca marcador nativo.

## Relacionados

- Escala tipográfica em [tokens.md](../tokens.md).
