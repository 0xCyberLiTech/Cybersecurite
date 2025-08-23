
<div align="center">

  <br></br>
  
  <a href="https://github.com/0xCyberLiTech">
    <img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&size=50&duration=6000&pause=1000000000&color=FF0048&center=true&vCenter=true&width=1100&lines=%3ECYBERLITECH_" alt="Titre dynamique CYBERLITECH" />
  </a>
  
  <br></br>
  
  <p align="center">
    <em>Un dépôt pédagogique autour du monde linux DEBIAN.</em><br>
    <b>📘 Apprentissage – 🔐 Sécurité – 🧠 Compréhension</b>
  </p>
  
  <p align="center">
    <a href="https://0xcyberlitech.github.io/">
      <img src="https://img.shields.io/badge/Portfolio-0xCyberLiTech-181717?logo=github&style=flat-square" alt="Portfolio" />
    </a>
    <a href="https://github.com/0xCyberLiTech">
      <img src="https://img.shields.io/badge/Profil-GitHub-181717?logo=github&style=flat-square" alt="Profil GitHub" />
    </a>
    <a href="https://github.com/0xCyberLiTech/0xcyberlitech/releases/latest">
      <img src="https://img.shields.io/github/v/release/0xCyberLiTech/0xcyberlitech?label=version" alt="Latest Release" />
    </a>
    <a href="https://github.com/0xCyberLiTech/0xcyberlitech/blob/main/CHANGELOG.md">
      <img src="https://img.shields.io/badge/📄%20CHANGELOG-0xcyberlitech-blue" alt="Changelog" />
    </a>
    <a href="https://github.com/0xCyberLiTech?tab=repositories">
      <img src="https://img.shields.io/badge/Dépôts-publics-blue?style=flat-square" alt="Dépôts publics" />
    </a>
  </p>

</div>

---

### 👨‍💻 **À propos de moi.**

> Bienvenue dans mon **laboratoire numérique personnel** dédié à l’apprentissage et à la vulgarisation de la cybersécurité.  
> Passionné par **Linux**, la **cryptographie** et les **systèmes sécurisés**, je partage ici mes notes, expérimentations et fiches pratiques.  
> Proposer un contenu clair, structuré et accessible pour étudiants, curieux et professionnels de l’IT.

<p align="center">
  <img src="https://skillicons.dev/icons?i=linux,debian,bash,docker,nginx,git,vim" alt="Skills" width="300" />
</p>

---

### 🎯 **Objectif de ce dépôt.**

Ce dépôt a pour vocation de centraliser un ensemble de notions clés en cybersécurité. Il s’adresse aux passionnés, étudiants, et professionnels souhaitant mieux comprendre les menaces informatiques, apprendre à sécuriser leurs environnements et se familiariser avec les concepts et outils de défense.

---

### 💡 **Malware**
#### 👋 Qu'est-ce qu'un logiciel malveillant ?

Un **logiciel malveillant** (ou *malware*) est un programme conçu pour nuire à l’utilisateur ou à son système. Il peut :

- infecter un ordinateur ou un appareil mobile,
- se propager à d'autres appareils connectés,
- voler des données, ralentir un système, ou encore chiffrer des fichiers pour exiger une rançon.

Aucun système d’exploitation n’est totalement à l’abri (Windows, macOS, Linux, Android, iOS…).  
Une stratégie de sécurité efficace (correctifs, contrôles d’accès, sauvegardes) est donc essentielle.

---

### ⚠️ **Pourquoi sont-ils si préoccupants ?**

> 💥 Imaginez : vous allumez votre ordinateur au bureau, et un écran rouge vous annonce que vos fichiers ont été chiffrés… avec un compte à rebours et une demande de rançon.

Ce scénario est réel. En mai 2017, le ransomware **WannaCry** a frappé des milliers d’organisations, y compris des hôpitaux.

Mais souvent, les malwares agissent **en silence** : vol de données, surveillance, ralentissement... Leur détection est parfois complexe.

