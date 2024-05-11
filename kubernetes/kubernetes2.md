# Kubernetes : utilisation
<!-- .slide: class="slide" -->  

----

## Etat du cluster
<!-- .slide: class="slide" -->  

```
kubectl get x
kubectl describe x  
kubectl get x -n namespace  
kubectl get x -A
```  

```
kubectl get nodes
kubectl get pods
kubectl get deployment
```

----

## Créer des objets
<!-- .slide: class="slide" -->  

```YAML
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
    - name: nginx
      image: nginx
```  

```
kubectl apply -f object.yml
kubectl delete -f object.yml
```

----

## Debug
<!-- .slide: class="slide" -->  

```
kubectl logs PODID  
kubectl port-forward PODID|SERVICEID HOSTPORT:PODPORT  
kubectl exec -it PODID -- COMMAND
```  

* Connexion SSH sur un worker node 

----

## Demo
<!-- .slide: class="slide" -->  

----

## TP : matos (Choix du cluster)
<!-- .slide: class="slide" -->  

<b>Option cloud, compte temporaire</b>  

Utiliser le cluster partagé :  
* https://console.cloud.google.com/kubernetes/list?project=lebacasable  

<b>Option cloud, compte perso</b>  

* Créer un cluster, minimum 1 noeud  `e2-small`  

Exemples de scripts terraform : https://bitbucket.org/olevitt/formations/src/master/kubernetes/terraform/kubernetes  

<b>Option local</b>  

* Linux : https://k3s.io/  
* Windows / MacOS : :(

----

## TP : matos (Récupération des credentials)
<!-- .slide: class="slide" -->  

<b>Option cloud</b>  

* Aller dans la liste des clusters : https://console.cloud.google.com/kubernetes/list  
* Choisir le cluster  
* Récupérer l'IP de l'APIServer (Endpoint : )  
* Ouvrir le cloudshell (ou installer `gcloud`)
* Récupérer l'access toke (`gcloud auth print-access-token`)

<b>Option local</b>  

* Dépend de la distribution utilisée  
* Pour k3s : configuration déjà faite (`k3s kubectl`)

----

## TP : Hello kubectl
<!-- .slide: class="slide" -->  

* Installer Kubectl  
* Confirmer la bonne connexion au cluster
  
```
kubectl get nodes --server=https://IP --token=TOKEN --insecure-skip-tls-verify
```  

* Créer un namespace personnel  

```
kubectl create namespace NOM_AU_CHOIX
```  

* Dans toute la suite, on travaillera dans ce namespace

----

## TP 1 : Let's deploy
<!-- .slide: class="slide" -->  

* Déployer un `nginx`  
* Consulter ses logs (éventuellement : comparer avec un docker run classique)  
* En utilisant `port-forward`, faire une requête HTTP sur le `nginx`  
* Déterminer l'IP du POD et celle de son noeud hôte  
* Ouvrir un terminal dans le conteneur  

Faire le ménage, tout supprimer

----

## TP 2 : Let's scale
<!-- .slide: class="slide" -->  

Pour la suite, on se proposer d'utiliser l'image `gcr.io/google-samples/hello-app:1.0` plutôt que `nginx`.  
Le code source est disponible [ici](https://github.com/GoogleCloudPlatform/kubernetes-engine-samples/tree/master/hello-app) et le port d'écoute est le `8080`.

* On veut maintenant scaler notre application. Quel concept utiliser à la place des `pods` ?  
* Lancer un `hello-app` scalé à 2 instances  
* Déterminer les IP et noeuds de chaque pod  
* Supprimer un pod, quelles sont les conséquences ?  
* Scaler l'application à 3 instances  
* Quel est la limite à l'utilisation de `port-forward` dans cette situation ?  

Faire le ménage, tout supprimer

----

## TP 3 : Let's expose
<!-- .slide: class="slide" -->  

* On veut maintenant exposer notre `hello-app` scalé. Quel concept utiliser ?  
* Lancer un `hello-app` scalé à 2 instances  
* Créer une IP unique regroupant les différents pods de ce `hello-app`  
* Depuis l'intérieur du cluster, faire une requête HTTP sur cette IP plusieurs fois
* Tuer un pod, tester puis tuer le deuxième, tester  
* A l'aide de la documentation sur les DNS Kubernetes ([ex](https://kubernetes.io/docs/concepts/services-networking/dns-pod-service/)), déterminer le nom DNS associé au service

Faire le ménage, tout supprimer

----

## Aller plus loin
<!-- .slide: class="slide" -->  

* Jouer avec Helm : https://helm.sh/ / https://github.com/helm/helm  
* En se coordonnant avec les autres utilisateurs du cluster, mettre en place l'Ingress Controller `nginx`  (exemple de doc : https://github.com/InseeFrLab/cloud-scripts/tree/master/gke/postinstall)
* Reverse-proxifier `hello-app`