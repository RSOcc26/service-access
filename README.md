# service-access

Access service: which apps each company and user may use, and with which role.

Part of **CompanyHub**, a multi-tenant, cloud-native microservices platform
built for the *Cloud Computing Services* course (RSO 2026/27, FRI UL).
See the [RSOcc26 organization](https://github.com/RSOcc26) for the other services.

> **Status:** scaffold — no implementation yet.

## Responsibilities

- Registry of the apps on the platform
- Which apps each company has enabled
- Per-user app access and roles
- Access groups that grant roles to many users at once

## Data ownership

This service owns its own PostgreSQL database; no other service reads or
writes it directly. Each company (tenant) gets its own schema.

Owns: apps, company apps, user apps, access groups.

## API

| Interface | Description |
|---|---|
| REST API | _To be defined._ The OpenAPI document will be served at `/api-docs`. |
| Health | `/health/live` and `/health/ready` for Kubernetes probes. |
| Metrics | `/metrics` in Prometheus format. |

## Events

| Direction | Event | Description |
|---|---|---|
| Publishes | _To be defined._ | |
| Consumes | _To be defined._ | |

## Configuration

All configuration comes from environment variables (see `.env.example`
once it exists). Secrets are never committed; in Kubernetes they come from
Secrets, everything else from ConfigMaps.

| Variable | Required | Description |
|---|---|---|
| _To be defined._ | | |

## Getting started

Prerequisites: Node.js 24 (see `.nvmrc`), Docker, and a PostgreSQL instance.

_Commands will be added with the first implementation._

## Project structure

```
src/
  api/          HTTP routes, request validation, OpenAPI document
  domain/       business rules, independent of HTTP and storage
  data/         database access (repositories, queries)
  events/       event publishers and consumers
  config/       configuration loading and validation
migrations/     versioned database migrations
test/
  unit/         fast tests with no external dependencies
  integration/  tests against a real database
docs/
  adr/          architecture decision records
```

## Deployment

Built as a container image and published to GitHub Container Registry.
Kubernetes manifests and Helm charts live in the deployment repository.

## Contributing

- Branch from `main` (`feat/…`, `fix/…`, `chore/…`) and open a pull request.
- Commit messages follow [Conventional Commits](https://www.conventionalcommits.org/).
- Pull requests need a review from a code owner and passing checks; they are squash-merged.
- Record notable changes in `CHANGELOG.md`.
