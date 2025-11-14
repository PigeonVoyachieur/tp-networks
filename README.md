#TP-Network

##Création des fichiers:
    -Création d'un fichier compose.yml à la racine du projet
    -Création d'un fichier Dockerfile dans le dossier app pour Flask et pymysql
    -Création d'un fichier Dockerfile dans le dossier proxy pour nginx

##compose.yml:
    -Permet de lancer le service db qui utilise MariaDB et qui la relie au network "backend_network" pour son utilisation avec le proxy sans qu'elle soit accessible directement
    -Permet de lancer le service app, en lui donnant une dépandance au service db pour qu'il se lance après celui-ci et on lui renseigne le build de l'image à utiliser pour lancer l'app. On lui donne également le network "frontend_network" pour que cela soit le network que l'on souhaite afficher avec le proxy
    -Permet de lancer le service proxy pour que les deux autres services puissent communiquer entre eux sans que le services db soit accessible directement et soit caché. On lui renseigne le build de l'image à utiliser pour lancer le proxy avec nginx et on lui donne les deux network pour qu'il puisse faire la passerelle entre le service app et db

##app/Dockerfile:
    - A partir de "python:3.11-slim" on va récupérer Flask ainsi que pymysql pour le fonctionnement de l'application
    - On renseigne également le port

##proxy/Dockerfile:
    - A partir d'alpine on va récupérer Nginx pour le proxy qui va nous permettre de lier le service app et le service db

##Test: 
    Je n'ai pas pu tester si cela marcher à cause d'un bug de DNS ou de réseaux sur mon docker (voir screen) même en ayant changer le DNS utiliser par Docker Desktop, en ayant forcer le DNS sur le build et l'ayant mis dans le compose.yml pour le build de l'app, etc...

###Ducoup point positif comme dis dans le bonus je n'arrive pas à accéder à db, point négatif je n'accéde à rien dutout.
    
