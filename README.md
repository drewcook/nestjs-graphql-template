# Web3 NestJS + GraphQL Template

## Description

[Nest](https://github.com/nestjs/nest) framework TypeScript starter repository. This also includes the added bells and whistles:

- TypeORM for working with a Postgres database
- GraphQL support
- Simple validation with `class-validator` + `class-transformer`
- An `account` entity with an Ethereum address field
- A `createAccount` mutation & `accounts` query
- Viem with custom scalars for Ethereum addresses and hashes
- A prettier logger with `nestjs-pino`
- A generic pagination and sorting service that can be applied to any entity
- Base entities setup using UUID strings as IDs
- A decimal transformer to store decimals as strings in the DB
- An optional but non-null decorator
- TSConfig/ESLint/Prettier wrangling
- Husky pre-commit hooks and conventional commit messages

## Installation

```bash
pnpm install
```

## Running the app

```bash
# development mode
$ pnpm run dev

# start without watcher
$ pnpm run start

# production mode
$ pnpm run start:prod

# lint with ESLint
$ pnpm lint

# format with Prettier
$ pnpm format
```

Then you can open up the GraphQL Playground and play with the `Account` types:

```graphql
mutation CreateNewAccount {
  createAccount(
    createAccountInput: {
      address: "0xEthereumAddress"
    }
  ) {
    id
    address
    createdAt
    updatedAt
  }
}

query GetAllAccounts {
  accounts(sort: { key: "address", asc: true }) {
    items {
      id
      address
      createdAt
      updatedAt
    }
    meta {
      currentPage
      itemCount
      itemType
      itemsPerPage
      totalItems
      totalPages
    }
  }
}
```

## Running Tests

```bash
# unit tests
$ pnpm run test

# e2e tests
$ pnpm run test:e2e

# test coverage
$ pnpm run test:cov
```
