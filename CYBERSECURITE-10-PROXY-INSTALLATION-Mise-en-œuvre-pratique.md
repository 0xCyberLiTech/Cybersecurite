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

## 🚀 À propos & Objectifs

Ce projet propose des solutions innovantes et accessibles en cybersécurité, avec une approche centrée sur la simplicité d’utilisation et l’efficacité. Il vise à accompagner les utilisateurs dans la protection de leurs données et systèmes, tout en favorisant l’apprentissage et le partage des connaissances.

Le contenu est structuré, accessible et optimisé SEO pour répondre aux besoins de :
- 🎓 Étudiants : approfondir les connaissances
- 👨‍💻 Professionnels IT : outils et pratiques
- 🖥️ Administrateurs système : sécuriser l’infrastructure
- 🛡️ Experts cybersécurité : ressources techniques
- 🚀 Passionnés du numérique : explorer les bonnes pratiques

---

## 📘 10 **Installation et configuration d'un proxy sortant (Squid) sur Debian 12 & 13 :**
## 📋 Prérequis

-   Un serveur Debian 12 (Bookworm) ou Debian 13 (Trixie) à jour
-   Un accès administrateur (`sudo`)
-   Un réseau local (LAN) qui utilisera ce proxy

------------------------------------------------------------------------

## 🔹 Étape 1 : Mettre à jour le système

``` bash
sudo apt update && sudo apt upgrade -y
```

------------------------------------------------------------------------

## 🔹 Étape 2 : Installer Squid

``` bash
sudo apt install squid -y
```

------------------------------------------------------------------------

## 🔹 Étape 3 : Sauvegarder la configuration par défaut

Avant toute modification :

``` bash
sudo cp /etc/squid/squid.conf /etc/squid/squid.conf.backup
```

------------------------------------------------------------------------

## 🔹 Étape 4 : Configurer Squid

Éditer le fichier principal :

``` bash
sudo nano /etc/squid/squid.conf
```

### a) Port d'écoute

Vérifier ou modifier la ligne :

    http_port 3128

### b) Autoriser ton réseau local

Ajouter, par exemple pour le réseau `192.168.1.0/24` :

    acl localnet src 192.168.1.0/24
    http_access allow localnet
    http_access allow localhost

Puis bloquer tout le reste :

    http_access deny all

### c) (Optionnel) Mode transparent

Pour intercepter automatiquement le trafic HTTP :

    http_port 3128 transparent

⚠️ Nécessite aussi une règle de pare-feu (iptables/nftables).

------------------------------------------------------------------------

## 🔹 Étape 5 : Redémarrer Squid

``` bash
sudo systemctl restart squid
sudo systemctl enable squid
```

Vérifier :

``` bash
systemctl status squid
```

------------------------------------------------------------------------

## 🔹 Étape 6 : Configurer les clients

Sur les machines clientes, définir : - IP du serveur Debian (ex :
`192.168.1.10`) - Port `3128`

Test avec `curl` :

``` bash
curl -x http://192.168.1.10:3128 http://ifconfig.me
```

------------------------------------------------------------------------

## 🔹 Étape 7 : (Optionnel) Authentification par utilisateur

### a) Installer l'outil d'authentification

``` bash
sudo apt install apache2-utils -y
```

### b) Créer un utilisateur

``` bash
sudo htpasswd -c /etc/squid/passwd user1
```

👉 Ajouter d'autres utilisateurs avec :

``` bash
sudo htpasswd /etc/squid/passwd user2
```

### c) Modifier `squid.conf`

Ajouter :

    auth_param basic program /usr/lib/squid/basic_ncsa_auth /etc/squid/passwd
    auth_param basic realm Proxy_Auth
    acl authenticated proxy_auth REQUIRED
    http_access allow authenticated

### d) Redémarrer

``` bash
sudo systemctl restart squid
```

------------------------------------------------------------------------

## 🔹 Étape 8 : Vérification des logs

Les connexions sortantes sont enregistrées dans :

    /var/log/squid/access.log

------------------------------------------------------------------------

## ✅ Résumé

-   **Port par défaut** : `3128`
-   **Fichier de configuration** : `/etc/squid/squid.conf`
-   **Authentification optionnelle** via `htpasswd`
-   **Logs** : `/var/log/squid/access.log`
-   Compatible **Debian 12 (Bookworm)** et **Debian 13 (Trixie)**

---

<div align="center">
  <a href="https://github.com/0xCyberLiTech" target="_blank" rel="noopener">
    <img src="https://skillicons.dev/icons?i=linux,debian,bash,docker,nginx,git,vim,python,markdown" alt="Skills" width="440">
  </a>
</div>

<div align="center">
  <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>
</div>

