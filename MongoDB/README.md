# MongoDB Cheat Sheet File

**MongoDB** is *NOSQL* Database and doesn't follow strict schema.

The `Write/Insert` operations are **faster**, but `Read`, `Update` and `Delete` Operations are **Slower**.

> **Note:** the variables with `<objectName>` should be replaced by appropriately named object.

# Terminologies:
* `db` - Current Database and can hold many `collections` .
    > In the mongo shell variable `db` is set to the current database.
* `collections` -  these can hold multiple JSON `documents` and are place in Databases (`db`).
    > These are  equivalent to tables in relational databases.
* `documents` - a place to store data. The Data is in Fields and value format and works similar to json.

* `fields` - These are similar to columns in Relational Database and hold meta data for Stored Data.

```
# Databases
`db`
 | # Collections in Database
 |-`<CollectionName>`
 |        | # Documents in Collection
 |        |-`<Document>`
 |        |-`<Document>`
 |
 |
 |-`<CollectionName>`
 |        |-`<Document>`
 |        |-`<Document>`
```

# Starting MongoDB
## Shell
`mongod` - for creating server instance.

`mongo` - for client shell.

---


# Database Operations
`show dbs`- Print a list of all databases on the server.
> **Note:** New database without any `collections` will not appear with this command.

`use <databaseName>` - Switch current database to `<databaseName>` if `<databaseName>` doesn't exist then it creates new database.
> **Note:** Replace `<databaseName>` with appropriate database name

`db` - Will give currently selected `<databaseName>`.

`db.dropDatabase()` - To drop/delete current database.

`show collections` - Print a list of all collections for current database.

`db.createCollection('<collectionName>')` - To create New Empty Collection.

`show profile` - Print the five most recent operations that took 1 millisecond or more.
>See [documentation](https://docs.mongodb.com/manual/tutorial/manage-the-database-profiler/) on the database profiler for more information.


`db.stats()` - Prints range of statistics on current database.
> **Note:** It takes time for large database, but for recent versions it will not block.

`db.<collectionName>.stats()` - Prints range of statistics on `<collectionName>`.

---

# CRUD Functions
## Create/ Insert Function:
> **Note:** In *MongoDB* Creation of schema Fields is done dynamically when inserting the data with new schema to collections.

**To insert one Document to `<collectionName>` in `db`.**
```
db.<collectionName>.insert({
                            '<DocumentFields>': <dataValue>
                            })
```

**to insert many Documents to `<collectionName>` in `db`.**
```
db.<collectionName>.insertMany([
                                {
                                    '<Document1Fields1>': <dataValue> ,
                                    '<Document1Fields2>': <dataValue>
                                },
                                {
                                    '<Document2Fields1>': <dataValue>,
                                    '<Document2Fields2>': <dataValue>
                                },
                            ])
```
---
## Read/Query:
Use [Query Operators](http://docs.mongodb.org/manual/reference/operator/query/) as the **Query argument** for `find()` function.
```
db.<collectionName>.find()
```

**Examples** for Query operator and other function on `find()` :
```
db.<collectionName>.find().pretty()
db.<collectionName>.find({Fields: {$exists: true}})
db.<collectionName>.find({ type: { $in: [ 'Fields', 'Fields2' ] } } )
db.<collectionName>.find().limit( 5 )
db.<collectionName>.find().sort( { name: 1 } ).limit( 5 )
db.<collectionName>.find().skip(5)
```
---

## Update/Modify:

Here we are querying for documents to update and then **`creating new documents`** in its place(old document is replaced).
```
db.<collectionName>.update(
   <query>,
   { <Fields> : <value> }
)
```

Here we are querying for documents to update and then **`replacing`** given `<value>` for `<Fields>` in `$set` operator.
```
db.<collectionName>.update(
   <query>,
   { $set: { <Fields> : <value> }}
)
```
> Read [update](https://docs.mongodb.com/manual/reference/method/db.collection.update/) to learn more.

---
## Delete/Remove:
**remove all**
```
db.<collectionName>.remove({})
```

**remove specific**
````
db.<collectionName>.remove( { <specificFields> : '<SepecificValue>' } )
````

---

## Backup/Restore
### Backup

1. stop the `mongod` instance:

        `service mongodb stop`

2. Go to the backup directory (or any directory where you want to store the mongodb backup), and execute the `mongodump` command.

    > Note: The `–dbpath` in `mongodump` indicates the location of the mongodb database files.

        `cd /backup`

        `mongodump `

3. Finally, start the `mongod` instance;

        `mongod`

### Restore
* Use `mongorestore` to restore from backup directory

        `mongorestore backupfolder/`

> Read [backup with mongodump](http://docs.mongodb.org/manual/tutorial/backup-with-mongodump/) for more information.

---