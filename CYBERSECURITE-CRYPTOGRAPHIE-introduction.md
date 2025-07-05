<p align="center">
  <img src="https://avatars.githubusercontent.com/u/167217017?s=400&u=d983b9423c4eb8cdb9bfe8b14f505be5c894d6bc&v=4" width="150" />
</p>

# 🌐 CYBERSÉCURITÉ - CRYPTOGRAPHIE 🌐
## INTRODUCTION

<p align="center">
  Un dépôt pédagogique autour des fondamentaux de la cybersécurité.<br>
  📘 Apprentissage – 🔐 Sécurité – 🧠 Compréhension
</p>

---

## 💡 La Cryptographie

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

## 🌐 À propos de moi

- 💡 Passionné par Debian GNU/Linux depuis plusieurs années  
- 🎓 Autodidacte, avec un fort esprit de transmission  
- 🔐 Intéressé par la cybersécurité, les solutions open source et la performance système  
- 🧪 Toujours partant pour tester une nouvelle stack technique

---

<p align="center">
  🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous.
</p>
