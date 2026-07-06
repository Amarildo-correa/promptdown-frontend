# Estrutura do projeto

Este arquivo **não** repete a árvore de diretórios — ela vive em um único lugar,
[`AGENTS.md`](../../AGENTS.md#estrutura-do-repositório), para evitar duas árvores redundantes
consumindo janela de contexto. Aqui ficam apenas fatos **estruturais estáticos**: regras de
organização e ressalvas que não cabem num comentário inline da árvore.

> Status de implementação (o que está vazio/scaffolding e por quê) é **estado**, não estrutura —
> vive em [`.specs/project/STATE.md`](../project/STATE.md).

## `api/` — somente leitura

| Regra           | Descrição                                                                                                                                                                                               |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Somente leitura | O agente **MUST NOT** editar, criar ou remover arquivos em `api/` manualmente — alterações de contrato pertencem ao repositório de origem (`promptdown-contracts`).                                     |
| Sincronização   | Automatizada via [`.github/workflows/sync-contract.yml`](../../.github/workflows/sync-contract.yml) (Git Subtree, agendado/sob demanda). Basta `git pull` neste repo para obter a revisão mais recente. |
| Proteção        | [`.github/CODEOWNERS`](../../.github/CODEOWNERS) exige revisão obrigatória em qualquer PR que toque `api/`.                                                                                             |

## `src/js/services/` — organização por domínio

| Item               | Regra                                                                                                                                                 |
| ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| Pasta por entidade | Uma subpasta por domínio (`records/`, futuramente `prompts/` etc.), espelhando o padrão já usado em `src/pages/`.                                     |
| `http.js`          | Exceção — fica na raiz de `services/` por ser o wrapper genérico de `fetch`, compartilhado por todos os domínios, não específico de nenhuma entidade. |

Detalhe por componente do Design System: [`design-system/DESIGN.md`](../../design-system/DESIGN.md).
