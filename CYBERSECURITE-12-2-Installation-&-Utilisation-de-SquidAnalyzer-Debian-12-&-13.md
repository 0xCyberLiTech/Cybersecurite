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

## 📝 Installation & Utilisation de SquidAnalyzer (Debian 12 & 13)

- Installer **SquidAnalyzer**  
- Configurer l’outil pour analyser les logs Squid  
- Générer et consulter un **rapport HTML**  

---

## 1️⃣ Installation de Squid et génération de logs

Si Squid n’est pas déjà installé :  
```bash
sudo apt update
sudo apt install squid -y
```

Vérification du service :  
```bash
systemctl status squid
```

👉 Les logs sont générés par défaut dans :  
- `/var/log/squid/access.log`  

---

## 2️⃣ Installation de SquidAnalyzer

```bash
sudo apt install squidanalyzer -y
```

Cela installe :  
- le binaire `squidanalyzer`  
- la config par défaut : `/etc/squidanalyzer/squidanalyzer.conf`  
- le répertoire des rapports : `/var/lib/squidanalyzer/www/`  

---

## 3️⃣ Configuration de SquidAnalyzer

Éditer le fichier de configuration :  
```bash
sudo nano /etc/squidanalyzer/squidanalyzer.conf
```

Paramètres importants :  
```ini
# Fichier de log de Squid
LogFile /var/log/squid/access.log

# Répertoire de sortie des rapports
OutputDir /var/lib/squidanalyzer/www

# Titre du rapport
Title "Rapports SquidAnalyzer"
```

👉 Vérifier que l’utilisateur `squidanalyzer` a les droits de lecture sur `/var/log/squid/access.log` :  
```bash
sudo usermod -aG proxy squidanalyzer
sudo chmod 640 /var/log/squid/access.log
sudo chown proxy:proxy /var/log/squid/access.log
```

---

## 4️⃣ Génération d’un premier rapport

```bash
sudo squidanalyzer
```

Les rapports HTML sont générés dans :  
```
/var/lib/squidanalyzer/www/
```

👉 Ils sont organisés par **année/mois/jour** avec statistiques détaillées.  

---

## 5️⃣ Automatisation avec CRON

Pour générer automatiquement les rapports tous les jours à 23h :  
```bash
sudo crontab -e
```

Ajouter :  
```
0 23 * * * /usr/bin/squidanalyzer > /dev/null 2>&1
```

---

## 6️⃣ Consultation du rapport

Si ton serveur a un serveur web (Apache/Nginx), créer un lien symbolique :  
```bash
sudo ln -s /var/lib/squidanalyzer/www /var/www/html/squidanalyzer
```

Accéder ensuite via un navigateur :  
```
http://<ip-serveur>/squidanalyzer/
```

---

## ✅ Résultats attendus

- **Tableaux détaillés** : top sites, top utilisateurs, temps de réponse  
- **Graphiques dynamiques** : répartition du trafic par heure/jour  
- **Suivi global** : trafic entrant/sortant et utilisation du proxy  

---

## 🔎 Comparaison rapide

| Outil             | Points forts                     | Limites                 |
|-------------------|----------------------------------|-------------------------|
| **SARG**          | Simple, rapide, HTML clair       | Graphiques limités      |
| **Calamaris**     | Très léger, rapide               | Peu visuel              |
| **SquidAnalyzer** | Rapports détaillés, avec graphes | Plus lourd, Perl requis |

👉 Pour un usage moderne et visuel : **SquidAnalyzer est recommandé**.

---

<div align="center">
  <a href="https://github.com/0xCyberLiTech" target="_blank" rel="noopener">
    <img src="https://skillicons.dev/icons?i=linux,debian,bash,docker,nginx,git,vim,python,markdown" alt="Skills" width="440">
  </a>
</div>

<div align="center">
  <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>
</div>

