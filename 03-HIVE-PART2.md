# HIVE - TP 2
TABLES EXTERNES - VISUALISATION

<br/>

## Hive: External Tables

* Quick Pre-read : 
  
  https://www.quora.com/Difference-between-Hive-internal-tables-and-external-tables

* Creating external table Example - Create table on weather data :
  
```sql
  CREATE EXTERNAL TABLE weather (temperature INT, date STRING)
  ROW FORMAT DELIMITED
  FIELDS TERMINATED BY ','
  LOCATION '/hive/data/weather';
```
<br/>

## Chargement depuis HDFS

**Load the data in table**

Load the data from HDFS to Hive using the following command:

```console
  LOAD DATA INPATH ‘hdfs:/data/2012.txt’ INTO TABLE weather;
```
<br/>

## Partitionnement

* Hive stores tables in partitions. Partitions are used to divide the table into related parts. Partitions make data querying more efficient. 

* For example in the above weather table the data can be partitioned on the basis of year and month and when query is fired on weather table this partition can be used as one of the column.

**EXAMPLE :**

```sql
  CREATE EXTERNAL TABLE IF NOT EXISTS weather (temperature INT, date STRING)
    PARTITIONED BY (year INT, month STRING)
    ROW FORMAT DELIMITED
    FIELDS TERMINATED BY ','
    LOCATION '/hive/data/weather';
```

* Loading data in partitioned tables is different than non-partitioned one. 

* There is little manual work of mentioning the partition data. 

* Data can be loaded in partition, year 2012 and month 01 and 02 as follows:
```console
LOAD DATA INPATH ‘hdfs:/data/2012.txt’ INTO TABLE weather PARTITION (year=2012, month=’01’);
LOAD DATA INPATH ‘hdfs:/data/2012.txt’ INTO TABLE weather PARTITION (year=2012, month=’02’);
```

* This creates the partitioned table and makes different folder for each partition which helps in querying data.

### Querying of partitioned table :

Partitioned tables can use partition parameters as one of the column for querying. To retrieve all the data for month of ‘02’ following query can be used on weather table.

```sql
SELECT * FROM weather WHERE month = '02';
```

# Assignment

####Utiliser le dataset suivant :
https://www1.ncdc.noaa.gov/pub/data/ghcn/daily/by_year/

1. Etudier la structure d’un fichier.

2. Charger les données des années 2017- 2018 dans HIVE (tables externes).

3. Effectuer un partitionnement adapté.

4. Créer des vues et requêter les données.

5. Visualiser des histogrammes pertinents dans Superset (Demo Live Mehdi + doc sur Slack).