---

### 🧬 **Anatomie d’un malware**

Un logiciel malveillant repose généralement sur deux composants :  
- **Système de distribution** : comment il se propage.  
- **Charge utile** (*payload*) : ce qu’il exécute une fois en place.

#### 🧭 Systèmes de distribution

| Type                      | Description                                  |
|---------------------------|----------------------------------------------|
| **Cheval de Troie**       | Trompe l'utilisateur pour s'installer.      |
| **Ver (worm)**            | Se duplique de façon autonome via les réseaux. |
| **Exploit**               | Exploite une faille logicielle.              |
| **Hameçonnage (phishing)**| Trompe l'utilisateur pour obtenir des accès.|
| **Rootkit / Bootkit**     | Accès privilégié furtif au système.          |

#### 🎯 Charges utiles possibles

| Type                          | Description                                      |
|-------------------------------|------------------------------------------------|
| **Logiciel publicitaire**     | Affiche des publicités non désirées.            |
| **Logiciel espion**           | Espionne les activités de l'utilisateur.        |
| **Botnet**                    | Contrôle l’appareil à distance.                  |
| **Mineur de cryptomonnaie**   | Exploite les ressources CPU/GPU.                 |
| **Rançongiciel (ransomware)** | Chiffre les fichiers et exige une rançon.       |
| **Sabotage**                  | Destruction de fichiers ou systèmes.             |

---

### 🕵️ **Exemples de menaces**

#### 🐴 Chevaux de Troie

Technique classique d’**ingénierie sociale** : une application "utile" cache un malware.  
Exemples : fausse barre d’outils, clavier emoji, clé USB piégée...

#### 🪱 Vers

Se propagent automatiquement via réseaux ou périphériques.  
Historiquement : disquettes, emails, puis réseaux entiers (ex: **Mirai**, **ILOVEYOU**).

#### 💥 Exploits & CVE

Un **exploit** tire parti d'une vulnérabilité connue ou inconnue (0-day) pour infiltrer un système.  
👉 Importance de maintenir les systèmes à jour.

#### 🎣 Hameçonnage

Email frauduleux, site cloné, SMS d'alerte fictive...  
But : obtenir des **informations sensibles** (mots de passe, comptes bancaires...).

#### 🛠️ Rootkits / Bootkits

Permettent un **contrôle total** du système sans être détectés.  
Les bootkits agissent même au niveau du noyau de l’OS.

#### 📢 Publicité & Espionnage

Les **adwares** polluent avec des pubs. Les **spywares** collectent vos données ou frappes clavier (keylogger).  
👉 Risques pour la vie privée et dégradation des performances.

#### 🤖 Botnets

Contrôle d’un appareil à distance pour : DDoS, spam, minage...  
Exemple : **Mirai** (2016) a utilisé des objets connectés (IoT) pour une attaque massive.

#### 💸 Rançongiciels

Chiffrent vos fichiers, puis exigent une rançon (souvent en Bitcoin).  
Exemples : **WannaCry**, **Petya**, **LockerGoga**...

#### 🔥 Autres menaces célèbres

- **Michelangelo (1992)** : efface les disques durs.  
- **ILOVEYOU (2000)** : virus email, détruit fichiers et se propage aux contacts.  
- **Stuxnet (2010)** : attaque sophistiquée ciblant des infrastructures critiques.

---

### 🛡️ **Se défendre efficacement**

- 🔄 **Mettez à jour** vos systèmes régulièrement.  
- 🔐 **Contrôlez les accès** et les droits utilisateurs.  
- 📦 **Utilisez des antivirus et EDR fiables**.  
- 🧠 **Formez les utilisateurs** aux risques et bonnes pratiques.  
- 💾 **Sauvegardez régulièrement** (et testez vos restaurations).

> Le meilleur antivirus reste la **vigilance humaine**.

---

<p align="center">
  <b>🔐 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour une cybersécurité compréhensible et efficace. 🔐</b>
</p>
