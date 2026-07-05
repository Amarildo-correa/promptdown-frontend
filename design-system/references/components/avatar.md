# Componente: Avatar

## Descrição

Marcador quadrado de identidade do autor, exibindo uma inicial. Ocupa a célula lateral esquerda da linha do autor.

## Especificação (`.avatar-sq`)

| Propriedade   | Valor                        |
| ------------- | ---------------------------- |
| Dimensão      | `32×32px`                    |
| Borda         | `1.5px solid var(--accent)`  |
| Cor da letra  | `var(--accent)`              |
| Tipografia    | `13px`, bold, monoespaçada   |
| Alinhamento   | `flex` + center              |
| Fundo         | nenhum (herda `--bg`)        |
| Raio          | nenhum (quadrado)            |

## Conteúdo

Uma única letra maiúscula derivada do nome do autor (`N` para `@nicolly_dev`).

## Acessibilidade

A letra é decorativa (`aria-hidden="true"`), pois a identidade já é fornecida em texto pela célula de metadados do autor (`.c-author-info`). Evita leitura redundante em leitores de tela.

## Relacionados

- Cor e tipografia em [tokens.md](../tokens.md).
