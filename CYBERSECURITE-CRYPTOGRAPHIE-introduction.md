<p align="center">
  <img src="https://avatars.githubusercontent.com/u/167217017?s=400&u=d983b9423c4eb8cdb9bfe8b14f505be5c894d6bc&v=4" width="150" />
</p>

<h1 align="center">🌐 CYBERSÉCURITÉ - CRYPTOGRAPHIE 🌐</h1>
<h2 align="center"> INTRODUCTION</h2>

<p align="center">
  Un dépôt pédagogique autour des fondamentaux de la cybersécurité.<br>
  📘 Apprentissage – 🔐 Sécurité – 🧠 Compréhension
</p>

---
<h2 align="left">💡 La Cryptographie.</h2>
<h3 align="left">👋 L'Art du Secret et de la Sécurité Numérique.</h3>

La cryptographie, du grec "kryptos" (caché) et "graphein" (écrire), est la science et l'art de concevoir des méthodes permettant de **protéger l'information**. Historiquement, son but était de garantir le secret des communications. Aujourd'hui, elle englobe bien plus, servant de fondation à la sécurité de nos systèmes numériques.

On distingue principalement deux grands domaines :
1.  La **cryptographie symétrique** (ou à clé secrète).
2.  La **cryptographie asymétrique** (ou à clé publique).

---
<h2 align="left">💡 Pourquoi la cryptographie est-elle essentielle ?</h2>

Dans un monde hyper-connecté, la cryptographie est cruciale car elle garantit quatre propriétés fondamentales de la sécurité de l'information :

