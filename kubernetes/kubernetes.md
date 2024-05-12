# Kubernetes (k8s)
<!-- .slide: class="slide" -->  

----

## C'est quoi ?
<!-- .slide: class="slide" -->  

* Orchestrateur de conteneurs
* Release : 2015  
* Opensource (apache 2.0) par Google  
* Distributions Kubernetes : cloud VS on-premise  
* Managé (GKE, EKS, AKS, OVHCloud ...)  
* Non managé (K3S, OpenShift, Rancher 2.0 ...)

----

## Architecture
<!-- .slide: class="slide" -->  

![](kubernetes/img/archi_k8s.png)  

----

## Kubectl
<!-- .slide: class="slide" -->  

* CLI
* Interaction avec les masters (APIServer)  
* https://kubernetes.io/docs/tasks/tools/install-kubectl/  
* Kubeconfig : URL, token (+ certificat SSL, namespace ...)  

----

## Concepts
<!-- .slide: class="slide" -->  

* node : machine
* pod : plus petite unité kubernetes. Correspond à 1 (quelques fois plusieurs) conteneur.  
* deployment : gère les pods, s'assure du bon nombre de pods vivants.  
* service : exposition d'un pod dans le cluster.  
* ingress : exposition d'un service au monde extérieur (~ une entrée reverse proxy).  

Et tellement d'autres (secret, serviceaccount, replicaset, configmap, persistentvolumeclaim ...) !  
+ vos propres concepts : CRD (Custom Resource Definition).

----

## Demo
<!-- .slide: class="slide" -->  



----

## Alternative vidéo
<!-- .slide: class="slide" -->  

<iframe width="560" height="315" src="https://www.youtube.com/embed/aSrqRSk43lY" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>  

