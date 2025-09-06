<div align="center">

  <br></br>
  
  <a href="https://github.com/0xCyberLiTech">
  <img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&size=50&duration=6000&pause=1000000000&color=FF0048&center=true&vCenter=true&width=1100&lines=%3ECYBERSECURITE_" alt="Titre dynamique CYBERSECURITE" />
  </a>
  
  <br></br>

  <h2>Laboratoire numérique pour la cybersécurité, Linux & IT.</h2>
  
  <p align="center">
      <a href="https://0xcyberlitech.github.io/">
        <img src="https://img.shields.io/badge/Portfolio-0xCyberLiTech-181717?logo=github&style=flat-square" alt="Portfolio" />
      </a>
      <a href="https://github.com/0xCyberLiTech">
        <img src="https://img.shields.io/badge/Profil-GitHub-181717?logo=github&style=flat-square" alt="Profil GitHub" />
      </a>
      <a href="https://github.com/0xCyberLiTech/Cybersecurite/releases/latest">
        <img src="https://img.shields.io/github/v/release/0xCyberLiTech/Cybersecurite?label=version" alt="Latest Release" />
      </a>
      <a href="https://github.com/0xCyberLiTech/Cybersecurite/blob/main/CHANGELOG.md">
        <img src="https://img.shields.io/badge/📄%20CHANGELOG-Cybersecurite-blue" alt="Changelog" />
      </a>
      <a href="https://github.com/0xCyberLiTech?tab=repositories">
        <img src="https://img.shields.io/badge/Dépôts-publics-blue?style=flat-square" alt="Dépôts publics" />
      </a>
  </p>

</div>

<div align="center">
  <img src="https://img.icons8.com/fluency/96/000000/cyber-security.png" alt="CyberSec" width="80"/>
</div>

<div align="center">
  <p>
    <strong>Cybersécurité</strong> <img src="https://img.icons8.com/color/24/000000/lock--v1.png"/> • <strong>Linux Debian</strong> <img src="https://img.icons8.com/color/24/000000/linux.png"/> • <strong>Sécurité informatique</strong> <img src="https://img.icons8.com/color/24/000000/shield-security.png"/>
  </p>
</div>

---

<div align="center">
  
## À propos & Objectifs.

</div>

Ce projet propose des solutions innovantes et accessibles en cybersécurité, avec une approche centrée sur la simplicité d’utilisation et l’efficacité. Il vise à accompagner les utilisateurs dans la protection de leurs données et systèmes, tout en favorisant l’apprentissage et le partage des connaissances.

Le contenu est structuré, accessible et optimisé SEO pour répondre aux besoins de :
- 🎓 Étudiants : approfondir les connaissances
- 👨‍💻 Professionnels IT : outils et pratiques
- 🖥️ Administrateurs système : sécuriser l’infrastructure
- 🛡️ Experts cybersécurité : ressources techniques
- 🚀 Passionnés du numérique : explorer les bonnes pratiques

---

# 📘 Cryptographie & Outils pratiques sous Debian 12 & 13

## 1. Installation des outils de base :

Sur Debian 12 (Bookworm) et Debian 13 (Trixie), les paquets nécessaires sont disponibles dans les dépôts officiels :

```bash
sudo apt update
sudo apt install gpg openssl age python3-cryptography -y
```

- **GnuPG (gpg)** → gestion de clés, chiffrement asymétrique, signatures.  
- **OpenSSL** → primitives cryptographiques, certificats SSL/TLS.  
- **age** → outil moderne de chiffrement symétrique et asymétrique, simple d’utilisation.  
- **Python3 + cryptography** → scripts pédagogiques pour expérimenter les algorithmes.  

---

## 2. Travaux pratiques

### 🔑 2.1 Chiffrement symétrique avec OpenSSL
```bash
echo "Message secret" > message.txt
openssl enc -aes-256-cbc -pbkdf2 -in message.txt -out message.enc
openssl enc -d -aes-256-cbc -pbkdf2 -in message.enc -out message_dechiffre.txt
```
👉 Démonstration : même clé pour chiffrer et déchiffrer.  

---

### 🔐 2.2 Chiffrement asymétrique avec GnuPG
```bash
gpg --full-generate-key
gpg --list-keys
gpg --armor --export <identité> > cle_pub.asc
gpg -e -r <identité> message.txt
gpg -d message.txt.gpg > clair.txt
```
👉 Démonstration : clé publique pour chiffrer, clé privée pour déchiffrer.  

---

### 🧩 2.3 Hachage et intégrité
```bash
sha256sum message.txt
openssl dgst -sha512 message.txt
```
👉 Démonstration : modification du fichier → hash complètement différent.  

---

### ✍️ 2.4 Signature numérique avec GPG
```bash
gpg --sign message.txt
gpg --verify message.txt.gpg
```
👉 Démonstration : prouve l’identité de l’expéditeur et l’intégrité du fichier.  

---

### 🔏 2.5 Certificats auto-signés avec OpenSSL
```bash
openssl genrsa -out serveur.key 2048
openssl req -new -x509 -key serveur.key -out serveur.crt -days 365
openssl x509 -in serveur.crt -text -noout
```
👉 Démonstration : rôle des certificats dans HTTPS et importance des autorités de certification.  

---

### ⚡ 2.6 Chiffrement moderne avec age
```bash
age-keygen -o ma_cle.txt
cat ma_cle.txt
age -r <cle_publique> -o secret.age message.txt
age -d -i ma_cle.txt secret.age > message_dechiffre.txt
```
👉 Avantage : outil simple, moderne, très pédagogique.  

---

### 🐍 2.7 Cryptographie avec Python3
Petit script pour illustrer le chiffrement symétrique (Fernet) :

```python
from cryptography.fernet import Fernet

# Génération d'une clé
key = Fernet.generate_key()
cipher = Fernet(key)

# Message
message = b"Bonjour Debian 12 et 13"
chiffre = cipher.encrypt(message)
print("Chiffré :", chiffre)

# Déchiffrement
dechiffre = cipher.decrypt(chiffre)
print("Déchiffré :", dechiffre.decode())
```

👉 Démonstration : lien entre théorie et pratique en programmation.  

---

## 3. TP récapitulatif (Alice & Bob)
🎯 **Projet pédagogique complet :**  
1. Alice génère sa paire de clés GPG.  
2. Bob fait de même.  
3. Ils échangent leurs clés publiques.  
4. Bob envoie un fichier chiffré à Alice avec la clé publique d’Alice.  
5. Alice déchiffre avec sa clé privée.  
6. Alice renvoie un accusé de réception signé.  
7. Bob vérifie la signature.  

---

## 4. Ressources pédagogiques
- 📖 [The GNU Privacy Handbook](https://www.gnupg.org/gph/en/manual.html)  
- 📖 [OpenSSL Cookbook](https://www.feistyduck.com/library/openssl-cookbook/)  
- 📖 [Crypto 101](https://crypto101.io/)  
- 📦 Paquet `python3-cryptography` : <https://cryptography.io/>  

---

<div align="center">
  <a href="https://github.com/0xCyberLiTech" target="_blank" rel="noopener">
    <img src="https://skillicons.dev/icons?i=linux,debian,bash,docker,nginx,git,vim,python,markdown" alt="Skills" width="440">
  </a>
</div>

<div align="center">
  <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>
</div>

