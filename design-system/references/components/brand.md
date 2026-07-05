# Componente: Marca (Logo)

## Descrição

Identidade do produto no cabeçalho, composta por dois elementos independentes: o **selo em pixels** (à esquerda) e o **logotipo textual** (ao centro).

## Logotipo textual (`.c-brand`)

Palavra única em duas cores, sem espaço entre as partes.

| Parte    | Classe | Cor             | Tipografia                    |
| -------- | ------ | --------------- | ----------------------------- |
| `PROMPT` | `.pr`  | `#ffffff`       | Escala da marca (ver [tokens.md](../tokens.md)) |
| `DOWN`   | `.dw`  | `var(--accent)` | Escala da marca (ver [tokens.md](../tokens.md)) |

O `#ffffff` de `.pr` é a exceção literal documentada em [tokens.md](../tokens.md) (não há token para ele).

## Selo em pixels (`.c-logo`)

Malha `2×3` (2 colunas × 3 linhas) de blocos; `gap` e `padding` conforme o espaçamento do logo em [tokens.md](../tokens.md).

| Modificador | Classe   | Cor            |
| ----------- | -------- | -------------- |
| Escuro      | `.px`    | `var(--lo-b)`  |
| Médio       | `.px.a`  | `var(--lo-a)`  |
| Destaque    | `.px.hi` | `var(--accent)`|

Disposição dos 6 pixels (ordem no DOM):

```
[a ][  ]
[hi][a ]
[a ][  ]
```

## Markup de referência

```html
<div class="c-brand">
  <span class="pr">PROMPT</span><span class="dw">DOWN</span>
</div>
```

## Regras normativas (RFC 2119)

- O agente MUST NOT unificar as duas partes em uma cor só.
- O agente MUST NOT inserir espaço ou quebra entre `.pr` e `.dw`.
- O agente SHALL manter `#ffffff` em `.pr` e `var(--accent)` em `.dw`.

## Faça / Não faça

| ✅ Faça                                        | ❌ Não faça                              |
| --------------------------------------------- | ---------------------------------------- |
| Manter as duas cores do logotipo (`#ffffff` + `--accent`) | Unificar a marca em uma cor só |
| Preservar a proporção `2×3` do selo           | Aplicar sombra ou gradiente aos pixels   |

## Relacionados

- Cores em [tokens.md](../tokens.md).
