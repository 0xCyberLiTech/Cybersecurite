<div align="center">



&nbsp; <br></br>

&nbsp; 

&nbsp; <a href="https://github.com/0xCyberLiTech">

&nbsp; <img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono\&size=50\&duration=6000\&pause=1000000000\&color=FF0048\&center=true\&vCenter=true\&width=1100\&lines=%3ECYBERSECURITE\_" alt="Titre dynamique CYBERSECURITE" />

&nbsp; </a>

&nbsp; 

&nbsp; <br></br>



&nbsp; <h2>Laboratoire numérique pour la cybersécurité, Linux \& IT</h2>

&nbsp; 

&nbsp; <p align="center">

&nbsp;     <a href="https://0xcyberlitech.github.io/">

&nbsp;       <img src="https://img.shields.io/badge/Portfolio-0xCyberLiTech-181717?logo=github\&style=flat-square" alt="Portfolio" />

&nbsp;     </a>

&nbsp;     <a href="https://github.com/0xCyberLiTech">

&nbsp;       <img src="https://img.shields.io/badge/Profil-GitHub-181717?logo=github\&style=flat-square" alt="Profil GitHub" />

&nbsp;     </a>

&nbsp;     <a href="https://github.com/0xCyberLiTech/Cybersecurite/releases/latest">

&nbsp;       <img src="https://img.shields.io/github/v/release/0xCyberLiTech/Cybersecurite?label=version" alt="Latest Release" />

&nbsp;     </a>

&nbsp;     <a href="https://github.com/0xCyberLiTech/Cybersecurite/blob/main/CHANGELOG.md">

&nbsp;       <img src="https://img.shields.io/badge/📄%20CHANGELOG-Cybersecurite-blue" alt="Changelog" />

&nbsp;     </a>

&nbsp;     <a href="https://github.com/0xCyberLiTech?tab=repositories">

&nbsp;       <img src="https://img.shields.io/badge/Dépôts-publics-blue?style=flat-square" alt="Dépôts publics" />

&nbsp;     </a>

&nbsp; </p>



</div>



<!-- Optimisation SEO : mots-clés cybersécurité, sécurité informatique, Linux, Debian, administration système, réseau, IT, cryptographie, open source, pare-feu, proxy, reverse proxy, DNS, SSH, Docker, OpenVAS, SIEM, EDR, XDR, SOAR, pentest, forensic, logs, tutoriels, guides, formation, expertise, supervision, ressources techniques, étudiants, professionnels, passionnés, bonnes pratiques, protection des données, analyse de risques, cyberattaque, défense, conformité, audit, gestion de crise, sensibilisation, monitoring, cloud, virtualisation, DevSecOps. -->



<div align="center">

&nbsp; <img src="https://img.icons8.com/fluency/96/000000/cyber-security.png" alt="CyberSec" width="80"/>

</div>



<div align="center">

&nbsp; <p>

&nbsp;   <strong>Cybersécurité</strong> <img src="https://img.icons8.com/color/24/000000/lock--v1.png"/> • <strong>Linux Debian</strong> <img src="https://img.icons8.com/color/24/000000/linux.png"/> • <strong>Sécurité informatique</strong> <img src="https://img.icons8.com/color/24/000000/shield-security.png"/>

&nbsp; </p>

</div>



---



\## 🚀 À propos \& Objectifs



Ce projet propose des solutions innovantes et accessibles en cybersécurité, avec une approche centrée sur la simplicité d’utilisation et l’efficacité. Il vise à accompagner les utilisateurs dans la protection de leurs données et systèmes, tout en favorisant l’apprentissage et le partage des connaissances.



Le contenu est structuré, accessible et optimisé SEO pour répondre aux besoins de :

\- 🎓 Étudiants : approfondir les connaissances

\- 👨‍💻 Professionnels IT : outils et pratiques

\- 🖥️ Administrateurs système : sécuriser l’infrastructure

\- 🛡️ Experts cybersécurité : ressources techniques

\- 🚀 Passionnés du numérique : explorer les bonnes pratiques



---



\# Wazuh — Présentation \& Procédure d’installation (Debian 12 \& 13)



> \*\*Résumé express\*\* : Wazuh est une plateforme \*\*XDR/SIEM 100% libre\*\* (GPLv2 / ALv2), sans édition payante. Ce guide vous donne un \*\*aperçu illustré\*\* du Dashboard puis une \*\*procédure pas à pas\*\* pour l’installer sur \*\*Debian 12 (Bookworm)\*\* et \*\*Debian 13 (Trixie)\*\*, avec les commandes de vérification, l’ajout d’agents, et les points de sécurité utiles.



---



\## 1) Introduction rapide à Wazuh



