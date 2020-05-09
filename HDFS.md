### HADOOP - TP 1
LE SYSTÈME DE GESTION DE FICHIER HDFS

BUT DU TP :
Prendre en main et apprendre à manipuler des fichiers dans l’environnement HDFS. :heavy_check_mark: 

<br/>

#### Enoncé 1 : Manipulation

:information_source: CONSULTER PREALABLEMENT LA REFERENCE DES COMMANDES USUELLES EN PAGE 5

1 - Télécharger le fichier suivant dans le Système linux via la commande WGET 
```console
wget https://raw.githubusercontent.com/jpatokal/openflights/master/data/airports.dat
```

2 - Créer un répertoire sous HDFS OPTIONNEL.
[mon_user@ip-172-31-23-69:~]# hdfs dfs -mkdir /user/mon_user

:warning: Spoiler : 
```console
$ hdfs dfs -mkdir /user/my-user
```

3 - Insérer le fichier dans ce répertoire HDFS via la commande PUT dans votre répertoire user.

:warning: Spoiler : 
```console
$ hdfs dfs -put airports.dat /user/my-user
```

4 - Vérifier la présence de ce fichier dans votre répertoire hdfs user via la commande LS (hdfs).

:warning: Spoiler : 
```console
$ hdfs dfs -ls /user/my-user
```
<br/>

#### Enoncé 1/2 : Manipulation

1 - Créer un répertoire hdfs “data” dans votre répertoire “user/monavatar”.

:warning: Spoiler : 
```console
$ hdfs dfs -mkdir /user/my-user/data
```

2 - Déplacer le fichier airports.dat depuis hdfs dans ce répertoire data.

:warning: Spoiler : 
```console
$ hdfs dfs -mv /user/my-user/airports.dat /user/my-user/data
```

3 - Modifier les droits hdfs de ce fichier pour le rendre accessible uniquement à vous.

:warning: Spoiler :
```console
$ hdfs dfs -chmod 700 /user/my-user/data/airports.dat
```

:information_source: Consulter la doc pour les commandes :  mkdir / mv / chmod

<br/>

#### Enconcé 2 : METADATA

Explorer le mapping réel des fichiers HDFS dans EXT4.
Localiser les données relatives au fichier chargé dans HDFS lors de la première partie.

* Blocs du fichier
* Mapping du fichier et des blocs
* Mapping des blocs vers les serveurs

:information_source: Ressource Utile : 
https://hortonworks.com/blog/hdfs-metadata-directories-explained/


Infos des blocs de fichiers :
```console
$ hdfs fsck /user/my-user/data/airports.dat -files -blocks -locations
```
