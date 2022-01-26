# Challenge 5: Connection pooling

[< Previous Challenge](./04-offline-cutover-validation.md) - **[Home](../README.md)**

## Introduction

Configure connection pooling for our database in Flexible Server.

## Description
In this challenge you will configure connection pooling to optimize the impact of having too many idle connections.

Postgres uses a process-based model for connections which makes it expensive to maintain many idle connections. So, Postgres itself runs into resource constraints once the server runs more than a few thousand connections. The primary benefit of PgBouncer is to improve idle connections and short-lived connections at the database server. PgBouncer uses a more lightweight model that utilizes asynchronous I/O, and only uses actual Postgres connections when needed, that is, when inside an open transaction, or when a query is active. This model can support thousands of connections more easily with low overhead and allows scaling to up to 10,000 connections with low overhead.

You will reconfigure the application to use a connection string that points to the Flexible Server. You will need to update ContosoPizza/values-postgresql.yaml values file with the updated values for dataSourceURL.

```yaml
appConfig:
  dataSourceURL: "jdbc url goes here" # your JDBC connection string goes here

  ```bash

helm upgrade --install postgres-contosopizza ./ContosoPizza -f ./ContosoPizza/values.yaml -f ./ContosoPizza/values-postgresql.yaml
kubectl -n contosoapppostgres rollout restart deployment contosopizza
```

Wait for a minute or two until the status field for the command of kubectl is  "Running" and "READY" state is "1/1".

Status field changes from "Terminating" to "ContainerCreating" and then to "Running".

```bash

 kubectl -n contosoapppostgres get pods

```

## Success Criteria

* Enable pbouncer and change your application's connection string. 

## Hints

* Use the general purpose or memory optimized version of Flexible Server


## References

* [PGBouncer and Azure Database for PostgreSQL - Flexible Server](https://docs.microsoft.com/en-us/azure/postgresql/flexible-server/concepts-pgbouncer)



