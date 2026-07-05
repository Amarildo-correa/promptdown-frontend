# Convenções

> Convenções de CSS, nomenclatura e estrutura efetivamente observadas em `promptdown.html`.

## Tokens antes de valores

Todos os valores de cor e dimensão vêm de CSS Custom Properties declaradas em `:root`. Componentes consomem `var(--token)` em vez de literais. Ver [tokens.md](./tokens.md).

Exceções literais documentadas:
- `#ffffff` na palavra "PROMPT".
- Valores de tipografia e espaçamento aplicados por bloco (não tokenizados).

## Nomenclatura de classes

O CSS usa prefixos por responsabilidade. Não é BEM estrito; é um sistema de namespaces curtos.

| Prefixo   | Significado           | Exemplos                                             |
| --------- | --------------------- | ---------------------------------------------------- |
| `c-`      | Célula do cabeçalho / linha do autor | `.c-logo`, `.c-brand`, `.c-menu`, `.c-avatar`, `.c-author-info`, `.c-eye` |
| `sb-`     | Sidebar (rail lateral) | `.sb-item`, `.sb-arrow`, `.sb-spacer`              |
| `md-`     | Conteúdo markdown     | `.md-h1`, `.md-p`, `.md-code`, `.md-strong`, `.md-list`, `.md-dash`, `.md-li-text` |
| `px`      | Pixel do logo         | `.px`, `.px.a`, `.px.hi`                              |

Blocos estruturais usam nomes semânticos sem prefixo: `.app`, `.header`, `.author-row`, `.body-grid`, `.content-col`, `.sidebar-col`, `.title-block`, `.body-block`, `.icon`, `.avatar-sq`.

Modificadores são classes adicionais aplicadas ao lado da base (`.px.a`, `.px.hi`), não sufixos.

## Estrutura de layout

- Layout construído com **CSS Grid** nas seções em faixa (header, author-row, body-grid) e **Flexbox** nas colunas empilhadas (`.app`, `.sidebar-col`, `.content-col`).
- Divisão visual feita exclusivamente por borda (`1px solid var(--bd)`). Ver [layout/mosaic-grid.md](./layout/mosaic-grid.md).
- Sem `border-radius` na estrutura. Cantos retos.

## Mobile-first

- `<meta viewport>` com `width=device-width, initial-scale=1.0, user-scalable=no`.
- Unidade `100svh` para altura total considerando a barra dinâmica do navegador móvel.
- `-webkit-text-size-adjust: 100%` para impedir reajuste de fonte no iOS.
- Alvos de toque de `56px` (ver tokens.md).

## Reset

Reset local mínimo no topo da folha:

```css
*, *::before, *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

## Acessibilidade (convenção)

- Todo elemento clicável recebe `role="button"`, `tabindex="0"` e `aria-label` descritivo.
- Ícones puramente visuais recebem `pointer-events: none` (o clique é capturado pela célula) e, quando decorativos, `aria-hidden="true"`.
- Ver notas por componente em [components/button.md](./components/button.md).
