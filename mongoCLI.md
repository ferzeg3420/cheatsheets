---
title: Mongo CLI
---

# Mongo CLI

## Installation

1. First one must install:\
`brew install mongodb/brew/mongodb-community-shell`

2. then add what we installed to our path:
PATH=/usr/local/Cellar/mongodb-community-shell/4.2.0/bin:$PATH

3. Then run this command with your info username would be your
username and <dbname> your dbname.

`mongo "mongodb+srv://cluster0.clwsl.mongodb.net/<dbname>" --username fernando`

## Basic commands

### Show databases
show dbs  

### Select a database
use <db name>

### Show a collection
show collections 

### Show documents in a collection
db.collectionsName.find() 

### Pretty print the documents in a collection
db.collectionsName.find().pretty()
