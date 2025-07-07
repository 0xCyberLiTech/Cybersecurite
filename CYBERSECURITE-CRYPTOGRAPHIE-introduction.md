<div align="center">

<a href="https://github.com/0xCyberLiTech">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&size=32&pause=1000&color=33FF33&center=true&vCenter=true&width=1000&lines=CRYPTOGRAPHIE+%26+CYBERSÉCURITÉ;Chiffrement+•+Hachage+•+Authentification;Comprendre+les+bases+pour+mieux+protéger" alt="Typing SVG" />
</a>

<p align="center">
  <em>Un dépôt pédagogique autour des fondamentaux de la cybersécurité.</em><br>
  <b>📘 Apprentissage – 🔐 Sécurité – 🧠 Compréhension</b>
</p>

</div>

---

### 👨‍💻 **À propos de moi.**

> Ce dépôt constitue mon laboratoire numérique où je consigne rigoureusement mes apprentissages et expérimentations.
> Passionné par l'écosystème Linux et la cybersécurité, je documente mon parcours et mes projets sur mon GitHub.
> Vous y trouverez des guides pratiques sur la supervision (Zabbix, Nagios), la conteneurisation (Docker) et la sécurisation de serveurs Debian.
> Mon objectif : partager mes connaissances de manière claire et pédagogique.
> N'hésitez pas à y jeter un œil : https://github.com/0xcyberlitech

<p align="center">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=linux,debian,bash,docker,nginx,grafana,prometheus,git,vim" />
  </a>
</p>

---

### 🎯 **Objectif de ce dépôt.**

> Ce dépôt a pour vocation de centraliser un ensemble de notions clés en cybersécurité. Il s’adresse aux passionnés, étudiants, et professionnels souhaitant mieux comprendre les menaces informatiques, apprendre  > à sécuriser leurs environnements et se familiariser avec les concepts et outils de défense.

---

## 💡 **La cryptographie :**

### I. Fondamentaux de la Cybersécurité

### 👋 L'Art du Secret et de la Sécurité Numérique

La cryptographie, du grec *kryptos* (caché) et *graphein* (écrire), est la science et l'art de concevoir des méthodes permettant de **protéger l'information**.  
Historiquement, son but était de garantir le secret des communications. Aujourd'hui, elle est la pierre angulaire de la sécurité de nos systèmes numériques.

On distingue principalement deux grands domaines :  
1. La **cryptographie symétrique** (ou à clé secrète)  
2. La **cryptographie asymétrique** (ou à clé publique)

---

## 💡 Pourquoi la cryptographie est-elle essentielle ?

Dans un monde hyper-connecté, la cryptographie garantit quatre propriétés fondamentales :

1. **Confidentialité :** Seules les personnes autorisées accèdent à l'information (ex : chiffrer un email).  
2. **Intégrité :** L'information n'est pas modifiée ou altérée (ex : vérifier qu’un fichier n’est pas corrompu).  
3. **Authentification :** Vérifier l'identité d’un utilisateur, système ou information (ex : communiquer avec le bon serveur bancaire).  
4. **Non-répudiation :** Empêcher une entité de nier une action effectuée (ex : prouver la signature d’un contrat numérique).

---

## 💡 I. La Cryptographie Symétrique : La Clé Partagée

C’est la forme la plus ancienne, où la **même clé** sert à **chiffrer** et **déchiffrer**.

### 👋 Comment ça marche ?

Imaginez un cadenas avec une clé unique. Le message est enfermé dans une boîte verrouillée par ce cadenas. Seule la clé partagée permet d’ouvrir la boîte.

- **Chiffrement :** Message clair (M) + Clé (K) → Message chiffré (C)  
- **Déchiffrement :** Message chiffré (C) + Clé (K) → Message clair (M)

### 👋 Algorithmes courants

