<img alt="icon" src=".alixea/icon.svg" width="32">

# PostgreSQL add-on for Alixea

PostgreSQL with the [pgvector](https://github.com/pgvector/pgvector) extension. It uses the image
[pgvector/pgvector](https://hub.docker.com/r/pgvector/pgvector), which is the official
[postgres](https://hub.docker.com/_/postgres) image with pgvector added.

## pgvector

The extension is installed but not turned on. Turn it on in a database as the add-on's superuser (`POSTGRES_USER`):

```sql
CREATE EXTENSION IF NOT EXISTS vector;
```

Only a superuser can do this. The Odoo component does it for Odoo's database by itself.

## Release a new version

1. Change the image in `.alixea/helm/postgres.yaml`. Keep the `-trixie` ending of the tag.
2. Commit, push, and tag the commit `v<PostgreSQL version>`, such as `v18.7`.
3. Turn the version on for the add-on on the platform's admin **Components** page.

A move inside PostgreSQL 18, such as 18.3 to 18.7, keeps the data as it is. A new major version, such as 19, needs
the data moved over, which this add-on does not do.
