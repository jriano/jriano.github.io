---
layout: post
title: Script to Clean Mysql Definers
subtitle: Keeping Some Definers
tags: [bash]
---

I have to constantly move MySQL dumps between environments for testing, and sometimes there are definers with users not present in the new environment. This script takes either a .sql or .sql.gz database dump and change the definers to match your local users.

## Requirements

* Linux, with the following installed
* Git, gunzip
* Clone this snippet and make it executable: [clean_mysql_definers.sh](https://bitbucket.org/snippets/jriano/yebo8b/mysql-definer-cleaner)

## What It Does

It takes a .sql or .sql.gz file, extracts it and replaces the definers with 'root'.

## Configure It

The default is to replace the definer with 'root', but you can change that in line 54:

```bash
# Find definers other than root and admin, and replace them by root
NEWDEFINER='DEFINER=`root`'
```

And you can decide what definers to leave alone by modifying the following in line 55 **(root\|admin)**:

```bash
DEFINERS=$( grep -oE "DEFINER=\`[a-zA-Z]+\`" "${DB}" | grep -viE "DEFINER=\`(root|admin)\`" | sort | uniq )
```

## Run the Script

```bash
./clean_mysql_definers.sh
```

## Enjoy the Extra Time

Over time, this script has saved me a lot of time, hope it helps you too.