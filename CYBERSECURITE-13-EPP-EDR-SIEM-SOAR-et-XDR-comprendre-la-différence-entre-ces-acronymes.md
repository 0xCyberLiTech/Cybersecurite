<!-- MASTER-HEADER-START -->
<div align="center">

<a href="https://0xcyberlitech.com/">
  <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/headers/header-cybersecurite.svg" alt="ATELIER CYBERSÉCURITÉ // DÉFENSE LINUX" width="100%" />
</a>

<p align="center">
  <a href="https://0xcyberlitech.com/"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/btn-portal.svg" alt="Portail 0xCyberLiTech.com" width="24%" /></a>
  <a href="https://0xcyberlitech.com/soc-rd.html"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/btn-soc-rd.svg" alt="Livre Blanc SOC Cockpit" width="24%" /></a>
  <a href="https://0xcyberlitech.com/jarvis-rd.html"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/btn-jarvis-rd.svg" alt="Livre Blanc JARVIS IA" width="24%" /></a>
  <a href="https://github.com/0xCyberLiTech?tab=repositories"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/btn-github.svg" alt="Catalogue des 23 Dépôts" width="24%" /></a>
</p>
<p align="center">
  <a href="README.md"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/btn-back-readme.svg" alt="Retour au sommaire du dépôt" width="340" /></a>
</p>

<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/divider-hud.svg" alt="" width="100%" />
</div>
<!-- MASTER-HEADER-END -->

