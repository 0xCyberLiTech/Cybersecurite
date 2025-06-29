<p align="center">
  <img src="./images/Cloud-et-securite.png" alt="Cloud et Sécurité" width="300">
</p>

<h1 align="center">🛡️ CYBERSÉCURITÉ : Programmes Malveillants</h1>

<p align="center">
  Introduction aux logiciels malveillants : types, modes de propagation, et méthodes de protection.
</p>

---

## 💡 Qu'est-ce qu'un logiciel malveillant ?

Un **logiciel malveillant** (ou *malware*) est un programme conçu pour nuire à l’utilisateur ou à son système. Il peut :

- infecter un ordinateur ou un appareil mobile,
- se propager à d'autres appareils connectés,
- voler des données, ralentir un système, ou encore chiffrer des fichiers pour exiger une rançon.

Aucun système d’exploitation n’est totalement à l’abri (Windows, macOS, Linux, Android, iOS…).  
Une stratégie de sécurité efficace (correctifs, contrôles d’accès, sauvegardes) est donc essentielle.

---

## ⚠️ Pourquoi sont-ils si préoccupants ?

> 💥 Imaginez : vous allumez votre ordinateur au bureau, et un écran rouge vous annonce que vos fichiers ont été chiffrés… avec un compte à rebours et une demande de rançon.

Ce scénario est réel. En mai 2017, le ransomware **WannaCry** a frappé des milliers d’organisations, y compris des hôpitaux.

Mais souvent, les malwares agissent **en silence** : vol de données, surveillance, ralentissement... Leur détection est parfois complexe.

---

## 🧬 Anatomie d’un malware

Un logiciel malveillant repose généralement sur deux composants :
- **Système de distribution** : comment il se propage.
- **Charge utile** (*payload*) : ce qu’il exécute une fois en place.

### 🧭 Systèmes de distribution

| Type                      | Description |
|---------------------------|-------------|
| **Cheval de Troie**       | Trompe l'utilisateur pour s'installer. |
| **Ver (worm)**            | Se duplique de façon autonome via les réseaux. |
| **Exploit**               | Exploite une faille logicielle. |
| **Hameçonnage (phishing)**| Trompe l'utilisateur pour obtenir des accès. |
| **Rootkit / Bootkit**     | Accès privilégié furtif au système. |

### 🎯 Charges utiles possibles

| Type                          | Description |
|-------------------------------|-------------|
| **Logiciel publicitaire**     | Affiche des publicités non désirées. |
| **Logiciel espion**           | Espionne les activités de l'utilisateur. |
| **Botnet**                    | Contrôle l’appareil à distance. |
| **Mineur de cryptomonnaie**   | Exploite les ressources CPU/GPU. |
| **Rançongiciel (ransomware)** | Chiffre les fichiers et exige une rançon. |
| **Sabotage**                  | Destruction de fichiers ou systèmes. |

---

## 🕵️ Exemples de menaces

### 🐴 Chevaux de Troie

Technique classique d’**ingénierie sociale** : une application "utile" cache un malware.  
Exemples : fausse barre d’outils, clavier emoji, clé USB piégée...

### 🪱 Vers

Se propagent automatiquement via réseaux ou périphériques.  
Historiquement : disquettes, puis emails, et aujourd’hui réseaux entiers (ex: **Mirai**, **ILOVEYOU**).

### 💥 Exploits & CVE

Un **exploit** tire parti d'une vulnérabilité connue ou inconnue (0-day) pour infiltrer un système.  
👉 Importance de maintenir les systèmes à jour.

### 🎣 Hameçonnage

Email frauduleux, site cloné, SMS d'alerte fictive...  
Le but est d’obtenir des **informations sensibles** (mots de passe, comptes bancaires...).

### 🛠️ Rootkits / Bootkits

Permettent un **contrôle total** du système sans être détectés.  
Les bootkits agissent même au niveau du noyau de l’OS.

### 📢 Publicité & Espionnage

Les **adwares** polluent avec des pubs. Les **spywares** collectent vos données ou frappes clavier (keylogger).  
👉 Risques pour la vie privée + performance système dégradée.

### 🤖 Botnets

Contrôle d’un appareil à distance pour : DDoS, spam, minage...  
Exemple : **Mirai** en 2016 a utilisé des objets connectés (IoT) pour une attaque massive.

### 💸 Rançongiciels

Chiffrent vos fichiers, puis exigent une rançon (souvent en Bitcoin).  
Exemples célèbres : **WannaCry**, **Petya**, **LockerGoga**...

### 🔥 Autres menaces

- **Michelangelo (1992)** : efface les disques durs.
- **ILOVEYOU (2000)** : virus par email, détruit fichiers et envoie à vos contacts.
- **Stuxnet (2010)** : attaque complexe ciblant les centrifugeuses iraniennes — probablement d'origine étatique.

---

## 🛡️ Se défendre efficacement

- 🔄 **Mettez à jour** vos systèmes (correctifs de sécurité)
- 🔐 **Contrôlez les accès**
- 📦 **Utilisez des antivirus et EDR fiables**
- 🧠 **Formez les utilisateurs**
- 💾 **Sauvegardez régulièrement** (et testez vos sauvegardes)

> Le meilleur antivirus reste la **vigilance humaine**.

---

<p align="center">
  🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour une cybersécurité accessible à tous.
</p>
