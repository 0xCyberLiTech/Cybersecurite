<div align="center">

  <br></br>
  
  <a href="https://github.com/0xCyberLiTech">
  <img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&size=50&duration=6000&pause=1000000000&color=FF0048&center=true&vCenter=true&width=1100&lines=%3ECYBERSECURITE_" alt="Titre dynamique CYBERSECURITE" />
  </a>
  
  <br></br>

  <h2>Laboratoire numérique pour la cybersécurité, Linux & IT</h2>
  
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

<!-- Optimisation SEO : mots-clés cybersécurité, sécurité informatique, Linux, Debian, administration système, réseau, IT, cryptographie, open source, pare-feu, proxy, reverse proxy, DNS, SSH, Docker, OpenVAS, SIEM, EDR, XDR, SOAR, pentest, forensic, logs, tutoriels, guides, formation, expertise, supervision, ressources techniques, étudiants, professionnels, passionnés, bonnes pratiques, protection des données, analyse de risques, cyberattaque, défense, conformité, audit, gestion de crise, sensibilisation, monitoring, cloud, virtualisation, DevSecOps. -->

<div align="center">
  <img src="https://img.icons8.com/fluency/96/000000/cyber-security.png" alt="CyberSec" width="80"/>
</div>

<div align="center">
  <p>
    <strong>Cybersécurité</strong> <img src="https://img.icons8.com/color/24/000000/lock--v1.png"/> • <strong>Linux Debian</strong> <img src="https://img.icons8.com/color/24/000000/linux.png"/> • <strong>Sécurité informatique</strong> <img src="https://img.icons8.com/color/24/000000/shield-security.png"/>
  </p>
</div>

---

# Wazuh — TP Complet & Guide d’installation (Debian 12 & 13)

> **Licence :** Wazuh est 100% **gratuit et open‑source** (GPLv2 / Apache 2.0).  
> Aucune fonctionnalité payante n’est cachée. Le support commercial existe mais reste optionnel.

---

## 1) Introduction à Wazuh

- **Nature :** SIEM + EDR/XDR open source.  
- **Fonctions clés :**  
  - Collecte et corrélation de journaux.  
  - Détection d’intrusion et vulnérabilités.  
  - Surveillance de l’intégrité des fichiers (FIM).  
  - Dashboards de conformité (PCI, GDPR, HIPAA, NIST).  
  - Réponse active (blocage IP, alertes).  

**Architecture simplifiée :**  

