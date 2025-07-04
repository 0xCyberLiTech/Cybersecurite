<p align="center">
  <img src="https://avatars.githubusercontent.com/u/167217017?s=400&u=d983b9423c4eb8cdb9bfe8b14f505be5c894d6bc&v=4" width="150" />
</p>

<h1 align="center">🌐 CYBERSÉCURITÉ - Cryptographie</h1>

<p align="center">
  Un dépôt pédagogique autour des fondamentaux de la cybersécurité.<br>
  📘 Apprentissage – 🔐 Sécurité – 🧠 Compréhension
</p>

---

## 📋 Sommaire

- [01 – Définition de la cryptographie](#01--définition-de-la-cryptographie)
- [02 – Intégrité : le hachage](#02--intégrité--le-hachage)
- [03 – Hachage à clé et stockage sécurisé](#03--hachage-à-clé-et-stockage-sécurisé)
- [04 – Authenticité : la signature numérique](#04--authenticité--la-signature-numérique)
- [05 – Confidentialité : le chiffrement](#05--confidentialité--le-chiffrement)
- [06 – Le chiffrement hybride](#06--le-chiffrement-hybride)
- [🔗 Source](#-source)

---

## 🔎 01 – Définition de la cryptographie

La **cryptographie** est une branche de la cryptologie visant à protéger les messages par des procédés mathématiques :

- 🔐 **Confidentialité**
- ✅ **Authenticité**
- 📦 **Intégrité**

Elle se distingue de la **stéganographie**, qui masque un message au lieu de le rendre illisible.

> 💡 La cryptographie existe depuis l’Antiquité. Les systèmes modernes comme la cryptographie asymétrique sont apparus à la fin du XXe siècle.

---

## 🧱 02 – Intégrité : le hachage

Le **hachage** permet de garantir qu’un message n’a pas été modifié :

- Fonction unidirectionnelle
- Produit une **empreinte unique**
- Permet de vérifier l’intégrité de :
  - Fichiers
  - Répertoires
  - Données téléchargées

### 🔍 Exemple :
> `SHA256(hello.txt)` → `a9f0e61a…`

---

## 🔑 03 – Hachage à clé et stockage sécurisé

Le **hachage à clé** combine une clé secrète avec la fonction de hachage :

- L’empreinte dépend de la **clé utilisée**
- Deux clés différentes → empreintes différentes
- Utilisé pour :
  - ✅ Stockage sécurisé des **mots de passe**
  - ✅ Détection de **modifications non autorisées**

---

## ✍️ 04 – Authenticité : la signature numérique

La **signature numérique** permet de prouver l’origine d’un message et son intégrité :

- Alice utilise sa **clé privée** pour signer
- Bob vérifie avec la **clé publique** d’Alice

### ✉️ Pourquoi signer ?
- Prouver que vous êtes l’auteur d’un message
- Garantir qu’il n’a **pas été modifié**

---

## 🕵️‍♂️ 05 – Confidentialité : le chiffrement

Le **chiffrement** transforme un message en une version illisible sans la bonne clé :

### 📦 Chiffrement symétrique :
- Une **seule clé** partagée
- Très **rapide**
- Nécessite un **canal sécurisé**

### 🔐 Chiffrement asymétrique :
- Utilise une **paire de clés** : publique/privée
- Permet de chiffrer sans partager de secret
- Plus **lent**

---

## ♻️ 06 – Le chiffrement hybride

Le **chiffrement hybride** combine les deux approches :

1. 🔑 Une **clé secrète** est générée
2. Elle est chiffrée avec la **clé publique**
3. Les échanges utilisent ensuite un **chiffrement symétrique**

💡 Exemple d’usage : **HTTPS** (navigation web sécurisée)

<p align="center">
  <img src="./images/confidentialite-01.png" alt="Confidentialité numérique" width="400">
</p>

---

## 🔗 Source

> [CNIL – Comprendre les grands principes de la cryptologie et du chiffrement](https://www.cnil.fr/fr/comprendre-les-grands-principes-de-la-cryptologie-et-du-chiffrement)

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

