---
title: Common CKAN administrator tasks
date: 2018-11-18 14:20:32
tags:
 - ckan
 - cli
 - paster
categories:
 - ckan
teaser: How to carry out common CKAN admin tasks using paster.
---

The majority of common CKAN administration tasks are carried out using the **paster** script.

Paster is run on the command line on the server running CKAN. This section covers *common tasks using paster*

#### Activating of VirtualEnv

Before excuting paster script, must the **VirtualEnv** be activated

```bash
# activate VirtualEnv
. /usr/lib/ckan/default/bin/activate
```

For the full list of tasks supported by paster, you can run:

``` bash
paster --plugin=ckan --help
```


#### Database

```bash
# Before running CKAN for the first time,
# run db init to create the tables in the database and the default authorization settings
paster --plugin=ckan db init -c /etc/ckan/production.ini

# delete everything in the database, including the tables, to start from scratch
paster --plugin=ckan db clean -c /etc/ckan/production.ini

# upgrade migration
paster --plugin=ckan db upgrade -c /etc/ckan/production.ini
```


#### User - Create and manage users

``` bash
# create user
paster --plugin=ckan user add admin -c /etc/ckan/production.ini

# Give sysadmin rights
paster --plugin=ckan sysadmin add admin -c /etc/ckan/production.ini

# delete user
paster --plugin=ckan user remove admin -c /etc/ckan/production.ini
```

#### Rebuild search index

```bash
# reindex all datasets
paster --plugin=ckan search-index rebuild -c /etc/ckan/production.ini

# reindex only one dataset dataset_name
paster --plugin=ckan search-index rebuild dataset-name -c /etc/ckan/production.ini

# reindex only datasets, which are not already indexed
paster --plugin=ckan search-index rebuild -o -c /etc/ckan/production.ini

# don’t rebuild the whole index, but just refresh it
paster --plugin=ckan search-index rebuild -r -c /etc/ckan/production.ini

# checks for datasets not indexed
paster --plugin=ckan search-index check -c /etc/ckan/production.ini

# shows index of a dataset
paster --plugin=ckan search-index show <dataset_name> -c /etc/ckan/production.ini

# clears the search index for the provided dataset or for the whole ckan instance
paster --plugin=ckan search-index clear [dataset_name] -c /etc/ckan/production.ini
````

#### Harvester

Harvest sources must be created via web interface

``` bash
# shows all harvest source with source id
paster --plugin=ckanext-harvest harvester sources -c /etc/ckan/production.ini

# create harvest job for an harvest source
paster --plugin=ckanext-harvest harvester job {source_id} -c /etc/ckan/production.ini

## remove all datasets and harvest jobs a harvest source
paster --plugin=ckanext-harvest harvester clearsource {source_id} -c /etc/ckan/production.ini

# remove a harvest source
paster --plugin=ckanext-harvest harvester rmsource {source_id} -c /etc/ckan/production.ini

# excutes harvest jobs - harvesting
paster --plugin=ckanext-harvest harvester run -c /etc/ckan/production.ini

# gather data from harvest jobs
paster --plugin=ckanext-harvest harvester gather_consumer -c /etc/ckan/production.ini

# Running after gather_consumer
# fetch and insert data from gather_consumer to database
paster --plugin=ckanext-harvest harvester fetch_consumer -c /etc/ckan/production.ini

# cleans queue of gather_consumer and fetch_consumer
paster --plugin=ckanext-harvest harvester purge_queues -c /etc/ckan/production.ini
```

***Links***
* [CKAN Documentation](https://docs.ckan.org/en/ckan-1.7.4/paster.html)