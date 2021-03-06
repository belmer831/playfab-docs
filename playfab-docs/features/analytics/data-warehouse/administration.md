---
title: Data Warehouse tutorial - administration
author: kennethsabotta
description: Learn how to administer permissions and tables with Data Warehouse.
ms.author: Kenneth.Sabotta
ms.date: 01/17/2019
ms.topic: article
ms.prod: playfab
ROBOTS: NOINDEX,NOFOLLOW
keywords: playfab. analytics, data warehouse, permissions, tables, administration
ms.localizationpriority: medium
---

# Data Warehouse tutorial - administration

> [!IMPORTANT]
> This feature is currently in **Private Preview**.  
>
> It is provided to give you an early look at an upcoming feature and to allow you to provide feedback while it is still in development.  
>
> Access to this feature is restricted to select titles. If you are interested in trying it, you can request access by submitting a ticket on [support.playfab.com](https://support.playfab.com/hc/en-us/requests/new).

The Data Warehouse Premium offering grants customers access to an isolated cluster to conduct queries or create, schedule and monitor custom data pipelines without sharing compute or storage resources. When enabling the offering, an organizational or Microsoft account (MSA) is required in order to access the cluster and perform administrative tasks like create tables or assign user permissions. This tutorial demonstrates helpful queries to complete these tasks.

## Administering Permissions

Adds a new user with an MSA to access the cluster:

```cmd
.add follower database {DATABASENAME} admins/users ('msauser={MSA Email}')
```

Adds a new user with a organizational account (i.e. AAD):

```cmd
.add follower database {DATABASENAME} admins/users ('aaduser=imikeoein@fabrikam.com;TENANTID'')
```

## Table Administration

Run a query against the raw events and insert results into a newly created table:

```cmd
.set-or-append TestOutputTable <| database("SOURCEDATABASE").SourceTable | count
```

Alter/update a table with new column:

```cmd
.alter-merge table TestOutputTable (newColumnName:string)
```
