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

</details>
<!-- CIEL-PEDAGOGY-END -->


### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-plan.svg" width="18" height="18" align="absmiddle" alt="" /> **Qu'est-ce qu'une Fiche Réflexe ?**

> En matière de cybersécurité, la préparation est la clé de la résilience.
> Une "fiche réflexe" est un document opérationnel crucial qui guide toute personne au sein d'une organisation sur les premières actions à mener en cas d'incident de sécurité informatique.
> Conçue pour être concise et immédiatement applicable, elle permet de réagir de manière ordonnée et efficace dans une situation de stress, minimisant ainsi les impacts d'une attaque.

---

### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-target.svg" width="18" height="18" align="absmiddle" alt="" /> **Objectifs de la Fiche Réflexe**

> * **Qualifier l'incident :** Confirmer rapidement la nature de l'attaque (rançongiciel, hameçonnage, etc.).
> * **Contenir la menace (Endiguement) :** Isoler les systèmes affectés pour stopper la propagation.
> * **Alerter les bonnes personnes :** Identifier et contacter rapidement les responsables internes et externes.
> * **Préserver les preuves :** Sauvegarder les éléments nécessaires à l'analyse post-incident.
> * **Lancer la remédiation :** Initier les premières étapes du retour à la normale.

---

### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-target.svg" width="18" height="18" align="absmiddle" alt="" /> **Modèle de Fiche Réflexe : Accès Rapide**

<div align="center">

| Étape Clé | Description | Accès Direct |
|:---:|:---|:---:|
| **1. Identification** | Qualifier la nature et l'étendue de l'incident. | [<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/btn-explore.svg" alt="Accéder" />](#1-identification-et-qualification-de-lincident) |
| **2. Endiguement** | Appliquer les actions immédiates pour stopper la menace. | [<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/btn-explore.svg" alt="Accéder" />](#2-actions-immédiates--lendiguement) |
| **3. Alerte** | Contacter les responsables internes et les partenaires externes. | [<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/btn-explore.svg" alt="Accéder" />](#3-alerter--qui-contacter) |
| **4. Preuves** | Préserver les éléments nécessaires à l'analyse forensique. | [<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/btn-explore.svg" alt="Accéder" />](#4-préserver-les-preuves) |
| **5. Communication** | Gérer les communications internes et externes de manière contrôlée. | [<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/btn-explore.svg" alt="Accéder" />](#5-communication) |

</div>

---

### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> **FICHE RÉFLEXE CYBERSÉCURITÉ : PREMIERS GESTES EN CAS D'INCIDENT**

> **ATTENTION : En cas de suspicion d'incident, gardez votre calme et suivez cette procédure. Ne prenez pas d'initiatives non coordonnées.**

#### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-puzzle.svg" width="18" height="18" align="absmiddle" alt="" /> 1. Identification et Qualification de l'Incident

- **Décrivez précisément le problème observé** (ex : fichiers chiffrés, message de rançon, site web défiguré, alertes antivirus, etc.).
- **Notez la date, l'heure et la personne ayant découvert l'incident.**
- **Listez les systèmes, applications ou données impactés** (serveurs, postes, applications métier).
- **Évaluez l'impact sur l'activité** (service interrompu, données inaccessibles, etc.).

#### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-puzzle.svg" width="18" height="18" align="absmiddle" alt="" /> 2. Actions Immédiates : L'Endiguement

| Type d'incident | Actions concrètes à réaliser |
|-----------------|-----------------------------|
| **Rançongiciel** | 1. **Isolez la machine compromise** : débranchez le câble réseau, désactivez le Wi-Fi.<br>2. **Ne l'éteignez pas** : laissez-la allumée pour l'analyse.<br>3. **Ne payez jamais la rançon.** |
| **Hameçonnage** | 1. **Ne cliquez sur rien** (liens, pièces jointes).<br>2. **Ne répondez pas à l'expéditeur.**<br>3. **Signalez le message** comme phishing.<br>4. **Changez immédiatement les mots de passe** si des identifiants ont été saisis.<br>5. **Alertez l'équipe IT.** |
| **Intrusion** | 1. **Changez les mots de passe** des comptes concernés.<br>2. **Déconnectez toutes les sessions actives.**<br>3. **Vérifiez les règles de transfert d'emails et autres modifications suspectes.**<br>4. **Isolez les systèmes impactés.** |
| **Déni de Service (DDoS)** | 1. **Contactez votre hébergeur ou FAI** pour mitigation.<br>2. **Analysez les logs** pour identifier l'origine. |

<h3 id="3-alerter--qui-contacter">3. Alerter : Qui Contacter ?</h3>

- **Responsable Sécurité / Équipe IT** : contactez immédiatement le référent interne.
- **Direction / Cellule de crise** : informez la direction des impacts potentiels.
- **Contacts externes** :
  - Cybermalveillance.gouv.fr pour assistance.
  - Police/Gendarmerie pour dépôt de plainte.
  - CNIL en cas de fuite de données personnelles (notification sous 72h).

#### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-puzzle.svg" width="18" height="18" align="absmiddle" alt="" /> 4. Préserver les Preuves

- **Ne pas éteindre les machines compromises** (sauf consigne contraire).
- **Ne supprimer aucun fichier ou log.**
- **Documentez toutes les actions** (qui, quoi, quand, pourquoi).

#### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-puzzle.svg" width="18" height="18" align="absmiddle" alt="" /> 5. Communication

- **Interne** : informez les collaborateurs des mesures à suivre (ex : ne plus utiliser une application compromise).
- **Externe** : toute communication vers l’extérieur doit être validée par la direction ou le RSSI.
* **Externe :** Préparer les éléments de langage pour les clients ou le public. La communication doit être contrôlée.

---

### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-puzzle.svg" width="18" height="18" align="absmiddle" alt="" /> **Comment Utiliser cette Fiche ?**

> * **Diffusion :** Cette fiche doit être accessible à tous, en version numérique et papier.
> * **Sensibilisation :** Son contenu doit faire l'objet de sessions de sensibilisation régulières.
> * **Mise à jour :** Les informations (notamment les contacts) doivent être vérifiées au moins une fois par an.

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
