# Sacra Telegram Bot

Sacra Telegram Bot is a TypeScript Telegram bot for Sacra referral/community
flows. It reads Sacra subgraph data, stores bot/user state in Postgres, and uses
database migrations managed by Knex.

## Tech Stack

- Node.js 18
- TypeScript
- node-telegram-bot-api
- Apollo Client
- GraphQL Code Generator
- Knex
- PostgreSQL
- Docker and Docker Compose

## Repository Layout

- `src/bot.ts` - bot entry point.
- `src/db/` - database access layer.
- `src/models/` - application models.
- `src/graphql/` - generated GraphQL types/helpers.
- `src/utils/` - shared utilities.
- `gql/` - GraphQL queries and codegen configuration.
- `migrations/` - Knex database migrations.
- `knex-config.ts` - database migration configuration.
- `.env_example` - required environment variable example.
- `Dockerfile` and `docker-compose.yml` - containerized runtime setup.

## Configuration

Create `.env` from the example:

```bash
cp .env_example .env
```

Required variables:

```dotenv
SACRA_TELEGRAM_BOT_TOKEN=your_token
SACRA_LINK=https://sonic-beta.sacra.cc/
SUBGRAPH_URL=url
SACRA_GUIDE_LINK=https://docs.sacra.cc/sacra-whitepaper/
DB_HOST=localhost
DB_NAME=my_database
DB_USER=my_user
DB_PASSWORD=my_password
DB_PORT=5432
```

Do not commit real bot tokens or database credentials.

## Install

```bash
yarn install
```

## Build

```bash
yarn build
```

The production build runs GraphQL code generation, TypeScript compilation, and
production database migrations.

For staging/development migration settings:

```bash
yarn build:dev
```

## Start

```bash
yarn start
```

For development settings:

```bash
yarn start:dev
```

## Migrations

```bash
yarn migration
yarn rollback
```

Development variants:

```bash
yarn migration:dev
yarn rollback:dev
```

## Docker

```bash
docker compose up --build -d
```

The compose file starts Postgres and the bot service on a shared Docker network.
