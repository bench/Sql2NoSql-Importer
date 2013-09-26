Sql2NoSql-Importer
==================

Import Sql (MySQL,Oracle,PostgreSQL) data to NoSQL Systems. Mongodb,CouchDB, and Elastic Search systems are currently supported.

This project is a fork from https://code.google.com/p/sql-to-nosql-importer/ project, initialy developed by Sathis Kumar.

This version fixes serious memory leaks and add new field types support such as binaries, timestamp stored as integer or long, and more.

How to use ?
==================

#Download or clone project

#Modify import.properties file to match your needs.

Example :

\#common properties
sql-data-config-file=db-data-config.xml

autoCommitSize=500 

dataStoreType=couch #available values are mongo,es,couch 


\#couch-db related settings

couch.host=localhost

couch.db=xms-2124

couch.port=5984

3-Modify import.properties file. This file defines the structure of your imported documents.
The file structure follows Solr's dataimport configuration file. (see http://wiki.apache.org/solr/DataImportHandler)

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

4-Run SQLToNoSQLImporter.java !

