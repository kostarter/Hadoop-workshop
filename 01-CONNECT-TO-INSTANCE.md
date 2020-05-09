# Connexion à votre instance Centos :

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
![alt text](https://i.ibb.co/tYL7W8y/Annotation-2020-05-08-135954.png)
