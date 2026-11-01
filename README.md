# CondoFlow

Sistema web de gestão condominial desenvolvido como protótipo acadêmico. O CondoFlow centraliza rotinas do condomínio em uma interface responsiva e adapta as ações disponíveis de acordo com o perfil de acesso.

## Funcionalidades

- Cadastro e gestão de condomínios, unidades, moradores e prestadores.
- Comunicados gerais ou urgentes, com notificações aos usuários.
- Autorização e acompanhamento de visitantes, com geração de QR Code.
- Registro e retirada de encomendas.
- Gestão de áreas comuns e reservas, incluindo consulta à agenda.
- Abertura, atribuição e acompanhamento de chamados de manutenção e ocorrências.
- Controle de acesso por perfil: síndico, morador, porteiro e prestador.
- Anexos, histórico de operações e alteração de senha.

## Tecnologias

- **Frontend:** HTML, CSS e JavaScript (ES modules).
- **Backend:** Node.js, Express e API REST.
- **Banco de dados:** MySQL.
- **Testes:** Node.js Test Runner.

O backend também demonstra os padrões Singleton, Chain of Responsibility e Template Method.

## Requisitos

- Node.js 22 ou superior.
- MySQL em execução e usuário com permissão para criar o banco de dados.

## Configuração e execução

1. Instale as dependências:

   ```bash
   npm install
   ```

2. Crie o arquivo `.env` a partir do exemplo:

   ```bash
   cp .env.example .env
   ```

3. Ajuste no `.env` as credenciais e configurações do seu MySQL:

   ```dotenv
   PORT=3000
   DB_HOST=localhost
   DB_PORT=3306
   DB_USER=root
   DB_PASSWORD=sua_senha_mysql
   DB_NAME=condoflow
   COOKIE_SECURE=false
   ```

   `COOKIE_SECURE=false` é adequado para execução local sem HTTPS. Em uma publicação com HTTPS, configure `COOKIE_SECURE=true`.

4. Crie a estrutura do banco e os dados de demonstração:

   ```bash
   npm run db:setup
   ```

   O comando cria o banco indicado por `DB_NAME`, caso ainda não exista. Em um banco vazio, carrega dados de demonstração e cinco contas; se já houver usuários, preserva os dados existentes e não reinsere a demonstração.

5. Inicie o servidor:

   ```bash
   npm start
   ```

   Acesse [http://localhost:3000](http://localhost:3000). Para usar outra porta, altere `PORT` no `.env`.

Durante o desenvolvimento, use `npm run dev` para iniciar o servidor com reinicialização automática.

## Contas de demonstração

As contas são criadas pelo `npm run db:setup` quando o banco está vazio. A senha inicial é `Condo@123`.

| Perfil | E-mail |
|---|---|
| Síndico | `sindico@condoflow.com` |
| Morador | `morador@condoflow.com` |
| Porteiro | `porteiro@condoflow.com` |
| Prestador | `prestador@condoflow.com` |
| Moradora | `ana@condoflow.com` |

Selecione na tela de login o perfil correspondente à conta. Os dados pré-carregados são fictícios e destinados à demonstração.

## Testes

Execute os testes automatizados:

```bash
npm test
```

Os testes de integração estão disponíveis separadamente e requerem o MySQL configurado e o banco preparado:

```bash
npm run test:integration
```

## Estrutura do projeto

```text
backend/
  database/      Esquema e dados iniciais do MySQL
  models/        Modelos e entidades
  patterns/      Implementações dos padrões de projeto
  scripts/       Preparação do banco de dados
  tests/         Testes unitários e de integração
  server.js      Aplicação Express e rotas da API
frontend/
  css/           Estilos
  html/          Telas do sistema
  js/            Lógica e configuração das telas
```
