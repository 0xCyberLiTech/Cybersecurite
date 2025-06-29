<p align="center">
  <img src="./images/Cloud-et-securite.png" alt="Cloud et Sécurité" width="300" />
</p>

# CYBERSÉCURITÉ / PROXY & REVERSE PROXY

---

## Qu’est-ce qu’un Proxy ?

Un **proxy** est un serveur intermédiaire qui agit comme un relais entre un client (souvent un poste de travail) et un serveur cible (par exemple un site web).  

Il sert à :  
- **Masquer l’adresse IP du client**  
- **Filtrer et contrôler les requêtes** (ex : contrôle parental, filtrage web en entreprise)  
- **Améliorer la sécurité** en isolant le client du serveur réel  
- **Optimiser la connexion** (mise en cache des contenus fréquents)  

### Fonctionnement d’un proxy classique

Le client envoie sa requête au proxy → Le proxy transmet la requête au serveur cible → Le serveur répond au proxy → Le proxy renvoie la réponse au client.

---

## Qu’est-ce qu’un Reverse Proxy ?

Le **reverse proxy** est un serveur intermédiaire qui se place devant un ou plusieurs serveurs d’application ou web, et non devant le client.  

Il sert principalement à :  
- **Distribuer la charge** entre plusieurs serveurs (load balancing)  
- **Cacher la véritable infrastructure** du backend pour renforcer la sécurité  
- **Améliorer la performance** via la mise en cache ou compression des réponses  
- **Assurer la terminaison SSL/TLS** pour décharger les serveurs backend  
- **Offrir une interface unique** à plusieurs services internes  

### Fonctionnement d’un reverse proxy

Le client fait une requête vers le reverse proxy → Le reverse proxy décide quel serveur backend doit traiter la requête → Le serveur backend répond → Le reverse proxy transmet la réponse au client.

---

## Proxy vs Reverse Proxy : résumé

| Aspect                  | Proxy (forward proxy)                            | Reverse Proxy                                    |
|-------------------------|------------------------------------------------|-------------------------------------------------|
| Placement               | Entre client et serveur                         | Entre client et serveurs backend                  |
| Objectif principal      | Protéger et filtrer le client                   | Protéger et optimiser les serveurs backend        |
| Cache                   | Cache côté client                               | Cache côté serveur                                |
| Masquage                | Masque l’IP du client                           | Masque l’architecture serveur                     |
| Utilisation typique     | Navigation internet sécurisée, filtrage, anonymat | Répartition de charge, sécurité serveur, SSL termination |

---

## Exemples d’usages courants

### Proxy classique

- Dans les entreprises pour contrôler et filtrer l’accès à Internet  
- Pour masquer son IP et naviguer anonymement  
- Pour accéder à des contenus géo-restreints  

### Reverse Proxy

- Serveur Nginx ou Apache en frontal pour plusieurs applications web  
- Services de load balancing dans les infrastructures cloud  
- Terminaison SSL centralisée pour simplifier la gestion des certificats  

---

## Proxy & Sécurité

Les proxies, forwards ou reverse, jouent un rôle crucial dans la cybersécurité :  

- **Protection des endpoints et des serveurs** contre les attaques directes  
- **Filtrage et contrôle des contenus** malveillants  
- **Prévention des fuites d’informations** via anonymisation  
- **Réduction de la surface d’attaque** en cachant l’infrastructure réelle  

---

## Limites et précautions

- Un proxy mal configuré peut devenir un point d’entrée vulnérable  
- Le reverse proxy doit être dimensionné pour ne pas devenir un goulet d’étranglement  
- Le chiffrement (HTTPS) doit être géré avec soin (SSL offloading vs passthrough)  
- Les logs doivent être analysés régulièrement pour détecter des activités suspectes  

---

## Conclusion

Les **proxy** et **reverse proxy** sont des outils indispensables pour la gestion, la sécurité et l’optimisation des échanges entre clients et serveurs.  

Bien compris et bien configurés, ils renforcent considérablement la posture de sécurité et la performance des infrastructures réseau.

---

<p align="center">
  <img src="./images/Proxy-vs-ReverseProxy.png" alt="Proxy vs Reverse Proxy" width="600" />
</p>
