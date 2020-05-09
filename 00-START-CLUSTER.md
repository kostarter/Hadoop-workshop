# Lancement du cluster :
 
## Lancement de Cloudbreak :

1. Se connecter en tant que l'utilisateur 'cloudbreak' à la machine SYBREAK.

2. Aller dans le dossier /var/lib/cloudbreak-deployment/Profile.

3. Lancer la commande suivante en tant que super utilisateur :
```console
$ sudo cbd start
```

4. Lancer le cluster Sophia sur l'UI Cloudbreak.
![alt text](https://i.ibb.co/5ckWTzn/Screenshot-2020-05-10-Hortonworks-Cloudbreak.png "Start/Stop cluster")

5. Se connecter à Ambari afin de lancer les services.

:warning: Les services doivent être lancés dans le bon ordre (Zookeeper, Ranger, Yarn, HDFS, MapReduce, ...).

![alt text](https://i.ibb.co/JrJYmsj/Screenshot-2020-05-10-Ambari-hwx-sophia.png "Start/Stop services on Ambari")
