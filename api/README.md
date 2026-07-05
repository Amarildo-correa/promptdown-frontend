# Promptdown Contracts API — Especificação OpenAPI

Especificação OpenAPI da API de Contratos do Promptdown. **Estágio inicial (WIP)**: este repositório contém o esqueleto e o roadmap da especificação, funcionando como fonte de verdade centralizada para consumidores.

## Visão Geral

Este repositório é a **fonte de verdade** para o contrato da API de Contratos. Serve como ponto único de referência para:

- Definição formal da interface via OpenAPI 3.0.3
- Histórico de mudanças e versionamento (CHANGELOG)
- Comunicação clara entre equipes sobre evolução da especificação

Consumidores (frontends, serviços, clientes) integram este repositório em suas bases de código via **git subtree** (prefixo `api/`) de forma somente-leitura, garantindo que todas as implementações sigam a mesma especificação.

## Estado Atual

A especificação está no **estágio inicial**, contendo apenas:

- [x] Informações básicas da API (título, versão 1.0.0, descrição)
- [x] Referência oficial da [Especificação OpenAPI 3.0.3](https://spec.openapis.org/oas/v3.0.3)
- [ ] Nenhum endpoint implementado
- [ ] Nenhum schema de dados definido
- [ ] Nenhuma securityScheme configurada
- [ ] Nenhum exemplo de requisição/resposta

## Estrutura do Projeto

```
.
├── openapi.yaml          # Especificação OpenAPI 3.0.0 (esqueleto + roadmap)
├── README.md            # Este arquivo
├── CHANGELOG.md         # Histórico de versões (formato Keep a Changelog)
├── examples/            # [VAZIO] Exemplos de requisições e respostas (futuro)
└── errors/              # [VAZIO] Documentação de códigos de erro (futuro)
```

## Próximos Passos (Roadmap)

Implementação planejada em fases futuras:

### Fase 1: Definição de Ambiente

- [ ] `servers`: URLs dos ambientes (Production, Staging, Development)
- [ ] `security`: Configuração de autenticação obrigatória

### Fase 2: Endpoints e Operações

- [ ] `paths`: Endpoints CRUD para contratos
    - `GET /contracts` — Listar contratos
    - `POST /contracts` — Criar contrato
    - `GET /contracts/{id}` — Obter contrato específico
    - `PATCH /contracts/{id}` — Atualizar contrato
    - `DELETE /contracts/{id}` — Deletar contrato

### Fase 3: Dados e Schemas

- [ ] `components/schemas`: Modelos de dados
    - Contract (entidade principal)
    - CreateContractRequest / UpdateContractRequest (payloads)
    - Error (resposta de erro padronizada)
    - Pagination (metadados de listagem)
- [ ] `components/responses`: Respostas padrão (200, 400, 401, 404, 422, 500)
- [ ] `components/securitySchemes`: Autenticação Bearer Token (JWT)

### Fase 4: Recursos e Documentação

- [ ] Exemplos em `examples/`: Requisições e respostas reais
- [ ] Documentação de erros em `errors/`: Catálogo de códigos de erro
- [ ] Guias de integração e versionamento

### Detalhes de Implementação

- **Autenticação**: Bearer Token JWT obrigatório em todos os endpoints
- **Paginação**: Suporte a listagem com limite, offset e metadados
- **Validação**: Schemas JSON Schema com validação de entrada rigorosa
- **Soft Delete**: Exclusão lógica de contratos (campo `deletedAt`)
- **Metadados**: Campos customizados para extensibilidade (`metadata` object)
- **Versionamento**: API em `/v1`, preparada para futuras versões

## Consumidores

Repositórios consumidores (aplicações, serviços, clientes) integram este contrato via **git subtree**:

```bash
git subtree add --prefix api https://github.com/Amarildo-correa/promptdown-contracts.git main
```

Isso coloca a especificação completa em `api/` de forma **somente-leitura**. Sempre que há atualizações aqui, consumidores fazem:

```bash
git subtree pull --prefix api https://github.com/Amarildo-correa/promptdown-contracts.git main
```

**Importante**: A fonte de verdade é **sempre este repositório**. Nunca edite cópias da especificação no lado dos consumidores — edições devem ser feitas aqui e propagadas para frente.

## Contribuindo

Este repositório é a fonte-da-verdade para o contrato da API. Mudanças na especificação seguem este fluxo:

1. **Edite** `openapi.yaml` com as mudanças na especificação
2. **Documente** o que mudou no `CHANGELOG.md`, seguindo [Keep a Changelog](https://keepachangelog.com/pt-BR/1.0.0/)
3. **Versione** conforme [Semantic Versioning](https://semver.org/lang/pt-BR/) (`MAJOR.MINOR.PATCH`)
4. **Envie** pull request para revisão
5. **Merge** aprovado atualiza a fonte de verdade e todos os consumidores fazem `git subtree pull`

### Validação

Antes de fazer push, valide o YAML:

```bash
# Instale um validador OpenAPI (ex.: Swagger CLI)
swagger-cli validate openapi.yaml
```

## Referências

- [OpenAPI 3.0.3 Specification](https://spec.openapis.org/oas/v3.0.3) — Documentação oficial
- [Keep a Changelog](https://keepachangelog.com/pt-BR/1.0.0/) — Formato de changelog
- [Semantic Versioning](https://semver.org/lang/pt-BR/) — Esquema de versionamento
- [Git Subtree](https://git-scm.com/book/en/v2/Git-Tools-Subtrees) — Integração em consumidores
