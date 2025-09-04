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

# 📊 Suivi et Analyse des logs Squid sous Debian 12 & 13

## 🐙 Introduction

Squid est un proxy HTTP/HTTPS très utilisé dans les environnements réseau (entreprises, écoles, laboratoires).  
Il génère des **fichiers de logs** permettant de suivre :

- Les requêtes web des utilisateurs  
- Les performances du cache  
- Les accès autorisés/refusés  
- Les erreurs rencontrées  

👉 Ces logs se trouvent généralement dans :  
- `/var/log/squid/access.log` → requêtes des clients  
- `/var/log/squid/cache.log` → informations système et erreurs  
- `/var/log/squid/store.log` → gestion du cache  

---

## 🎯 Pourquoi analyser les logs ?

- **Audit et sécurité** : détecter des tentatives d’accès suspectes  
- **Optimisation** : améliorer la configuration du cache  
- **Suivi d’usage** : savoir quels sites sont consultés et par qui  
- **Rapports** : statistiques quotidiennes ou mensuelles  

---

## 🔎 Outils pour analyser les logs

### 1. Analyse en temps réel (CLI)
```bash
tail -f /var/log/squid/access.log
less /var/log/squid/access.log
```

Exemple pour voir les IP actives :
```bash
awk '{print $3}' /var/log/squid/access.log | sort | uniq -c | sort -nr | head
```

---

### 2. SARG (Squid Analysis Report Generator)

- Génère des **rapports HTML** (sites consultés, top utilisateurs, top sites, etc.)  
- Idéal pour l’audit et le reporting  

**Installation :**
```bash
sudo apt update
sudo apt install sarg -y
```

**Configuration (/etc/sarg/sarg.conf) :**
```ini
access_log /var/log/squid/access.log
output_dir /var/www/html/squid-reports
title "Rapport Squid"
```

**Générer un rapport :**
```bash
sudo sarg
```

**Accéder au rapport :**
```
http://<ip-serveur>/squid-reports/
```

---

### 3. Calamaris

- Rapports texte ou HTML légers  
- Analyse statistique (hit/miss, temps de réponse)  

**Installation :**
```bash
sudo apt install calamaris -y
```

**Exemple d’analyse :**
```bash
cat /var/log/squid/access.log | calamaris -a -w -F html > rapport.html
```

---

### 4. SquidAnalyzer

- Rapports HTML détaillés avec graphes  
- Plus moderne que SARG  

**Installation :**
```bash
sudo apt install squidanalyzer -y
```

**Fichier de config :**
`/etc/squidanalyzer/squidanalyzer.conf`

**Analyse :**
```bash
sudo squidanalyzer
```

Rapports disponibles dans `/var/lib/squidanalyzer/www/`.

---

### 5. Centralisation avancée (Graylog / ELK)

- Collecte via `rsyslog` → Elasticsearch  
- Dashboards avec Kibana ou Graylog  
- Idéal pour supervision temps réel + alertes  

---

## 📝 TP : Installation & Utilisation de SARG

1. Installer Squid et générer des logs :  
```bash
sudo apt install squid -y
```

2. Installer SARG :  
```bash
sudo apt install sarg -y
```

3. Configurer le fichier :  
```bash
sudo nano /etc/sarg/sarg.conf
```
- Vérifier `access_log /var/log/squid/access.log`  
- Définir `output_dir /var/www/html/squid-reports`  

4. Générer un rapport :  
```bash
sudo sarg
```

5. Consulter dans un navigateur :  
```
http://<serveur>/squid-reports/
```

---

## ✅ Conclusion

- **Suivi rapide CLI** → tail, awk, grep  
- **Analyse simple HTML** → SARG, Calamaris  
- **Analyse avancée** → SquidAnalyzer  
- **Dashboards modernes** → ELK / Graylog  

👉 Recommandation : commencer par **SARG** (facile, visuel) puis évoluer vers **SquidAnalyzer** ou un SIEM (Graylog/ELK) selon les besoins.

---

<div align="center">
  <a href="https://github.com/0xCyberLiTech" target="_blank" rel="noopener">
    <img src="https://skillicons.dev/icons?i=linux,debian,bash,docker,nginx,git,vim,python,markdown" alt="Skills" width="440">
  </a>
</div>

<div align="center">
  <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>
</div>

