<div align="center">

  <a href="https://github.com/0xCyberLiTech/Cybersecurite/blob/main/CYBERSECURITE-13-EPP-EDR-SIEM-SOAR-et-XDR-comprendre-la-diff%C3%A9rence-entre-ces-acronymes.md">
    <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&size=32&pause=1000&color=D14A4A&center=true&vCenter=true&width=800&lines=CYBERSÉCURITÉ;Fondamentaux+%26+Bonnes+Pratiques;Apprendre+•+Comprendre+•+Sécuriser" alt="Typing SVG" />
  </a>

  <p align="center">
    <em>Un dépôt pédagogique - Les piliers de la détection et réponse aux cybermenaces.</em><br>
    <b>📘 Apprentissage – 🔐 Sécurité – 🧠 Compréhension</b>
  </p>

  [![🔗 Profil GitHub](https://img.shields.io/badge/Profil-GitHub-181717?logo=github&style=flat-square)](https://github.com/0xCyberLiTech)
  [![📦 Dernière version](https://img.shields.io/github/v/release/0xCyberLiTech/Cybersecurite?label=version&style=flat-square)](https://github.com/0xCyberLiTech/Cybersecurite/releases/latest)
  [![📄 CHANGELOG](https://img.shields.io/badge/📄%20Changelog-Cybersecurite-blue?style=flat-square)](https://github.com/0xCyberLiTech/Cybersecurite/blob/main/CHANGELOG.md)
  [![📂 Dépôts publics](https://img.shields.io/badge/Dépôts-publics-blue?style=flat-square)](https://github.com/0xCyberLiTech?tab=repositories)
  [![👥 Contributeurs](https://img.shields.io/badge/👥%20Contributeurs-cliquez%20ici-007ec6?style=flat-square)](https://github.com/0xCyberLiTech/Cybersecurite/graphs/contributors)

</div>

---

### 👨‍💻 **À propos de moi.**

> Bienvenue dans mon **laboratoire numérique personnel** dédié à l’apprentissage et à la vulgarisation de la cybersécurité.  
> Passionné par **Linux**, la **cryptographie** et les **systèmes sécurisés**, je partage ici mes notes, expérimentations et fiches pratiques.  
>  
> 🎯 **Objectif :** proposer un contenu clair, structuré et accessible pour étudiants, curieux et professionnels de l’IT.  
> 🔗 [Mon GitHub principal](https://github.com/0xCyberLiTech)

<p align="center">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=linux,debian,bash,docker,nginx,git,vim" alt="Skills" />
  </a>
</p>

---

### 🎯 **Objectif de ce dépôt.**

> Ce dépôt a pour vocation de centraliser un ensemble de notions clés en cybersécurité. Il s’adresse aux passionnés, étudiants, et professionnels souhaitant mieux comprendre les menaces informatiques, apprendre  > à sécuriser leurs environnements et se familiariser avec les concepts et outils de défense.

---

<h2 align="left">💡 Une révolution pour la cyberdéfense ?</h2>
<h3 align="left">👋 Les piliers de la détection et réponse aux cybermenaces</h3>

Ces quatre acronymes sont au cœur de la cybersécurité moderne et représentent des solutions et des approches complémentaires pour protéger les systèmes d'information. Ils évoluent constamment pour faire face à des menaces de plus en plus sophistiquées.

---
<h3 align="left">👋 1. EPP (Endpoint Protection Platform) : La première ligne de défense du terminal</h3>

**Rôle :** L'EPP est la **suite logicielle de sécurité de base installée sur les terminaux** (ordinateurs de bureau, ordinateurs portables, serveurs, mobiles). C'est le "garde du corps" initial de chaque appareil. Son rôle principal est la **prévention** des menaces connues et la détection des activités malveillantes les plus évidentes.

**Fonctionnalités clés :**

* **Antivirus/Antimalware de nouvelle génération (NGAV) :** Utilise des signatures, l'analyse heuristique et l'apprentissage automatique pour détecter et bloquer les logiciels malveillants connus et inconnus.
* **Pare-feu personnel :** Contrôle le trafic réseau entrant et sortant du terminal.
* **Prévention des intrusions basées sur l'hôte (HIPS) :** Surveille l'activité du système et bloque les actions suspectes.
* **Contrôle des périphériques :** Gère l'accès aux ports USB, CD/DVD, etc.
* **Protection Web/Filtre de contenu :** Empêche l'accès à des sites Web malveillants.
* **Chiffrement des données :** Protège les données au repos sur le terminal.

**En bref :** L'EPP est conçu pour empêcher la majorité des menaces d'atteindre le terminal et de s'y exécuter. Il est la fondation de la sécurité des terminaux.

---
<h3 align="left">👋 2. EDR (Endpoint Detection and Response) : L'enquêteur et répondeur du terminal</h3>

**Rôle :** L'EDR prend le relais lorsque l'EPP a potentiellement été contourné ou pour détecter des menaces plus furtives et sophistiquées. Son objectif est la **détection avancée**, l'**investigation approfondie** et la **réponse rapide** sur les terminaux. C'est l'évolution logique de l'EPP.

**Fonctionnalités clés (en complément de l'EPP) :**

* **Surveillance continue :** Collecte en temps réel des données d'activité du terminal (processus, connexions réseau, fichiers accédés, registres modifiés, etc.).
* **Analyse comportementale :** Utilise le Machine Learning et l'IA pour identifier les activités anormales ou suspectes, même pour des menaces inconnues (zero-day, attaques sans fichier ou "fileless attacks").
* **Corrélation d'événements :** Relie différents événements apparemment anodins pour former un "scénario d'attaque".
* **Capacités d'investigation :** Permet aux analystes de sécurité de remonter le fil d'une attaque, de visualiser la chaîne d'événements et de comprendre l'étendue de la compromission.
* **Réponse automatisée/assistée :** Isoler un terminal, terminer des processus malveillants, restaurer des fichiers, etc.
* **Chasse aux menaces (Threat Hunting) :** Fournit les outils aux analystes pour rechercher proactivement des menaces cachées dans les données collectées.

**En bref :** L'EDR est l'œil vigilant et le bras réactif sur les terminaux. Il part du principe qu'une intrusion peut toujours avoir lieu et se concentre sur sa détection précoce et sa remédiation.

---
<h3 align="left">👋 3. NDR (Network Detection and Response) : Le détective du réseau</h3>

**Rôle :** Contrairement à l'EPP et l'EDR qui se concentrent sur les terminaux, le NDR se focalise sur le **trafic réseau**. Il agit comme un "détective" qui surveille toutes les communications au sein du réseau (entre serveurs, entre utilisateurs, vers l'extérieur, etc.) pour détecter des anomalies et des comportements suspects.

**Fonctionnalités clés :**

* **Analyse du trafic réseau :** Capture et analyse le trafic "North-South" (entre l'entreprise et l'extérieur) et "East-West" (mouvements latéraux à l'intérieur du réseau).
* **Détection d'anomalies comportementales :** Utilise le Machine Learning pour établir une ligne de base du comportement réseau normal et détecter les déviations (ex: augmentation inhabituelle du trafic, connexions à des serveurs de commande et contrôle, tentatives d'accès non autorisées).
* **Identification des menaces non basées sur des signatures :** Excellent pour repérer le mouvement latéral des attaquants, l'exfiltration de données, ou les communications de rançongiciels, même si aucun fichier malveillant n'est détecté sur un terminal.
* **Visibilité sur les appareils non managés :** Peut identifier des appareils connectés au réseau qui ne sont pas équipés d'agents EPP/EDR.
* **Intégration avec d'autres outils :** Souvent utilisé en complément des EDR pour une vision plus complète de l'attaque.

**En bref :** Le NDR est essentiel pour détecter les menaces qui ne sont pas visibles au niveau du terminal seul, notamment les phases de reconnaissance, de mouvement latéral et d'exfiltration de données d'une attaque sophistiquée.

---
<h3 align="left">👋 4. XDR (Extended Detection and Response) : L'orchestrateur de la sécurité unifiée</h3>

**Rôle :** Le XDR est l'évolution la plus récente et vise à **unifier la détection et la réponse sur l'ensemble de l'écosystème numérique d'une organisation**. Il agrège et corrèle les données de sécurité provenant de multiples sources (pas seulement les terminaux et le réseau) pour offrir une vue holistique et contextualisée des menaces. C'est le "chef d'orchestre" de la sécurité.

**Fonctionnalités clés :**

* **Collecte de données étendue :** Intègre la télémétrie et les alertes provenant de :
    * **Endpoints (EPP/EDR)**
    * **Réseau (NDR)**
    * **Cloud (charges de travail, applications cloud, identités)**
    * **Email**
    * **Identités (annuaires, systèmes d'authentification)**
    * **Applications (SaaS, logicielles)**
* **Corrélation et contextualisation avancées :** Utilise l'IA et le Machine Learning pour analyser toutes ces données hétérogènes, identifier les liens entre les événements et créer un tableau complet de l'attaque. Cela réduit le bruit (faux positifs) et met en évidence les menaces réelles.
* **Visibilité unifiée :** Fournit un tableau de bord centralisé ("single pane of glass") pour gérer et visualiser toutes les alertes et les incidents de sécurité.
* **Automatisation de la réponse :** Permet des actions de réponse automatisées sur diverses couches (isoler un terminal, bloquer une IP sur un pare-feu, révoquer des accès utilisateur, etc.).
* **Amélioration de la chasse aux menaces :** Offre une plateforme plus riche pour les analystes pour mener des recherches proactives sur l'ensemble de l'infrastructure.

**En bref :** Le XDR est la réponse aux silos de sécurité. Il offre une vision globale des menaces, permettant une détection plus rapide et une réponse plus efficace en automatisant la corrélation et en fournissant un contexte riche. Il est conçu pour les équipes de sécurité qui cherchent à optimiser leurs opérations face à la complexité croissante des cyberattaques.

---
<h3 align="left">👋 4. Tableau comparatif simplifié des rôles :</h3>
### 

| Caractéristique | EPP | EDR | NDR | XDR |
| :-------------- | :------------------------------------- | :------------------------------------------- | :-------------------------------------- | :------------------------------------------------- |
| **Focus** | Prévention sur les terminaux | Détection/Réponse avancée sur les terminaux | Détection/Réponse sur le réseau | Détection/Réponse unifiée (terminaux, réseau, cloud, email, identités...) |
| **Objectif** | Stopper les menaces connues avant l'exécution | Détecter et répondre aux menaces inconnues/complexes sur les terminaux | Détecter les menaces et mouvements latéraux sur le réseau | Détecter et répondre de manière holistique et automatisée sur toutes les sources |
| **Données** | Signatures, heuristiques, comportements de base du terminal | Comportements détaillés du terminal, processus, fichiers, événements | Trafic réseau, flux (NetFlow), paquets | Tous les logs et télémétrie de l'EPP, EDR, NDR, Cloud, Email, Identités |
| **Principale capacité** | Prévention | Détection avancée, Investigation, Réponse | Détection des mouvements latéraux, anomalie réseau | Corrélation, Contextualisation, Automatisation inter-domaines |

En conclusion, ces solutions ne sont pas mutuellement exclusives. Elles représentent une pyramide de défense. L'EPP est la base préventive. L'EDR apporte la profondeur de détection et de réponse sur les terminaux. Le NDR complète avec la visibilité réseau. Enfin, le XDR est l'approche intégrée qui agrège toutes ces informations pour une sécurité plus intelligente, plus rapide et plus efficace à l'échelle de l'entreprise.

---

<p align="center">
  🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessible à tous.
</p>