![Architecture Wazuh](https://documentation.wazuh.com/current/_images/deployment-architecture1.png)

---

## 2) Préparation de l’installation (Debian 12/13)

### 2.1 Prérequis système
- OS : Debian 12 (Bookworm) ou Debian 13 (Trixie).  
- Ressources minimales : 4 vCPU / 8 Go RAM / 50 Go disque (lab ≤ 25 agents).  
- Accès root/sudo et Internet sortant.  

Mettez à jour et installez les dépendances :  
```bash
sudo apt-get update && sudo apt-get upgrade -y
sudo apt-get install -y curl gnupg lsb-release ufw chrony
```

### 2.2 Pare-feu conseillé (UFW)
```bash
sudo ufw allow 443/tcp    # Dashboard
sudo ufw allow 1514/tcp   # Agent -> Manager
sudo ufw allow 1515/tcp   # Enrôlement agent
sudo ufw allow 55000/tcp  # API Server
sudo ufw enable
```

---

## 3) Installation du serveur Wazuh (all‑in‑one)

### 3.1 Script officiel
```bash
curl -sO https://packages.wazuh.com/4.12/wazuh-install.sh
sudo bash ./wazuh-install.sh -a
```

🎯 **Résultat attendu :** en fin d’installation, affichage du mot de passe `admin`.  

![Terminal installation Wazuh](https://documentation.wazuh.com/current/_images/install-wizard.png)

### 3.2 Accès au Dashboard
- URL : `https://<IP_SERVEUR>`  
- Identifiant : `admin` / mot de passe généré.

🎯 **Écran attendu (login) :**  
![Login Dashboard](https://documentation.wazuh.com/current/_images/dashboard-login.png)

🎯 **Après connexion (overview) :**  
![Dashboard Overview](https://documentation.wazuh.com/current/_images/dashboards1.gif)

---

## 4) Ajout d’un agent Debian

### 4.1 Installer l’agent
Sur la machine cliente :
```bash
curl -s https://packages.wazuh.com/key/GPG-KEY-WAZUH | sudo gpg --no-default-keyring --keyring gnupg-ring:/usr/share/keyrings/wazuh.gpg --import
echo "deb [signed-by=/usr/share/keyrings/wazuh.gpg] https://packages.wazuh.com/4.x/apt/ stable main" | sudo tee /etc/apt/sources.list.d/wazuh.list
sudo apt-get update

WAZUH_MANAGER="IP_DU_MANAGER" sudo apt-get install -y wazuh-agent
sudo systemctl enable --now wazuh-agent
```

### 4.2 Vérification
🎯 **Écran attendu (Agents Summary) :**  
![Agents Summary](https://documentation.wazuh.com/current/_images/endpoints-summary3.png)

---

## 5) Scénarios de test labo

### 5.1 Brute force SSH
Simulez plusieurs connexions SSH invalides vers un agent.  
🎯 **Écran attendu :** *à insérer votre capture locale*  
![SSH brute force alert](images/ssh-bruteforce.png)

### 5.2 Intégrité fichiers (FIM)
Modifiez `/etc/hosts` sur l’agent Debian.  
🎯 **Écran attendu :** *à insérer votre capture locale*  
![FIM alert](images/fim-alert.png)

### 5.3 Test antivirus (EICAR)
Créez `/tmp/eicar.com` avec la signature EICAR.  
🎯 **Écran attendu :** *à insérer votre capture locale*  
![Malware detection](images/malware-alert.png)

### 5.4 Active Response
Avec Active Response activé, le brute force SSH peut déclencher un blocage IP.  
🎯 **Écran attendu :** *à insérer votre capture locale*  
![Active Response](images/active-response.png)

---

## 6) Exploration du Dashboard

### 6.1 Vulnérabilités
![Vulnerabilities dashboard](https://documentation.wazuh.com/current/_images/vulnerabilities-dashboard.png)

### 6.2 Conformité (PCI, GDPR, NIST)
![Compliance dashboard](https://documentation.wazuh.com/current/_images/compliance-dashboard.png)

### 6.3 Threat Hunting (MITRE ATT&CK)
![Threat Hunting dashboard](https://documentation.wazuh.com/current/_images/mitre-dashboard.png)

### 6.4 Règles et décodeurs
![Rules list](https://documentation.wazuh.com/current/_images/rules3.png)

### 6.5 Logs et recherche
![Logs search](https://documentation.wazuh.com/current/_images/log-data.png)

---

## 7) Désinstallation

### Serveur
```bash
sudo bash ./wazuh-install.sh -u
```

### Agent
```bash
sudo systemctl stop wazuh-agent
sudo apt-get purge -y wazuh-agent
sudo rm -rf /var/ossec
```

---

## 8) Points pratiques labo

- Utilisez une **VM snapshotée** pour tester et revenir en arrière.  
- **Ne pas exposer** le Dashboard directement sur Internet sans cert SSL + proxy inverse.  
- Sauvegardez `wazuh-install-files.tar` (mots de passe initiaux, certs).  
- Debian 13 : agents compatibles, serveur conseillé sur Debian 12 pour plus de stabilité.

---

## 9) Conclusion du TP

- Wazuh = SIEM/EDR **open source complet**.  
- Licence totalement libre (GPLv2 / Apache 2.0).  
- Installation rapide (script `-a`), agents simples à déployer.  
- Dashboard riche (sécurité, vulnérabilités, conformité).  
- Scénarios labo (SSH brute force, FIM, EICAR) permettent de valider la détection.  

🎯 Vous disposez désormais d’un **environnement de test opérationnel** pour pratiquer la détection et la réponse sécurité.

---

## Références utiles

- Quickstart : https://documentation.wazuh.com/current/quickstart.html  
- Dashboard navigation : https://documentation.wazuh.com/current/user-manual/wazuh-dashboard/navigating-the-wazuh-dashboard.html  
- Agents install : https://documentation.wazuh.com/current/installation-guide/wazuh-agent/  
- Ports par défaut : https://documentation.wazuh.com/current/user-manual/agent/agent-enrollment/requirements.html  
- Livre blanc (Licence) : https://wazuh.com/resources/white-paper/  

---

<div align="center">
  <a href="https://github.com/0xCyberLiTech" target="_blank" rel="noopener">
    <img src="https://skillicons.dev/icons?i=linux,debian,bash,docker,nginx,git,vim,python,markdown" alt="Skills" width="440">
  </a>
</div>

<div align="center">
  <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>
</div>

