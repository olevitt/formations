# Docker
<!-- .slide: class="slide" -->  

[DIY](https://github.com/olevitt/tutoriels/blob/master/docker/hello/README.md)  
[DIY avancé](https://github.com/olevitt/tutoriels/blob/master/docker/avance/README.md)

----

## C'est quoi ?
<!-- .slide: class="slide" -->  

* Une implémentation de la conteneurisation
* Niveau micro : management local  

Pitié, ne confondez pas :  

* <b>Docker engine</b> : moteur
* Docker desktop : packaging incluant docker engine + goodies
* Docker hub : <b>un</b> registre d'image (le plus gros)  
* Docker compose : orchestration locale :older_man:
* Docker swarm : orchestration multi-machines :coffin:   

----

## Installation
<!-- .slide: class="slide" -->  

* Linux : docker engine ou docker desktop
* Mac / Windows : docker desktop
* https://docs.docker.com/engine/install/  

----

## Démo
<!-- .slide: class="slide" -->  

----

## Lancement de conteneurs  
<!-- .slide: class="slide" -->  

```
docker run hello-world
```  

```
docker run -it ubuntu
```  

```
docker run -it ubuntu /bin/bash
```

```
docker run -p 8888:80 nginx
```  

```
docker run --env POSTGRES_PASSWORD=secret -p 5432:5432 postgres:16
```  

```
docker run --env POSTGRES_PASSWORD=secret -p 5432:5432 -d postgres:16
```  

----

## Management (local) de conteneurs  
<!-- .slide: class="slide" -->  

```
docker ps
```  

```
docker logs ID
```  

```
docker kill ID
```  

```
docker exec -it ID COMMAND
```  

----

## Création d'images 
<!-- .slide: class="slide" -->  

Dockerfile :  
```
FROM ubuntu
RUN apt-get update
RUN apt-get -y install cowsay
ENTRYPOINT ["/usr/games/cowsay"]
```  

Docker build :  
```
docker build -t toto .
```  

Docker enjoy :
```  
docker run toto
```  

----

## Publication d'images
<!-- .slide: class="slide" -->  

Nom d'une image docker :  
```  
registry/organisation/nomimage:tag
```  

```  
postgres
postgres:12  
inseefrlab/onyxia-ui
gcr.io/distroless/base-debian10:nonroot
```  

```
docker tag toto monpseudodockerhub/titi
```  

```
docker login  
docker push monpseudodockerhub/titi
```

----

## TP 1 : Hello docker
<!-- .slide: class="slide" -->  

* Installer docker  
* Valider l'installation de Docker en lançant ```hello-world```
* Lancer un conteneur `nginx` (https://hub.docker.com/_/nginx)  
* Faire une requête HTTP sur le serveur `nginx`  
* Se connecter à chaud dans le `nginx`, supprimer le fichier /usr/share/nginx/html/index.html  
* Refaire une requête HTTP sur le serveur `nginx` : constater  
* Tuer le conteneur, le recréer, refaire une requête

----


## TP 2 : Mon image Docker
<!-- .slide: class="slide" -->  

* Créer une image Docker, en y mettant ce qui vous fait plaisir  
* Lancer des conteneurs de cette image  
* Publier votre image (soit sur dockerhub en créant un compte, soit sur ttl.sh soit sur le registre d'un ami (cf TP3))
* Diffuser le nom de votre image et épatez vos amis !  

----


## TP 3 : Aller plus loin
<!-- .slide: class="slide" -->  

* En utilisant l'image [registry](https://hub.docker.com/_/registry), mettre à disposition un registre public  
* Jeter un oeil aux volumes Docker : https://docs.docker.com/storage/volumes/
* En se baladant sur [Dockerhub](https://hub.docker.com), lancer les conteneurs de vos logiciels préférés  
* Exemples : ([VSCode](https://hub.docker.com/r/codercom/code-server), [Infinite mario](https://hub.docker.com/r/pengbai/docker-supermario/) ...)