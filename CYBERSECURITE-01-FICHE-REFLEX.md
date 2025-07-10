<div align="center">

<a href="https://github.com/0xCyberLiTech/Cybersecurite/blob/main/CYBERSECURITE-01-FICHE-REFLEX.md">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&size=32&pause=1000&color=D14A4A&center=true&vCenter=true&width=850&lines=FICHE+RÉFLEXE+:+CYBERSÉCURITÉ;Premiers+gestes+en+cas+d'incident;Qualifier+•+Contenir+•+Alerter" alt="Typing SVG" />
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

### 💡 **Qu'est-ce qu'une Fiche Réflexe ?**

> En matière de cybersécurité, la préparation est la clé de la résilience.
> Une "fiche réflexe" est un document opérationnel crucial qui guide toute personne au sein d'une organisation sur les premières actions à mener en cas d'incident de sécurité informatique.
> Conçue pour être concise et immédiatement applicable, elle permet de réagir de manière ordonnée et efficace dans une situation de stress, minimisant ainsi les impacts d'une attaque.

---

### 🎯 **Objectifs de la Fiche Réflexe**

> * **Qualifier l'incident :** Confirmer rapidement la nature de l'attaque (rançongiciel, hameçonnage, etc.).
> * **Contenir la menace (Endiguement) :** Isoler les systèmes affectés pour stopper la propagation.
> * **Alerter les bonnes personnes :** Identifier et contacter rapidement les responsables internes et externes.
> * **Préserver les preuves :** Sauvegarder les éléments nécessaires à l'analyse post-incident.
> * **Lancer la remédiation :** Initier les premières étapes du retour à la normale.

---

### 🧭 **Modèle de Fiche Réflexe : Accès Rapide**

<div align="center">

| Étape Clé | Description | Accès Direct |
|:---:|:---|:---:|
| **1. Identification** | Qualifier la nature et l'étendue de l'incident. | [<img src="https://img.shields.io/badge/ACCÉDER-blue?style=for-the-badge&logo=github&logoColor=white">](#1-identification-et-qualification-de-lincident) |
| **2. Endiguement** | Appliquer les actions immédiates pour stopper la menace. | [<img src="https://img.shields.io/badge/ACCÉDER-blue?style=for-the-badge&logo=github&logoColor=white">](#2-actions-immédiates--lendiguement) |
| **3. Alerte** | Contacter les responsables internes et les partenaires externes. | [<img src="https://img.shields.io/badge/ACCÉDER-blue?style=for-the-badge&logo=github&logoColor=white">](#3-alerter--qui-contacter) |
| **4. Preuves** | Préserver les éléments nécessaires à l'analyse forensique. | [<img src="https://img.shields.io/badge/ACCÉDER-blue?style=for-the-badge&logo=github&logoColor=white">](#4-préserver-les-preuves) |
| **5. Communication** | Gérer les communications internes et externes de manière contrôlée. | [<img src="https://img.shields.io/badge/ACCÉDER-blue?style=for-the-badge&logo=github&logoColor=white">](#5-communication) |

</div>

---

### 📜 **FICHE RÉFLEXE CYBERSÉCURITÉ : PREMIERS GESTES EN CAS D'INCIDENT**

> **ATTENTION : En cas de suspicion d'incident, gardez votre calme et suivez cette procédure. Ne prenez pas d'initiatives non coordonnées.**

<h3 id="1-identification-et-qualification-de-lincident"> 👋 1. Identification et Qualification de l'Incident</h3>

* **Quel est le problème observé ?** (Ex: Fichiers chiffrés, message de demande de rançon, site web défiguré, lenteurs extrêmes, alertes antivirus, etc.)
* **Quand le problème a-t-il été découvert et par qui ?**
* **Quels sont les systèmes, applications ou données impactés ?** (Serveurs, postes de travail, applications métier, etc.)
* **L'activité de l'entreprise est-elle perturbée ? Si oui, comment ?**

<h3 id="2-actions-immédiates--lendiguement"> 👋 2. Actions Immédiates : L'Endiguement</h3>

| Type d'incident suspecté | Actions immédiates à réaliser |
| :--- | :--- |
| **Rançongiciel (Ransomware)** | 1. **Isoler immédiatement la ou les machines compromises :**<br>   - **Débrancher le câble réseau (Ethernet).**<br>   - **Désactiver le Wi-Fi.**<br>2. **NE PAS ÉTEINDRE** la machine. Laissez-la en l'état pour l'analyse forensique.<br>3. **NE PAS PAYER LA RANÇON.** |
| **Hameçonnage (Phishing)** | 1. **Ne pas cliquer sur les liens, ni ouvrir les pièces jointes.**<br>2. **Ne pas répondre à l'expéditeur.**<br>3. **Signaler le message** comme "hameçonnage" dans votre client de messagerie.<br>4. Si des identifiants ont été saisis : **changer immédiatement le mot de passe** du compte concerné et de tous les autres comptes utilisant le même mot de passe.<br>5. **Alerter** l'équipe IT. |
| **Intrusion / Compromission** | 1. **Changer immédiatement les mots de passe** des comptes suspectés et des comptes administrateurs.<br>2. **Déconnecter toutes les sessions actives** du compte compromis.<br>3. **Vérifier les règles de transfert d'emails** et autres modifications suspectes.<br>4. **Isoler les systèmes** sur lesquels le compte a été utilisé. |
| **Déni de Service (DDoS)** | 1. **Contacter immédiatement votre hébergeur ou FAI.** Ils disposent des outils pour mitiger l'attaque.<br>2. **Analyser les logs** pour identifier l'origine et le type d'attaque (si possible). |

<h3 id="3-alerter--qui-contacter"> 👋 3. Alerter : Qui Contacter ?</h3>

* **Responsable de la Sécurité (RSSI) / Équipe Informatique :**
    * **Nom :** `[Nom du contact interne]`
    * **Téléphone :** `[Numéro de téléphone]`
    * **Email :** `[Email du contact]`
* **Direction / Cellule de crise :**
    * Informer la direction de l'incident et de ses impacts potentiels.
* **Contacts Externes (selon la gravité) :**
    * **Cybermalveillance.gouv.fr :** Pour obtenir de l'aide et être mis en relation avec des prestataires.
    * **Forces de l'ordre (Police/Gendarmerie) :** Pour un dépôt de plainte (`0 800 811 414` - Info Escroqueries).
    * **CNIL :** En cas de violation de données personnelles, notification obligatoire sous 72h.

<h3 id="4-préserver-les-preuves"> 👋 4. Préserver les Preuves</h3>

* **Ne pas éteindre les machines compromises** (sauf instruction contraire) pour préserver les preuves en mémoire vive (RAM).
* **Ne supprimer aucun fichier ou log.**
* **Noter chronologiquement toutes les actions entreprises :** Qui a fait quoi, quand et pourquoi.

<h3 id="5-communication"> 👋 5. Communication</h3>

* **Interne :** Informer les collaborateurs des mesures à prendre (ex: "Ne plus utiliser telle application").
* **Externe :** Préparer les éléments de langage pour les clients ou le public. La communication doit être contrôlée.

---

### ⚙️ **Comment Utiliser cette Fiche ?**

> * **Diffusion :** Cette fiche doit être accessible à tous, en version numérique et papier.
> * **Sensibilisation :** Son contenu doit faire l'objet de sessions de sensibilisation régulières.
> * **Mise à jour :** Les informations (notamment les contacts) doivent être vérifiées au moins une fois par an.

---

<p align="center">
  <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>
</p>
