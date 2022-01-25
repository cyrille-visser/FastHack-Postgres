# Challenge 1: Assessment 

[< Previous Challenge](./00-prereqs.md) - **[Home](../README.md)** - [Next Challenge >](./02-size-analysis.md)

## Introduction

Make sure your database is ready to move.

## Description

In this challenge you'll be connecting to your "on-prem" environment using the database tools you installed in the prerequisites. You will take an inventory of the databases that need to be migrated, check the database versions, check the database engine and determine if they are ready to migrate to Azure. 

* To validate the version, run SELECT version();
* To validate the database size, run SELECT pg_size_pretty( pg_database_size('wth'));
* To validate whether extensions are supported, run SELECT name, installed_version FROM pg_available_extensions WHERE installed_version IS NOT NULL;

## Success Criteria

* You have connected to the "on-prem" databases using the database tools and taken an inventory of the databases - the database version, size, schema objects, dependency between schema objects.
* You have verified that the "on-prem" database versions and size are supported in Azure DB for PostgreSQL
* You have checked for any other compatibility of the database that needs to resolve before migrating it to Azure - for specific compatibilty issues, refer to the Limitations pages below.

## References

* [Limitations in Flexible Server](https://docs.microsoft.com/en-us/azure/postgresql/flexible-server/concepts-limits)