- **AES (Advanced Encryption Standard)** : Norme actuelle, sécurisée et rapide, utilisée partout.  
- **DES / 3DES** : Plus anciens, aujourd’hui dépréciés ou en fin de vie.

### 👋 Avantages

- **Rapidité** et **efficacité** : Idéal pour chiffrer de grandes quantités de données.  
- **Faible consommation** de ressources.

### 👋 Inconvénients

- **Gestion des clés difficile** : La distribution sécurisée de la clé est un défi majeur.  
- **Scalabilité limitée** : Pour N participants, il faut N×(N−1)/2 clés.

---

## 💡 II. La Cryptographie Asymétrique (Clé Publique)

Introduite dans les années 1970, elle utilise une **paire de clés** mathématiquement liées : une clé publique et une clé privée.

### 👋 Comment ça marche ?

- **Clé publique :** Partagée librement, sert à chiffrer ou vérifier une signature.  
- **Clé privée :** Secrète, sert à déchiffrer ou signer numériquement.

### 👋 Scénarios d’utilisation

1. **Confidentialité :**  
   Alice chiffre un message avec la clé publique de Bob → Bob déchiffre avec sa clé privée.  
   *Pas besoin d’échanger une clé secrète.*

2. **Authentification & Intégrité :**  
   Alice signe un message avec sa clé privée → Bob vérifie avec la clé publique d’Alice.  
   *Garantit l’identité de l’expéditeur et l’intégrité.*

### 👋 Algorithmes courants

- **RSA :** Basé sur la factorisation de grands nombres premiers.  
- **ECC (Elliptic Curve Cryptography) :** Clés plus courtes, adapté aux appareils limités.  
- **Diffie-Hellman :** Spécialement pour échange sécurisé de clés symétriques.

### 👋 Avantages

- **Distribution des clés simplifiée.**  
- **Non-répudiation** grâce aux signatures numériques.  
- **Résout le problème de l’échange de clés symétriques.**

### 👋 Inconvénients

- **Plus lent** que la cryptographie symétrique.  
- **Clés plus longues** nécessaires pour un niveau de sécurité équivalent.

---

## 💡 III. Fonctions de Hachage Cryptographique : L’Empreinte Numérique

Algorithmes produisant une **empreinte numérique** de taille fixe à partir d’une entrée arbitraire.

### 👋 Propriétés essentielles

1. **Déterministe** : même entrée → même sortie.  
2. **Rapide à calculer.**  
3. **Résistance à la préimage** : difficile de retrouver l’entrée depuis le hachage.  
4. **Résistance à la seconde préimage** : difficile de trouver une autre entrée produisant le même hachage.  
5. **Résistance aux collisions** : difficile de trouver deux entrées différentes avec le même hachage.

### 👋 Algorithmes courants

- **SHA-2 (SHA-256, SHA-512)** : largement utilisés.  
- **SHA-3** : nouvelle famille standard.  
- **MD5 / SHA-1** : obsolètes ou dépréciés.

### 👋 Utilisations

- Vérification d’intégrité.  
- Stockage sécurisé des mots de passe (hachage salé).  
- Signatures numériques (signer le hachage).  
- Blockchain et cryptomonnaies.

---

## 💡 IV. L’Utilisation Combinée : Le "Chiffrement Hybride"

La plupart des systèmes sécurisés utilisent une approche hybride :

1. **Échange de clé symétrique** via cryptographie asymétrique (ex : RSA, Diffie-Hellman).  
2. **Chiffrement des données** avec la clé symétrique (rapide et efficace).

---

## 💡 La Cryptographie Post-Quantique

Recherche de nouveaux algorithmes résistants aux ordinateurs quantiques qui pourraient casser les méthodes actuelles (RSA, ECC, etc.). Un enjeu majeur pour la sécurité future.

---

En résumé, la cryptographie est la pierre angulaire de la sécurité numérique, protégeant nos communications, nos données et notre identité dans un monde connecté.

---

<p align="center">
  🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous.
</p>
