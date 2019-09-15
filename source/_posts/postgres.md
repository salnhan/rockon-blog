---
title: Common postgreSQL commands
date: 2018-04-16 12:55:43
tags:
 - postgres
categories:
 - postgreSQL
teaser: Useful postgreSQL commands
---

Common postgreSQL commands

{% img logo-icon
 https://www.postgresql.org/media/img/about/press/elephant.png
 150 120 postgreSQL logo %}

#### Basic PostgeSQL commands

``` bash
# switch postgres
sudo su - postgres
#call psql
psql
# show call database
\l

## connect to database
\c database_name

## show all tables of database;
\dt

# show columns of a table;
\d+ table_name

# disconnect a database
\q

# show content of a table
select * from table_name;

# clear table
TRUNCATE table_name CASCADE;

# drop database
REVOKE CONNECT ON DATABASE database_name FROM public;
SELECT pg_terminate_backend(pg_stat_activity.pid) FROM pg_stat_activity WHERE pg_stat_activity.datname = 'database_name';
DROP DATABASE database_name;

# create database
CREATE DATABASE database_name;

# create database user
createuser -S -D -R -P -l datastore_default;
createdb -O ckan_default datastore_default -E utf-8


# grant select permissions for read-only user
GRANT CONNECT ON DATABASE "datastore_default" TO "datastore_default";
GRANT USAGE ON SCHEMA public TO "datastore_default";

# grant access to current tables and views to read-only user
GRANT SELECT ON ALL TABLES IN SCHEMA public TO "datastore_default";

# grant access to new tables and views by default
ALTER DEFAULT PRIVILEGES FOR USER "ckan_default" IN SCHEMA public
  GRANT SELECT ON TABLES TO "datastore_default";
```

#### PostgeSQL in Docker

``` bash
# import dump to docker container 
cat full-backup-1d.sql | docker exec -i rlp_ckan_tpp_db pg_restore  -U postgres -d ckan_default
```


***Links***
* https://www.postgresql.org/