# Componente: Avatar

## Descrição

Marcador quadrado de identidade do autor, exibindo uma inicial. Ocupa a célula lateral esquerda da linha do autor.

## Especificação (`.avatar-sq`)

| Propriedade   | Valor                                          |
| ------------- | ---------------------------------------------- |
| Dimensão      | `32×32px`                                      |
| Borda         | Borda do avatar em [tokens.md](../tokens.md)   |
| Cor da letra  | `var(--accent)`                                |
| Tipografia    | Escala (letra do avatar) em [tokens.md](../tokens.md) |
| Alinhamento   | `flex` + center                                |
| Fundo         | nenhum (herda `--bg`)                          |
| Raio          | nenhum (quadrado)                              |

## Conteúdo

Uma única letra maiúscula derivada do nome do autor (`N` para `@nicolly_dev`).

## Acessibilidade

A letra é decorativa (`aria-hidden="true"`), pois a identidade já é fornecida em texto pela célula de metadados do autor (`.c-author-info`). Evita leitura redundante em leitores de tela.

## Markup de referência

```html
<div class="c-avatar">
  <div class="avatar-sq" aria-hidden="true">N</div>
</div>
```

## Regras normativas (RFC 2119)

- O agente MUST manter `aria-hidden="true"` na letra, pois a identidade já é dada em texto por `.c-author-info`.
- O agente MUST NOT aplicar `border-radius` (o avatar é quadrado, não circular).

## Relacionados

- Cor e tipografia em [tokens.md](../tokens.md).
