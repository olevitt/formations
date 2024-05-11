# Bonus : création d'un cluster Kubernetes

<!-- .slide: class="slide" -->

---

## Le choix des armes

<!-- .slide: class="slide" -->

| Distribution                                              | Tutorial                                                                                       | Avantages                                | Inconvénients         |
| --------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------- | --------------------- |
| [RKE](https://github.com/rancher/rke)                     | [Quickstart](https://rancher.com/docs/rke/latest/en/installation/)                             | Léger, simple                            | Tout tourne en docker |
| [Kubespray](https://github.com/kubernetes-sigs/kubespray) | [Quickstart](https://github.com/kubernetes-sigs/kubespray/blob/master/docs/getting-started.md) | Très paramétrable, plus complet, ansible | Plus lourd            |
| [K3S](https://github.com/kubernetes-sigs/kubespray)       | [Quickstart](https://rancher.com/docs/k3s/latest/en/quick-start/)                              | One-liner, ultra léger (edge computing)  | Production ready ???  |

---

## Principes généraux

<!-- .slide: class="slide" -->

- Configurer les noeuds (installer un OS, docker, configuratin des clés SSH)
- Créer un fichier inventaire des différents noeuds et de leurs rôles (master, etcd, worker)
- Lancer l'installation / upgrade en fournissant l'inventaire
- ???
- Profit
