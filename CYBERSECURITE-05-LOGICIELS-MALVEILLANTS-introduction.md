<div align="center">

<a href="https://github.com/0xCyberLiTech/Cybersecurite/blob/main/CYBERSECURITE-05-LOGICIELS-MALVEILLANTS-introduction.md">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&size=32&pause=1000&color=D14A4A&center=true&vCenter=true&width=1000&lines=LOGICIELS+MALVEILLANTS+:+INTRODUCTION;Comprendre+les+menaces+et+leurs+objectifs;Détecter,+protéger,+réagir" alt="Typing SVG" />
</a>

<p align="center">
  <em>Un dépôt pédagogique autour des fondamentaux de la cybersécurité.</em><br>
  <b>📘 Apprentissage – 🔐 Sécurité – 🧠 Compréhension</b>
</p>

</div>

---

### 👨‍💻 **À propos de moi.**

> Ce dépôt constitue mon laboratoire numérique où je consigne rigoureusement mes apprentissages et expérimentations. Passionné par l'écosystème Linux > et la cybersécurité, je
> documente mon parcours et mes projets sur mon GitHub. Vous y trouverez des guides pratiques sur la supervision (Zabbix,
> Nagios), la conteneurisation (Docker), la cryptographie les algorithmes de chiffrement symétrique (AES, ChaCha20) et asymétrique (RSA, ECC).  et la
> sécurisation de serveurs Debian. Mon objectif : partager mes connaissances de manière claire et pédagogique. N'hésitez pas à y jeter un œil : https://github.com/0xcyberlitech

<p align="center">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=linux,debian,bash,docker,nginx,grafana,prometheus,git,vim" />
  </a>
</p>

---

### 🎯 **Objectif de ce dépôt.**

> Ce dépôt a pour vocation de centraliser un ensemble de notions clés en cybersécurité. Il s’adresse aux passionnés, étudiants, et professionnels souhaitant mieux comprendre les menaces informatiques, apprendre  > à sécuriser leurs environnements et se familiariser avec les concepts et outils de défense.

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
  <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>
</p>