\- \*\*Ce que c’est :\*\* une solution \*\*SIEM + EDR\*\* unifiée (XDR) : collecte de logs, corrélation, détection d’intrusions, inventaire, vulnérabilités, FIM (intégrité des fichiers), réponses actives, etc.  

\- \*\*Composants :\*\*  

&nbsp; - \*\*Wazuh Server\*\* (manager + API) — analyse/corrélation.  

&nbsp; - \*\*Wazuh Indexer\*\* (basé OpenSearch) — stockage/Recherche.  

&nbsp; - \*\*Wazuh Dashboard\*\* — interface web.  

&nbsp; - \*\*Wazuh Agent\*\* — capteur multi‑OS sur les hôtes.

\- \*\*Licence :\*\* \*Wazuh est gratuit et open‑source\*. Les composants sont sous \*\*GPLv2\*\* et \*\*Apache 2.0\*\*. \*Aucune fonctionnalité payante cachée\* ; un support pro existe mais \*\*optionnel\*\*.



> Références officielles : Quickstart (licence \& une‑ligne d’installation), White Paper (chapitre Licensing).



---



\## 2) Aperçu visuel du Dashboard (captures)



> Captures issues de la documentation officielle Wazuh.



\*\*2.1 — “Dashboards” (vue d’ensemble)\*\*  