1.  **Confidentialité :** S'assurer que seules les personnes autorisées peuvent accéder à l'information (ex : chiffrer un email).
2.  **Intégrité :** Garantir que l'information n'a pas été modifiée ou altérée (ex : vérifier qu'un fichier téléchargé n'est pas corrompu).
3.  **Authentification :** Vérifier l'identité d'un utilisateur, d'un système ou d'une information (ex : s'assurer que vous communiquez avec le bon serveur bancaire).
4.  **Non-répudiation :** Empêcher une entité de nier avoir effectué une action (ex : prouver qu'un contrat numérique a bien été signé par une partie).

---
<h2 align="left">💡 I. La Cryptographie Symétrique : La Clé Partagée</h2>

C'est la forme la plus ancienne de cryptographie. Ici, la **même clé** est utilisée à la fois pour **chiffrer** et **déchiffrer** les données.

<h3 align="left">👋 Comment ça marche ?</h3>

Imaginez que vous voulez envoyer un message secret à un ami. Vous décidez d'utiliser un cadenas et une clé unique. Vous mettez votre message dans une boîte, fermez le cadenas avec votre clé, et l'envoyez. Votre ami doit avoir une copie exacte de cette même clé pour ouvrir le cadenas et lire le message.

* **Chiffrement :** Message clair (M) + Clé (K) $\rightarrow$ Message chiffré (C)
* **Déchiffrement :** Message chiffré (C) + Clé (K) $\rightarrow$ Message clair (M)

<h3 align="left">👋 Algorithmes courants :</h3>

* **AES (Advanced Encryption Standard) :** La norme actuelle, largement utilisée et très sécurisée. On la retrouve partout, des applications de messagerie aux VPN.
* **DES (Data Encryption Standard) / 3DES :** Plus anciens, DES est maintenant faible, 3DES est encore utilisé mais déprécié.

<h3 align="left">👋 Avantages :</h3>

* **Rapidité :** Généralement beaucoup plus rapides que les algorithmes asymétriques, ce qui les rend idéaux pour chiffrer de grandes quantités de données.
* **Efficacité :** Nécessitent moins de puissance de calcul.

<h3 align="left">👋 Inconvénients :</h3>

* **Gestion des clés :** Le défi majeur est la **distribution sécurisée de la clé**. Comment l'ami et vous échangez-vous la clé secrète sans qu'un espion ne la capte ? C'est le "problème de l'échange de clés".
* **Scalabilité :** Pour $N$ participants, il faut $N \times (N-1) / 2$ clés, ce qui devient vite ingérable dans de grands réseaux.

---

<h2 align="left">💡 II. La Cryptographie Asymétrique (à Clé Publique) : Les Deux Clés</h2>

Développée dans les années 1970, cette forme de cryptographie a révolutionné la sécurité en introduisant la notion de **paire de clés** : une clé publique et une clé privée.

<h3 align="left">👋 Comment ça marche ?</h3>

Chaque participant possède une paire de clés mathématiquement liées :

* **Clé publique :** Peut être partagée avec tout le monde. Elle sert à chiffrer un message pour son propriétaire ou à vérifier une signature numérique de ce dernier.
* **Clé privée :** Doit rester absolument secrète et n'est connue que de son propriétaire. Elle sert à déchiffrer les messages chiffrés avec la clé publique correspondante, ou à créer une signature numérique.

<h3 align="left">👋 Scénarios d'utilisation :</h3>

1.  **Confidentialité :**
    * Alice veut envoyer un message confidentiel à Bob.
    * Alice utilise la **clé publique de Bob** pour chiffrer le message.
    * Bob utilise sa **clé privée** (la seule qui fonctionne) pour déchiffrer le message.
    * **L'avantage :** Alice n'a jamais eu besoin d'échanger une clé secrète avec Bob.

2.  **Authentification et Intégrité (avec signature numérique) :**
    * Alice veut prouver qu'elle est l'expéditeur et que le message n'a pas été altéré.
    * Alice utilise sa **clé privée** pour "signer" numériquement le message (en réalité, elle signe un hachage du message).
    * Bob utilise la **clé publique d'Alice** pour vérifier cette signature. Si la vérification réussit, il est certain qu'Alice est l'expéditeur et que le message est intact.
    * Ceci garantit l'authentification et la non-répudiation.

<h3 align="left">👋 Algorithmes courants :</h3>

* **RSA (Rivest-Shamir-Adleman) :** L'algorithme asymétrique le plus connu, basé sur la difficulté de factoriser de grands nombres premiers. Employé pour le chiffrement, les signatures numériques et l'échange de clés.
* **ECC (Elliptic Curve Cryptography) :** Basé sur des courbes elliptiques, il offre un niveau de sécurité équivalent avec des clés plus courtes, avantageux pour les appareils à ressources limitées.
* **Diffie-Hellman :** Algorithme spécifiquement conçu pour l'échange sécurisé de clés symétriques sur un canal non sécurisé (souvent utilisé dans SSL/TLS).

<h3 align="left">👋 Avantages :</h3>

* **Distribution des clés simplifiée :** Pas besoin d'échanger secrètement une clé avant de communiquer. Les clés publiques peuvent être largement diffusées.
* **Non-répudiation et Authentification :** Permet les signatures numériques.
* **Échange de clés :** Résout le problème de l'échange de clés symétriques.

<h3 align="left">👋 Inconvénients :</h3>

* **Lenteur :** Les opérations de chiffrement/déchiffrement sont beaucoup plus lentes.
* **Taille des clés :** Nécessitent des clés beaucoup plus longues pour un niveau de sécurité équivalent (ex : clé RSA de 2048 bits pour la même sécurité qu'une clé AES de 128 bits).

---

<h2 align="left">💡 III. Fonctions de Hachage Cryptographique : L'Empreinte Numérique</h2>

Les fonctions de hachage sont des algorithmes qui prennent une entrée de taille arbitraire et produisent une **sortie de taille fixe** (appelée "hachage", "empreinte numérique" ou "digest").

<h3 align="left">👋 Propriétés essentielles :</h3>

1.  **Déterministe :** La même entrée produit toujours la même sortie.
2.  **Rapide à calculer :** Le calcul du hachage doit être rapide.
3.  **Résistance à la préimage :** Il est très difficile de retrouver l'entrée à partir du hachage.
4.  **Résistance à la seconde préimage :** Pour une entrée donnée, il est très difficile de trouver une autre entrée qui produise le même hachage.
5.  **Résistance aux collisions :** Il est très difficile de trouver deux entrées différentes qui produisent le même hachage.

<h3 align="left">👋 Algorithmes courants :</h3>

* **SHA-2 (Secure Hash Algorithm 2) :** Inclut SHA-256, SHA-512, très largement utilisés pour la vérification d'intégrité, les signatures numériques, les certificats SSL/TLS.
* **SHA-3 :** Nouvelle famille de fonctions de hachage, choisie comme standard par le NIST.
* **MD5 / SHA-1 :** Ancien (MD5 est obsolète, SHA-1 est fortement déprécié).

<h3 align="left">👋 Utilisations :</h3>

* **Vérification d'intégrité :** Pour s'assurer qu'un fichier n'a pas été modifié.
* **Stockage de mots de passe :** On ne stocke jamais les mots de passe en clair, mais leur hachage (souvent "salé").
* **Signatures numériques :** Pour signer un document, on signe son hachage, pas le document entier.
* **Blockchain et Cryptomonnaies :** Fondamentales pour l'intégrité des transactions.

---

<h2 align="left">💡 IV. L'Utilisation Combinée : Le "Chiffrement Hybride"</h2>

En pratique, la plupart des systèmes sécurisés (comme SSL/TLS qui sécurise les connexions HTTPS) utilisent une **approche hybride** qui combine les avantages des cryptographies symétrique et asymétrique :

1.  **Échange de clé symétrique :** Les parties utilisent la cryptographie **asymétrique** (ex : Diffie-Hellman ou RSA) pour échanger en toute sécurité une clé symétrique temporaire.
2.  **Chiffrement des données :** Une fois la clé symétrique partagée, toutes les données de la session sont chiffrées/déchiffrées avec cette clé symétrique, car c'est beaucoup plus rapide.

Cette approche permet de bénéficier de la facilité de gestion des clés de l'asymétrique et de la rapidité de la symétrique.

---

<h2 align="left">💡 La Cryptographie Post-Quantique</h2>

Un domaine de recherche actuel et crucial est la **cryptographie post-quantique**. Les algorithmes cryptographiques actuels (RSA, ECC, Diffie-Hellman) reposent sur la difficulté de problèmes mathématiques qui pourraient être résolus efficacement par des ordinateurs quantiques de grande envergure. La cryptographie post-quantique vise à développer de nouveaux algorithmes qui restent sécurisés même face à un attaquant disposant d'un ordinateur quantique.

---

En résumé, la cryptographie est la pierre angulaire de notre sécurité numérique. Comprendre ses principes, ses types (symétrique, asymétrique, fonctions de hachage) et leurs applications est essentiel pour quiconque étudie l'informatique ou la cybersécurité à l'université. Elle est partout, protégeant nos communications, nos transactions bancaires et l'intégrité de nos données.

Avez-vous des questions sur un aspect particulier ou souhaitez-vous explorer des applications spécifiques de la cryptographie ?

---

## 🌐 À propos de moi

- 💡 Passionné par Debian GNU/Linux depuis plusieurs années
- 🎓 Autodidacte, avec un fort esprit de transmission
- 🔐 Intéressé par la cybersécurité, les solutions open source et la performance système
- 🧪 Toujours partant pour tester une nouvelle stack technique

---

<p align="center">
  🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessible à tous.
</p>

