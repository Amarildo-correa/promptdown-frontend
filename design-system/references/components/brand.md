# Componente: Marca (Logo)

## Descrição

Identidade do produto no cabeçalho, composta por dois elementos independentes: o **selo em pixels** (à esquerda) e o **logotipo textual** (ao centro).

## Logotipo textual (`.c-brand`)

Palavra única em duas cores, sem espaço entre as partes.

| Parte    | Classe | Cor             | Tipografia               |
| -------- | ------ | --------------- | ------------------------ |
| `PROMPT` | `.pr`  | `#ffffff`       | `17px`, bold, `letter-spacing: 2px` |
| `DOWN`   | `.dw`  | `var(--accent)` | `17px`, bold, `letter-spacing: 2px` |

## Selo em pixels (`.c-logo`)

Malha `2×3` (2 colunas × 3 linhas) de blocos, `gap: 3px`, padding `12px 10px`.

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

## Faça / Não faça

| ✅ Faça                                        | ❌ Não faça                              |
| --------------------------------------------- | ---------------------------------------- |
| Manter as duas cores do logotipo (`#ffffff` + `--accent`) | Unificar a marca em uma cor só |
| Preservar a proporção `2×3` do selo           | Aplicar sombra ou gradiente aos pixels   |

## Relacionados

- Cores em [tokens.md](../tokens.md).
