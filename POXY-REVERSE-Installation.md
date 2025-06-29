![Debian_logo-01](./images/Cloud-et-securite.png)

# CYBERSÉCURITÉ / PROXY & REVERSE PROXY

---

## Qu’est-ce qu’un Proxy ?

Un **proxy** est un serveur intermédiaire qui sert d’intermédiaire entre un client (par exemple, un poste de travail) et un serveur cible (comme un site web).  

Il permet notamment de :  
- Masquer l’adresse IP du client  
- Filtrer et contrôler les requêtes (contrôle d’accès, filtrage web)  
- Améliorer la sécurité en isolant le client du serveur final  
- Optimiser les performances via la mise en cache  

> **Fonctionnement :**  
> Le client envoie une requête au proxy → Le proxy relaie la requête vers le serveur → Le serveur répond au proxy → Le proxy transmet la réponse au client.

---

## Qu’est-ce qu’un Reverse Proxy ?

Le **reverse proxy** est un serveur qui se place devant un ou plusieurs serveurs backend (serveurs d’application, web, etc.) afin de :  
- Distribuer la charge (load balancing)  
- Cacher la structure réelle des serveurs backend pour renforcer la sécurité  
- Optimiser les performances grâce à la mise en cache et compression  
- Gérer la terminaison SSL/TLS  
- Proposer une interface unique à plusieurs services  

> **Fonctionnement :**  
> Le client adresse une requête au reverse proxy → Ce dernier sélectionne le serveur backend approprié → Le serveur backend traite la requête → Le reverse proxy transmet la réponse au client.

---

## Proxy vs Reverse Proxy : les différences clés

| Critère                  | Proxy (Forward Proxy)                         | Reverse Proxy                               |
|--------------------------|----------------------------------------------|---------------------------------------------|
| Position                 | Entre client et serveur                      | Entre client et serveurs backend            |
| Objectif principal       | Protection et filtrage côté client           | Protection, optimisation et répartition côté serveur |
| Mise en cache            | Cache côté client                            | Cache côté serveur                          |
| Masquage d’IP            | Masque l’IP du client                        | Masque l’architecture backend               |
| Cas d’usage typique      | Navigation web filtrée, anonymisation       | Load balancing, sécurité serveur, SSL offloading |

---

## Usages courants

### Proxy (Forward Proxy)

- Filtrage et contrôle d’accès web en entreprise  
- Anonymisation et contournement de géo-restrictions  
- Mise en cache locale de contenus fréquents  

### Reverse Proxy

- Serveur frontal (Nginx, Apache) pour plusieurs applications web  
- Répartition de charge (load balancing) dans les infrastructures cloud  
- Gestion centralisée du chiffrement SSL/TLS  

---

## Proxy et sécurité

Les proxies jouent un rôle majeur dans la cybersécurité :  
- Protection des clients et serveurs contre les attaques directes  
- Filtrage des contenus malveillants  
- Réduction des fuites d’informations via anonymisation  
- Réduction de la surface d’attaque en masquant l’infrastructure réelle  

---

## Limites et bonnes pratiques

- Une mauvaise configuration peut créer des vulnérabilités  
- Le reverse proxy doit être dimensionné pour éviter les goulets d’étranglement  
- Le chiffrement HTTPS nécessite une gestion rigoureuse (offloading vs passthrough)  
- Une analyse régulière des logs est essentielle pour détecter les anomalies  

---

## Conclusion

Les **proxy** et **reverse proxy** sont des composants essentiels pour sécuriser et optimiser les échanges réseau.  
Une bonne compréhension et une configuration adaptée renforcent la sécurité et la performance de votre infrastructure.

---

![Proxy-vs-ReverseProxy](./images/Proxy-vs-ReverseProxy.png)