!\[Wazuh Dashboards (overview)](https://documentation.wazuh.com/current/\_images/dashboards1.gif)



\*\*2.2 — Agents > Summary\*\*  

!\[Agents management summary](https://documentation.wazuh.com/current/\_images/endpoints-summary3.png)



\*\*2.3 — Server management > Rules\*\*  

!\[Rules list](https://documentation.wazuh.com/current/\_images/rules3.png)



> Astuce : Les autres sections du Dashboard incluent Endpoint Security, Threat Intelligence, Compliance (PCI/GDPR/NIST…), Cloud (Docker, AWS, O365…), Index management, RBAC/SSO, etc.



---



\## 3) Installation “tout‑en‑un” (serveur + indexer + dashboard) sur Debian 12/13



\### 3.1 Prérequis système (VM conseillée)

\- \*\*OS :\*\* Debian 12 (Bookworm) ou Debian 13 (Trixie), x86\_64/ARM64.  

\- \*\*Ressources indicatives (Quickstart)\*\* :  

&nbsp; - \*1–25 agents :\* 4 vCPU, 8 Go RAM, 50 Go SSD  

&nbsp; - \*25–50 agents :\* 8 vCPU, 8 Go RAM, 100 Go  

&nbsp; - \*50–100 agents :\* 8 vCPU, 8 Go RAM, 200 Go

\- \*\*Accès root/sudo\*\*, Internet sortant.  

\- \*\*Heure à l’heure\*\* (NTP) : `sudo apt-get update \&\& sudo apt-get install -y chrony`  

\- \*\*Pare‑feu\*\* (conseil) : ouvrez \*\*443/TCP\*\* (Dashboard), \*\*1514/TCP\*\* (agents), \*\*1515/TCP\*\* (enrôlement agent), \*\*55000/TCP\*\* (API servidor).



```bash

\# (optionnel) UFW de base

sudo apt-get install -y ufw

sudo ufw allow 443/tcp    # Wazuh Dashboard (HTTPS)

sudo ufw allow 1514/tcp   # Agent -> Manager

sudo ufw allow 1515/tcp   # Enrollment (authd)

sudo ufw allow 55000/tcp  # API Wazuh Server

sudo ufw enable

```



\### 3.2 Installation automatique (assistant officiel)



> Cette méthode déploie \*\*Server + Indexer + Dashboard\*\* sur \*\*une même machine\*\* (idéal pour PoC/PME).



```bash

\# 1) Récupérer \& lancer l’assistant (version 4.12 au moment d’écrire)

curl -sO https://packages.wazuh.com/4.12/wazuh-install.sh

sudo bash ./wazuh-install.sh -a

```



À la fin, le script affiche un \*\*récapitulatif\*\* avec l’URL d’accès, l’utilisateur `admin` et son \*\*mot de passe\*\* initial.  

Vous pouvez aussi retrouver tous les mots de passe générés dans l’archive locale :



```bash

\# Lister les mots de passe générés (API/Indexer/Dashboard)

sudo tar -O -xvf wazuh-install-files.tar wazuh-install-files/wazuh-passwords.txt

```



\*\*Connexion :\*\* ouvrez le navigateur sur `https://<IP\_DU\_SERVEUR>` (certificat auto‑signé par défaut), identifiant `admin`, mot de passe affiché ci‑dessus.



\### 3.3 Sécurisation \& bonnes pratiques post‑install



```bash

\# 1) Changer le mot de passe admin depuis le Dashboard (Settings > Security > Users)

\# 2) (Optionnel) Désactiver le dépôt apt Wazuh pour éviter des mises à jour non maîtrisées

sudo sed -i 's/^deb /#deb /' /etc/apt/sources.list.d/wazuh.list

sudo apt-get update

\# 3) Sauvegarder l’archive wazuh-install-files.tar en lieu sûr (mots de passe \& certs)

\# 4) (Optionnel) Remplacer le certificat du Dashboard par un cert signé (AC interne/Let’s Encrypt)

```



> Note : par défaut, le Dashboard écoute sur \*\*443/TCP\*\*. Vous pouvez changer ce port lors de l’installation avec `--port <num>` si besoin.



\### 3.4 Vérifications rapides



```bash

\# Services essentiels

sudo systemctl status wazuh-manager

sudo systemctl status wazuh-indexer

sudo systemctl status wazuh-dashboard



\# API Wazuh (par défaut sur le serveur, 55000/TCP) — test d’auth simple

\# (remplacer <ADMIN\_PASSWORD> si vous l’avez modifié)

curl -k -u admin:<ADMIN\_PASSWORD> https://localhost:55000/security/user/authenticate

```



Vous devez voir un \*\*token JWT\*\* en retour. Dans le Dashboard, l’onglet \*\*Agents > Summary\*\* doit s’afficher (même vide au début).



---



\## 4) Ajouter un agent Debian 12/13



> Chaque hôte à surveiller a besoin d’un \*\*agent\*\*. Les variables d’installation facilitent l’enrôlement automatique.



\### 4.1 Ajouter le dépôt Wazuh (sur l’endpoint)

```bash

\# GPG + dépôt (Debian/Ubuntu)

curl -s https://packages.wazuh.com/key/GPG-KEY-WAZUH | sudo gpg --no-default-keyring --keyring gnupg-ring:/usr/share/keyrings/wazuh.gpg --import

sudo chmod 644 /usr/share/keyrings/wazuh.gpg

echo "deb \[signed-by=/usr/share/keyrings/wazuh.gpg] https://packages.wazuh.com/4.x/apt/ stable main" | sudo tee /etc/apt/sources.list.d/wazuh.list

sudo apt-get update

```



\### 4.2 Installer + enrôler l’agent

> Remplacez `10.0.0.2` par \*\*l’adresse IP ou FQDN\*\* de votre serveur Wazuh.



```bash

\# Installation avec enrôlement “auto”

sudo WAZUH\_MANAGER="10.0.0.2" apt-get install -y wazuh-agent



\# Activer \& démarrer

sudo systemctl daemon-reload

sudo systemctl enable --now wazuh-agent



\# Vérifier la connexion vers le manager (port 1514/TCP par défaut)

sudo netstat -vatunp | grep wazuh-agentd || true

```



Une fois l’agent connecté, il apparaît dans \*\*Dashboard > Agents > Summary\*\*.  

\*(Bonnes pratiques : version agent ≤ version manager, et « geler » l’agent pour éviter des mises à jour non validées.)\*



```bash

\# (Optionnel) Bloquer les mises à jour côté endpoint

echo "wazuh-agent hold" | sudo dpkg --set-selections

\# ou commenter le dépôt

sudo sed -i 's/^deb/#deb/' /etc/apt/sources.list.d/wazuh.list

sudo apt-get update

```



\### 4.3 Ports à ouvrir côté Manager (rappel)



\- \*\*1514/TCP\*\* : communication agent ↔ manager  

\- \*\*1515/TCP\*\* : enrôlement (authd) par configuration agent  

\- \*\*55000/TCP\*\* : enrôlement via l’API Wazuh Server  

\- \*\*443/TCP\*\* : accès Dashboard (HTTPS)  

\- \*\*9200/TCP\*\* : API Indexer (interne)



---



\## 5) Tests rapides de détection



\### 5.1 Intégrité des fichiers (FIM)

\- Sur l’endpoint, modifiez `/etc/hosts` ou créez un fichier dans un chemin surveillé (ex. `/etc/ssh/sshd\_config`).  

\- Vérifiez l’alerte dans \*\*Security events\*\* (recherche sur `rule.groups:syscheck`).



\### 5.2 Détection basique “brute force SSH”

\- Simulez quelques connexions SSH échouées vers un endpoint Linux.  

\- Recherchez les alertes SSH correspondantes dans Wazuh (ou utilisez les dashboards prêts à l’emploi).



> Tip : vous pouvez enrichir avec \*\*Active Response\*\* (ex. blocage IP) et créer des \*\*dashboards personnalisés\*\* (Explore > Visualize → Dashboard).



---



\## 6) Désinstallation



\### 6.1 Désinstaller la \*\*pile centrale\*\* (serveur)

```bash

\# Depuis la machine où vous avez lancé l’assistant d’installation

sudo bash ./wazuh-install.sh -u

```



\### 6.2 Désinstaller un \*\*agent\*\*

```bash

sudo systemctl stop wazuh-agent

sudo apt-get purge -y wazuh-agent

sudo rm -rf /var/ossec

```



---



\## 7) Notes sur Debian 13 (Trixie)



\- La méthode \*\*Quickstart\*\* et les \*\*paquets APT officiels\*\* fonctionnent généralement sur Debian 13.  

\- Le projet Wazuh suit officiellement l’ajout de nouveaux OS ; en cas de limitation temporaire sur Trixie, déployez les \*\*composants centraux\*\* sur Debian 12 (ou Ubuntu LTS) et gardez Debian 13 pour les \*\*agents\*\*, le temps que la prise en charge complète soit confirmée dans les docs et tests officiels.



---



\## 8) Références officielles utiles



\- \*\*Quickstart\*\* (licences \& install assistée)  

&nbsp; https://documentation.wazuh.com/current/quickstart.html  

\- \*\*Naviguer dans le Dashboard\*\* (captures \& rubriques)  

&nbsp; https://documentation.wazuh.com/current/user-manual/wazuh-dashboard/navigating-the-wazuh-dashboard.html  

\- \*\*Installer le Wazuh Server (pas à pas)\*\*  

&nbsp; https://documentation.wazuh.com/current/installation-guide/wazuh-server/step-by-step.html  

\- \*\*Déployer un agent Linux (APT)\*\*  

&nbsp; https://documentation.wazuh.com/current/installation-guide/wazuh-agent/wazuh-agent-package-linux.html  

\- \*\*Ports par défaut (API/agent/enrôlement)\*\*  

&nbsp; https://documentation.wazuh.com/current/user-manual/agent/agent-enrollment/requirements.html  

\- \*\*Livre blanc — Licence (GPLv2)\*\*  

&nbsp; https://wazuh.com/resources/white-paper/



---



\### Changelog de ce document

\- v1.0 — Première version (Debian 12/13, install assistée, captures, agents).



---



\## 9) Scénarios de test pour un labo personnel



Ces tests vous permettent de \*\*valider rapidement\*\* que vos agents remontent des événements dans le Dashboard.



\### 9.1 Test “brute force SSH” (détection tentative de connexion)

Sur une machine \*\*agent Debian\*\* reliée au manager :



```bash

\# Depuis une autre machine du réseau :

for i in {1..6}; do ssh user@IP\_AGENT 'exit'; done

```



\- Laissez volontairement de \*\*mauvais mots de passe\*\*.  

\- Vérifiez dans le Dashboard : \*\*Security events\*\* → filtrez `rule.groups:ssh`.  

\- Vous devriez voir des alertes de type `sshd: multiple failed logins`.



\### 9.2 Test “FIM” (File Integrity Monitoring)

Sur la même machine agent Debian :



```bash

\# Modifier un fichier sensible surveillé par défaut

sudo sh -c 'echo "# test wazuh fim" >> /etc/hosts'

```



\- Dashboard : cherchez `rule.groups:syscheck`.  

\- Une alerte doit apparaître : \*File added/modified\*.



\### 9.3 Test malware EICAR (antivirus simulé)

Sur une machine agent Windows ou Linux :



```bash

\# Créer le fichier de test EICAR (signature bénigne universelle)

echo "X5O!P%@AP\[4\\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H\*" > /tmp/eicar.com

```



\- Vérifiez que l’alerte est captée dans le Dashboard.  

\- Supprimez le fichier juste après.



\### 9.4 Simulation blocage actif (Active Response)

Si vous activez \*\*Active response\*\* (ex. iptables/WinFW) :  

\- Le test brute force SSH peut déclencher un blocage automatique de l’IP source après plusieurs tentatives.  

\- Vérifiez les journaux côté agent (`/var/ossec/logs/active-responses.log`).



> ⚠️ \*\*Attention\*\* : faites ces tests uniquement dans un environnement \*\*de labo\*\*. Ne jamais utiliser le fichier EICAR ni les tentatives brute force sur une machine en production ou non maîtrisée.



---



\### Mise à jour du document

\- v1.1 — Ajout de la section \*\*Scénarios de test labo\*\* (SSH brute force, FIM, EICAR, Active Response).



---



<div align="center">

&nbsp; <a href="https://github.com/0xCyberLiTech" target="\_blank" rel="noopener">

&nbsp;   <img src="https://skillicons.dev/icons?i=linux,debian,bash,docker,nginx,git,vim,python,markdown" alt="Skills" width="440">

&nbsp; </a>

</div>



<div align="center">

&nbsp; <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>

</div>