<!-- DEBIAN-TRUTH-START -->
> [!IMPORTANT]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-shield.svg" width="18" height="18" align="absmiddle" alt="" /> ** Matrice Officielle Debian — `Debian 12 (Bookworm)` · `Debian 13 (Trixie)` · `Debian 14 (Forky)`**
> - **Sources Officielles Debian.org (`nftables`) :** `Bookworm (12)` : **`1.0.6-2+deb12u2`** &nbsp;·&nbsp; `Trixie (13 — Stable)` : **`1.1.3-1`** &nbsp;·&nbsp; `Forky (14 — Next-Gen)` : **`1.1.7-3`**
> - **Références Officielles :** [Paquet Debian Trixie (`nftables`)](https://packages.debian.org/trixie/nftables) &nbsp;·&nbsp; [Paquet Debian Forky (`nftables`)](https://packages.debian.org/forky/nftables) &nbsp;·&nbsp; [Documentation Officielle Debian](https://wiki.debian.org/Hardening)
> - **Note d'Ingénierie (Divergence 13 vs 14) :** Sous Debian 13 (Trixie) et Debian 14 (Forky), `net-tools` (`ifconfig`, `netstat`) et `iptables` sont définitivement remplacés par `iproute2` (`ip`, `ss`), `nftables`, `AppArmor` et `journalctl`.

<details>
<summary><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> <b>Afficher les Encarts Ligne de Commande : Debian 13 (Trixie — Stable) vs Debian 14 (Forky — Next-Gen)</b></summary>

#### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> Profil Production Stable — Commandes pour `Debian 13 (Trixie)`
```bash
# Debian 13 (Trixie) — Audit des ports en ecoute (iproute2) & pare-feu nftables :
ss -tulpn && ip -c a
sudo nft list ruleset && sudo journalctl -u ssh -n 50 --no-hostname
```

#### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-rd.svg" width="46" height="16" align="absmiddle" alt="[R&D]" /> Profil Anticipation Next-Gen — Commandes pour `Debian 14 (Forky)`
```bash
# Debian 14 (Forky) — Audit de durcissement systemd & AppArmor actif par defaut :
sudo aa-status
systemd-analyze security | grep -E 'EXPOSED|UNSAFE'
```

</details>
<!-- DEBIAN-TRUTH-END -->

<!-- CIEL-PEDAGOGY-START -->
<details>
<summary><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-puzzle.svg" width="18" height="18" align="absmiddle" alt="" /> <b>Synthèse d'Architecture, Standards Officiels &amp; Diagnostic (Niveau 1 : Fondamentaux · Niveau 2 : Repères · Niveau 3 : Diagnostic)</b></summary>

- **Niveau 1 — Fondamentaux &amp; Principe d'Architecture :** L'ingénierie de **Cybersécurité & Défense en Profondeur (*Defense-in-Depth*)** superpose des barrières de sécurité complémentaires : réduction de la surface d'attaque, durcissement du noyau (`sysctl`), filtrage réseau **Nftables**, détection d'intrusion **Suricata (IDS/IPS)** et remédiation comportementale **CrowdSec / Fail2ban**.
- **Niveau 2 — Repères Officiels (Ports IANA, Fichiers Debian &amp; Commandes de Validation) :** **Commandes de contrôle :** `ss -tulnp` (Audit des sockets en écoute) · `sudo suricata -T -c /etc/suricata/suricata.yaml` (Test syntaxique IDS) · `sudo cscli metrics` (État CrowdSec) · `sudo sysctl --system`.
- **Niveau 3 — Diagnostic d'Incidents &amp; Ingénierie Avancée :** **Diagnostic & Architecture :** Un système **IDS** (*Intrusion Detection System*) analyse le trafic pour lever des alertes qualifiées, tandis qu'un système **IPS** (*Intrusion Prevention System*) ou un bouncer pare-feu intercepte et bloque activement les adresses IP malveillantes au niveau de la couche Netfilter/Nftables.
- **Sources de Vérité Officielles Éditeurs &amp; Standards :** [Guides Officiels ANSSI (Durcissement Linux)](https://cyber.gouv.fr/) &nbsp;·&nbsp; [Documentation Officielle Suricata](https://docs.suricata.io/) &nbsp;·&nbsp; [Documentation Officielle CrowdSec](https://docs.crowdsec.net/)
- **Livres Blancs &amp; 67 Podcasts Audio R&amp;D :** [Portail 0xCyberLiTech](https://0xcyberlitech.com/) &nbsp;·&nbsp; [Livre Blanc SOC Cockpit v5.5](https://0xcyberlitech.com/soc-rd.html) &nbsp;·&nbsp; [Livre Blanc JARVIS Mark-VII](https://0xcyberlitech.com/jarvis-rd.html) &nbsp;·&nbsp; [Blueprint Logiciel &amp; Matériel RTX 5080](https://0xcyberlitech.com/blueprint-jarvis.html)

</details>
<!-- CIEL-PEDAGOGY-END -->


<h2 align="left"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-plan.svg" width="18" height="18" align="absmiddle" alt="" /> Une révolution pour la cyberdéfense ?</h2>
<h3 align="left"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> Les piliers de la détection et réponse aux cybermenaces</h3>

Ces quatre acronymes sont au cœur de la cybersécurité moderne et représentent des solutions et des approches complémentaires pour protéger les systèmes d'information. Ils évoluent constamment pour faire face à des menaces de plus en plus sophistiquées.

---
<h3 align="left"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> 1. EPP (Endpoint Protection Platform) : La première ligne de défense du terminal</h3>

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
<h3 align="left"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> 2. EDR (Endpoint Detection and Response) : L'enquêteur et répondeur du terminal</h3>


**Fonctionnalités clés (en complément de l'EPP) :**

* **Surveillance continue :** Collecte en temps réel des données d'activité du terminal (processus, connexions réseau, fichiers accédés, registres modifiés, etc.).
* **Analyse comportementale :** Utilise le Machine Learning et l'IA pour identifier les activités anormales ou suspectes, même pour des menaces inconnues (zero-day, attaques sans fichier ou "fileless attacks").
* **Corrélation d'événements :** Relie différents événements apparemment anodins pour former un "scénario d'attaque".
* **Capacités d'investigation :** Permet aux analystes de sécurité de remonter le fil d'une attaque, de visualiser la chaîne d'événements et de comprendre l'étendue de la compromission.
* **Réponse automatisée/assistée :** Isoler un terminal, terminer des processus malveillants, restaurer des fichiers, etc.
* **Chasse aux menaces (Threat Hunting) :** Fournit les outils aux analystes pour rechercher proactivement des menaces cachées dans les données collectées.

**En bref :** L'EDR est l'œil vigilant et le bras réactif sur les terminaux. Il part du principe qu'une intrusion peut toujours avoir lieu et se concentre sur sa détection précoce et sa remédiation.

---
<h3 align="left"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> 3. NDR (Network Detection and Response) : Le détective du réseau</h3>

**Rôle :** Contrairement à l'EPP et l'EDR qui se concentrent sur les terminaux, le NDR se focalise sur le **trafic réseau**. Il agit comme un "détective" qui surveille toutes les communications au sein du réseau (entre serveurs, entre utilisateurs, vers l'extérieur, etc.) pour détecter des anomalies et des comportements suspects.

**Fonctionnalités clés :**

* **Analyse du trafic réseau :** Capture et analyse le trafic "North-South" (entre l'entreprise et l'extérieur) et "East-West" (mouvements latéraux à l'intérieur du réseau).
* **Détection d'anomalies comportementales :** Utilise le Machine Learning pour établir une ligne de base du comportement réseau normal et détecter les déviations (ex: augmentation inhabituelle du trafic, connexions à des serveurs de commande et contrôle, tentatives d'accès non autorisées).
* **Identification des menaces non basées sur des signatures :** Excellent pour repérer le mouvement latéral des attaquants, l'exfiltration de données, ou les communications de rançongiciels, même si aucun fichier malveillant n'est détecté sur un terminal.
* **Visibilité sur les appareils non managés :** Peut identifier des appareils connectés au réseau qui ne sont pas équipés d'agents EPP/EDR.
* **Intégration avec d'autres outils :** Souvent utilisé en complément des EDR pour une vision plus complète de l'attaque.

**En bref :** Le NDR est essentiel pour détecter les menaces qui ne sont pas visibles au niveau du terminal seul, notamment les phases de reconnaissance, de mouvement latéral et d'exfiltration de données d'une attaque sophistiquée.

---
<h3 align="left"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> 4. XDR (Extended Detection and Response) : L'orchestrateur de la sécurité unifiée</h3>

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
<h3 align="left"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> 4. Tableau comparatif simplifié des rôles :</h3>
### 

| Caractéristique | EPP | EDR | NDR | XDR |
| :-------------- | :------------------------------------- | :------------------------------------------- | :-------------------------------------- | :------------------------------------------------- |
| **Focus** | Prévention sur les terminaux | Détection/Réponse avancée sur les terminaux | Détection/Réponse sur le réseau | Détection/Réponse unifiée (terminaux, réseau, cloud, email, identités...) |
| **Objectif** | Stopper les menaces connues avant l'exécution | Détecter et répondre aux menaces inconnues/complexes sur les terminaux | Détecter les menaces et mouvements latéraux sur le réseau | Détecter et répondre de manière holistique et automatisée sur toutes les sources |
| **Données** | Signatures, heuristiques, comportements de base du terminal | Comportements détaillés du terminal, processus, fichiers, événements | Trafic réseau, flux (NetFlow), paquets | Tous les logs et télémétrie de l'EPP, EDR, NDR, Cloud, Email, Identités |
| **Principale capacité** | Prévention | Détection avancée, Investigation, Réponse | Détection des mouvements latéraux, anomalie réseau | Corrélation, Contextualisation, Automatisation inter-domaines |

En conclusion, ces solutions ne sont pas mutuellement exclusives. Elles représentent une pyramide de défense. L'EPP est la base préventive. L'EDR apporte la profondeur de détection et de réponse sur les terminaux. Le NDR complète avec la visibilité réseau. Enfin, le XDR est l'approche intégrée qui agrège toutes ces informations pour une sécurité plus intelligente, plus rapide et plus efficace à l'échelle de l'entreprise.

<!-- MASTER-FOOTER-START -->
<div align="center">
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/divider-hud.svg" alt="" width="100%" />

<a href="https://0xcyberlitech.com/">
  <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/footer-master.svg" alt="0xCyberLiTech — Architecture Cyberdéfense, Ingénierie Déterministe & IA Souveraine" width="100%" />
</a>

<p align="center"><a href="https://0xcyberlitech.com/"><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/badge-antigravity.svg" alt="Architecturé par Marc & Antigravity (Google DeepMind)" width="520" /></a></p>

<sub><b>Architecturé &amp; Forgé par Marc &amp; Antigravity (Google DeepMind)</b> &nbsp;·&nbsp; <a href="https://0xcyberlitech.com/"><b>0xcyberlitech.com</b></a> &nbsp;·&nbsp; <a href="https://0xcyberlitech.com/soc-rd.html">Architecture SOC Cockpit v5.5</a> &nbsp;·&nbsp; <a href="https://0xcyberlitech.com/jarvis-rd.html">Architecture JARVIS Mark-VII</a> &nbsp;·&nbsp; <a href="https://0xcyberlitech.com/blueprint-jarvis.html">Blueprint Matériel RTX 5080</a></sub>

</div>
<!-- MASTER-FOOTER-END -->
