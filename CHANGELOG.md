# Changelog

Todas as mudanças notáveis neste projeto são documentadas neste arquivo.

O formato é baseado em [Keep a Changelog](https://keepachangelog.com/pt-BR/1.0.0/),
e este projeto segue [Semantic Versioning](https://semver.org/lang/pt-BR/).

## [1.0.0] - 2026-07-04

### Adicionado
- API REST completa para gerenciamento de contratos
- Endpoints para CRUD de contratos (Create, Read, Update, Delete)
- Esquema OpenAPI 3.0.0 com documentação completa
- Suporte a autenticação via JWT (Bearer Token)
- Respostas estruturadas com código de erro e detalhes
- Sistema de paginação para listagem de contratos
- Versionamento de API (v1)
- Ambientes multi-stage (Development, Staging, Production)
- Validação de dados com esquemas JSON Schema
- Suporte a soft delete de contratos
- Metadados customizados para contratos
- Termos e condições com datas de vigência
- Exemplos de requisições e respostas

### Segurança
- Autenticação obrigatória em todos os endpoints
- Tokens JWT com expiration
- Validação de entrada em todos os campos
- Tratamento padronizado de erros

## [0.1.0] - 2026-07-04

### Adicionado
- Estrutura inicial do projeto
- Configuração base do repositório
- Documentação de arquitetura
