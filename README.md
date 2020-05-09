# Lancement du cluster :
 
## Lancement de Cloudbreak :

1. Se connecter en tant que l'utilisateur 'cloudbreak' à la machine SYBREAK.

2. Aller dans le dossier /var/lib/cloudbreak-deployment/Profile.

3. Lancer la commande suivante en tant que super utilisateur :
```console
$ cbd start
```

4. Lancer le cluster Sophia sur l'UI Cloudbreak.

5. Se connecter à Ambari afin de lancer les services.

:warning: Les services doivent être lancés dans le bon ordre (Zookeeper, Ranger, Yarn, HDFS, MapReduce, ...).

<br/><br/>
## Connexion à votre instance Centos :

Vos Credentials et IP respectives vous seront envoyés sur le chat.
Une clé SSH .pem vous sera transmise sur le chat.

:warning: Si vous êtes sur Windows :

- Installation de Mobaxterm :
https://download.mobatek.net/2022020030522248/MobaXterm_Portable_v20.2.zip

La clé est fournie au format .pem : Convertissez-la en .ppk 

Pour ce faire suivre le mini-tuto ce-dessous :

```console
- Convert PEM to PPK :

1. Open PuTTYgen
3. Click "Load" on the right side about 3/4 down
4. Set the file type to *.*
5. Browse to, and Open your .pem file
6. PuTTY will auto-detect everything it needs, and you just need to click "Save private key" and you can save your ppk key for use with PuTTY

https://stackoverflow.com/questions/3190667/convert-pem-to-ppk-file-format
```


Se connecter en SSH à un des workers du cluster :
```console
ssh -i ./SYLAB.pem cloudbreak@35.180.197.45
```

<br/><br/>
### HADOOP - TP 1
LE SYSTÈME DE GESTION DE FICHIER HDFS

BUT DU TP :
Prendre en main et apprendre à manipuler des fichiers dans l’environnement HDFS. :heavy_check_mark: 

<br/><br/>
##### Enoncé 1 : Manipulation

:information_source: CONSULTER PREALABLEMENT LA REFERENCE DES COMMANDES USUELLES EN PAGE 5

1 - Télécharger le fichier suivant dans le Système linux via la commande WGET 
```console
wget https://raw.githubusercontent.com/jpatokal/openflights/master/data/airports.dat
```

2 - Créer un répertoire sous HDFS OPTIONNEL.
[mon_user@ip-172-31-23-69:~]# hdfs dfs -mkdir /user/mon_user

:warning: Spoiler : 
```console
$ hdfs dfs -mkdir /user/hbachkou
```

3 - Insérer le fichier dans ce répertoire HDFS via la commande PUT dans votre répertoire user.

:warning: Spoiler : 
```console
$ hdfs dfs -put airports.dat /user/hbachkou
```

4 - Vérifier la présence de ce fichier dans votre répertoire hdfs user via la commande LS (hdfs).

:warning: Spoiler : 
```console
$ hdfs dfs -ls /user/hbachkou
```
<br/><br/>
##### Enoncé 1/2 : Manipulation

1 - Créer un répertoire hdfs “data” dans votre répertoire “user/monavatar”.

:warning: Spoiler : 
```console
$ hdfs dfs -mkdir /user/hbachkou/data
```

2 - Déplacer le fichier airports.dat depuis hdfs dans ce répertoire data.

:warning: Spoiler : 
```console
$ hdfs dfs -mv /user/hbachkou/airports.dat /user/hbachkou/data
```

3 - Modifier les droits hdfs de ce fichier pour le rendre accessible uniquement à vous.

:warning: Spoiler :
```console
$ hdfs dfs -chmod 700 /user/hbachkou/data/airports.dat
```

:information_source: Consulter la doc pour les commandes :  mkdir / mv / chmod

<br/><br/>
##### Enconcé 2 : METADATA

Explorer le mapping réel des fichiers HDFS dans EXT4.
Localiser les données relatives au fichier chargé dans HDFS lors de la première partie.

* Blocs du fichier
* Mapping du fichier et des blocs
* Mapping des blocs vers les serveurs

:information_source: Ressource Utile : 
https://hortonworks.com/blog/hdfs-metadata-directories-explained/


Infos des blocs de fichiers :
```console
$ hdfs fsck /user/hbachkou/data/airports.dat -files -blocks -locations
```
