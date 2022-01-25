# FastHack - Postgres migration
## Introduction
This intro level hackathon will help you get hands-on experience migrating databases from on-premises PostgreSQL to Azure DB for PostgreSQL Flexible Server.

## Learning Objectives
In this hack you will solve a common challenge for companies migrating to the cloud: migrating open source databases to Azure. The application using the database is a sample e-commerce [application](https://github.com/pzinsta/pizzeria) written in Java. It will be configured to use PostgreSQL.

The participants will learn how to:

1. Perform a pre-migration assessment of the databases looking at size, database engine type, database version, etc.
1. Use offline tools to copy the databases to Flexible Server
1. Use the Azure Database Migration Service to perform an online migration
1. Do cutover and validation to ensure the application is working properly with the new configuration

## Challenges
- Challenge 0: **[Pre-requisites - Setup Environment and Prerequisites!](Student/00-prereqs.md)**
   - Prepare your environment to run the sample application
- Challenge 1: **[Assessment (features differences and compatibility)](Student/01-assessment.md)**
   - Assess the application's PostgreSQL databases
- Challenge 2: **[Size analysis](Student/02-size-analysis.md)**
   - Determine the CPU/memory configuration and database file size and map to an equivalent size in Azure
- Challenge 3: **[Offline migration](Student/03-offline-migration.md)**
   - Dump the "on-prem" databases, create databases for Azure DB for PostgreSQL and restore them
- Challenge 4: **[Offline Cutover and Validation](Student/04-offline-cutover-validation.md)**
   - Reconfigure the application to use the appropriate connection string and validate that the application is working
- Challenge 5: **[Online Migration](Student/05-online-migration.md)**
   - Create new databases in Azure DB for PostgreSQL and use the Azure Database Migration Service to replicate the data from the on-prem databases


## Prerequisites

- Access to an Azure subscription with Owner access
   - If you don't have one, [Sign Up for Azure HERE](https://azure.microsoft.com/en-us/free/)
   - Familiarity with Azure Cloud Shell
- [Azure Data Sudio](https://docs.microsoft.com/en-us/sql/azure-data-studio/download-azure-data-studio?view=sql-server-ver15) (optional)


