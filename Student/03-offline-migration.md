# Challenge 3: Offline migration of database

[< Previous Challenge](./02-size-analysis.md) - **[Home](../README.md)** - [Next Challenge >](./04-offline-cutover-validation.md)

## Introduction

Deploy an appropriate PostgreSQL Flexible Server based on what you determined and observed in previous challenges and then copy the Pizzeria database(s) to Azure. 
You are not required to reconfigure the application to Azure DB for PostgreSQL in this challenge as you will do that in the next one. 

## Description

In the offline migration approach, your application can tolerate some downtime to move to Azure. You can assume that the application is down and no changes are being made to the database. You will need to take into account the size analysis you performed in Challenge 2 and choose the appropriate database server tier and deployment option. 

## Success Criteria

* You have chosen the proper compute + storage tier based on the sizing analysis you performed in an earlier challenge
* You have created a PostgreSQL Flexible Server instance. 
* You have created a separate "wth" database
* You have a user called "contosoapp" with the same privileges that it has on the source database
* You have migrated the on premises database.

## Hints

* You can do the import/export from within the containers for PostgreSQL QL that you created in the prereqs. Alternatively, if the database copy tools are installed on your machine, you can connect to the database from your computer as well. 
* You are free to choose Database Migration Service or pg_dump / pg_restore.

# Steps

* Create a Flexible Server and use connect from a client.
* Run CREATE DATABASE wth;
* Switch to wth database and run CREATE ROLE contosoapp WITH LOGIN NOSUPERUSER INHERIT CREATEDB CREATEROLE NOREPLICATION PASSWORD 'OCPHack8';

* From Cloud Shell connect to your on premise Postgres, kubectl -n postgresql exec deploy/postgres -it -- bash
* su - postgres
* pg_dump wth | psql -h <yourserver>.postgres.database.azure.com -p 5432 -U contosoapp wth
* If you face permission errors with contosoapp user, run ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT SELECT,INSERT,UPDATE,DELETE ON TABLES TO contosoapp;


## References
* [Create an Azure Database for PostgreSQL server](https://docs.microsoft.com/en-us/azure/postgresql/flexible-server/quickstart-create-server-portal)
* [Migrate your PostgreSQL database using export and import](https://docs.microsoft.com/en-us/azure/postgresql/howto-migrate-using-dump-and-restore)

 
