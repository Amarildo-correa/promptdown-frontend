# Design Tokens

> Fonte da verdade dos valores atômicos do Design System.
> Todos os tokens são declarados em `:root` de `promptdown.html` como CSS Custom Properties.
> Nenhum outro arquivo deve repetir valores literais (hex, px) — referencie o nome do token.

## Cor

Paleta única, base escura. Não há tema alternativo (ver [themes.md](./themes.md)).

| Token      | Valor      | Papel                                                                 |
| ---------- | ---------- | --------------------------------------------------------------------- |
| `--bg`     | `#090d18`  | Fundo global. Único fundo da interface — não há fundos de sobreposição.|
| `--bd`     | `#1c2f4a`  | Borda divisória. Estrutura todo o mosaico (ver mosaic-grid).           |
| `--text`   | `#c8d8ec`  | Texto primário e ícone do menu.                                        |
| `--muted`  | `#4e6a8e`  | Texto secundário (autor), setas e traço dos ícones SVG.               |
| `--accent` | `#44b2e2`  | Cor de destaque: marca, sintaxe markdown, avatar.                     |
| `--lo-a`   | `#2b4e8a`  | Pixel médio do logo.                                                  |
| `--lo-b`   | `#0f1e34`  | Pixel escuro do logo.                                                 |

Regras de cor herdadas do brief:
- Apenas cores sólidas. Sem gradiente.
- Sem sombra.
- A divisão entre blocos é feita **somente por borda** (`--bd`), nunca por cor de fundo.

### Cor literal fora de token

| Valor      | Uso                                    | Observação                          |
| ---------- | -------------------------------------- | ----------------------------------- |
| `#ffffff`  | Palavra "PROMPT" da marca              | Contraste máximo contra `--accent`. |

## Dimensão / Alvo de toque

Tokens que controlam a malha e as áreas clicáveis (mobile-first).

| Token      | Valor  | Papel                                                              |
| ---------- | ------ | ------------------------------------------------------------------ |
| `--touch`  | `56px` | Altura padrão de qualquer célula clicável. Base do alvo de toque.  |
| `--header` | `68px` | Altura do cabeçalho (logo e menu).                                 |
| `--side`   | `56px` | Largura das colunas laterais (rail de ícones, célula do avatar).   |

Justificativa do `56px`: WCAG 2.5.5 exige mínimo `44×44px`. Como os botões são adjacentes e separados apenas por borda (sem espaçamento), o alvo é elevado para `56px` para evitar toque duplo acidental. Ver [components/button.md](./components/button.md).

### Tokens com valor idêntico — regra normativa (RFC 2119)

`--touch` e `--side` valem `56px` cada, mas têm papéis distintos. Um agente que os trate como intercambiáveis quebrará a semântica de layout.

| Token     | SHALL ser usado para                        | MUST NOT ser usado para              |
| --------- | ------------------------------------------- | ------------------------------------ |
| `--touch` | `height` de qualquer célula clicável        | `width` de coluna ou pixel do logo   |
| `--side`  | `width` das colunas laterais (rail, avatar) | `height` de qualquer elemento        |

## Tipografia

Fonte única, monoespaçada, reforçando a estética de terminal.

| Token conceitual   | Valor                                | Uso                          |
| ------------------ | ------------------------------------ | ---------------------------- |
| Família            | `'Courier New', Courier, monospace`  | Toda a interface.            |

### Escala de tamanho

| Tamanho | Peso | Line-height | Letter-spacing | Aplicação                        |
| ------- | ---- | ----------- | -------------- | -------------------------------- |
| `17px`  | bold | —           | `2px`          | Marca (PROMPTDOWN).              |
| `15px`  | bold | `1.55`      | —              | Título do card (`h1`).          |
| `13px`  | —    | `1.9`       | —              | Corpo do prompt / markdown.      |
| `13px`  | bold | —           | —              | Letra do avatar.                 |
| `13px`  | —    | —           | —              | Cabeçalho markdown (`# Objetivo`).|
| `12px`  | —    | —           | `0.2px`        | Metadados do autor.              |
| `18px`  | —    | —           | —              | Setas de navegação (↑ ↓).        |

## Borda

Não há `border-radius` na estrutura de layout. Cantos retos são intencionais.

| Token conceitual | Valor                  | Uso                                  |
| ---------------- | ---------------------- | ------------------------------------ |
| Divisória        | `1px solid var(--bd)`  | Todas as divisões do mosaico.        |
| Avatar           | `1.5px solid var(--accent)` | Contorno do quadrado do avatar. |

> Os atributos `rx` presentes nos SVGs pertencem ao desenho interno dos ícones e **não** são tokens de raio da interface.

## Espaçamento

Não há escala de espaçamento tokenizada; os valores são aplicados diretamente por bloco.

| Valor       | Aplicação                                  |
| ----------- | ------------------------------------------ |
| `18px 14px` | Padding do título e do corpo do prompt.    |
| `12px 10px` | Padding do logo em pixels.                 |
| `0 14px`    | Padding horizontal dos metadados do autor. |
| `7px`       | Gap entre traço e texto nos itens de lista.|
| `3px`       | Gap entre os pixels do logo.               |

## Elevação e Movimento

- **Sombra:** nenhuma.
- **Gradiente:** nenhum.
- **Transição:** nenhuma declarada.
- **Feedback de toque:** alteração de `opacity` no estado `:active` (ver button.md).
- `touch-action: manipulation` aplicado aos elementos clicáveis para remover o atraso de 300ms.
