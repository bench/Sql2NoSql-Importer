Sql2NoSql-Importer
==================

Import your Sql data (any JDBC driver such as MySQL, Oracle, PostgreSQL supported) to a NoSQL database . 

Currently supported : `Mongodb`, `CouchDB`, and `Elasticsearch`

Data can be imported as bulk to reduce processing time and can be forwarded to multiple elasticsearch nodes. 

This project was initialy a fork of [Sathis Kumar project](https://code.google.com/p/sql-to-nosql-importer/).

This version fixes serious memory leaks and add new field types support such as binaries, timestamp stored as integer or long, and more.

How to use ?
==================

**1 - Download or clone project**

**2 - Modify import.properties file to match your needs.**

  \#common properties
  sql-data-config-file=db-data-config.xml
  
  autoCommitSize=500 
  
  dataStoreType=couch #available values are mongo,es,couch 
  
  \#couch-db related settings
  couch.host=localhost
  
  couch.db=xms-2124
  
  couch.port=5984

This file defines the structure of your imported documents.
The file structure follows Solr's [dataimport configuration file](http://wiki.apache.org/solr/DataImportHandler)

Field definitions have one more mandatory attribute "type".

Possible values are 
- STRING, 
- INTEGER, 
- DOUBLE, 
- LONG, 
- DATE (convert timestamp or date type to yyyy-MM-dd'T'HH:mm:ssz)
- BOOLEAN, 
- BINARY (convert blob to byte array), 
- TIMESTAMPASINT (convert int to timestamp), 
- TIMESTAMPASLONG (convert long to timestamp), 
- TIMESTAMPASINTTOHUMANFORMAT (convert int to yyyy-MM-dd'T'HH:mm:ssz),
- TIMESTAMPASLONGTOHUMANFORMAT (convert long to yyyy-MM-dd'T'HH:mm:ssz)

**4 - Run main java class : SQLToNoSQLImporter.java**

**5 - Enjoy!**


