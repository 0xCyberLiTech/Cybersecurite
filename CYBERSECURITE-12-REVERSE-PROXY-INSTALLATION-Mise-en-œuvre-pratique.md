<div align="center">

  <br></br>
  
  <a href="https://github.com/0xCyberLiTech">
  <img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&size=50&duration=6000&pause=1000000000&color=FF0048&center=true&vCenter=true&width=1100&lines=%3ECYBERSECURITE_" alt="Titre dynamique CYBERSECURITE" />
  </a>
  
  <br></br>

  <h2>Laboratoire numérique pour la cybersécurité, Linux & IT.</h2>
  
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

<div align="center">
  
## À propos & Objectifs.

</div>

Ce projet propose des solutions innovantes et accessibles en cybersécurité, avec une approche centrée sur la simplicité d’utilisation et l’efficacité. Il vise à accompagner les utilisateurs dans la protection de leurs données et systèmes, tout en favorisant l’apprentissage et le partage des connaissances.

Le contenu est structuré, accessible et optimisé SEO pour répondre aux besoins de :
- 🎓 Étudiants : approfondir les connaissances
- 👨‍💻 Professionnels IT : outils et pratiques
- 🖥️ Administrateurs système : sécuriser l’infrastructure
- 🛡️ Experts cybersécurité : ressources techniques
- 🚀 Passionnés du numérique : explorer les bonnes pratiques

---

## 🧪 12 - **Mise en place d’un Reverse Proxy avec Apache (Debian 12 & 13) :**

## 🎯 Objectifs pédagogiques
- Comprendre le rôle d’un reverse proxy.  
- Installer et configurer Apache comme reverse proxy.  
- Mettre en place deux applications web internes et les publier via un seul serveur proxy.  
- Sécuriser l’accès avec HTTPS (Let’s Encrypt).  

---

## 📦 Matériel requis
- 1 VM **Debian 12/13** (servira de **reverse proxy**).  
- 2 VM/containers applicatifs internes (exemple : serveurs web simples).  
- Accès Internet et DNS (ou fichier `/etc/hosts` pour simuler les noms).  

---

## 📝 Schéma du scénario

```
          🌍 Client (navigateur)
                    |
           Requête HTTP/HTTPS
                    |
          +-------------------+
          |   Reverse Proxy   |  (192.168.56.100)
          |   Apache Debian   |
          +-------------------+
           /               \
          /                 \
   app1.exemple.com     app2.exemple.com
  (proxy → 8080)        (proxy → 5000)
       |                     |
+---------------+     +---------------+
| Serveur App1  |     | Serveur App2  |
| 192.168.56.10 |     | 192.168.56.20 |
|   Apache 8080 |     |   Flask 5000  |
+---------------+     +---------------+
```

---

## 📝 Scénario concret
- Application 1 (Apache interne) → **192.168.56.10:8080**  
- Application 2 (Python Flask) → **192.168.56.20:5000**  
- Reverse Proxy Debian → **192.168.56.100**  
- Noms de domaine :  
  - `app1.exemple.com` → redirige vers 192.168.56.10:8080  
  - `app2.exemple.com` → redirige vers 192.168.56.20:5000  

---

## 🔹 Étape 1 : Préparation du Reverse Proxy

Mettre à jour le système :

```bash
sudo apt update && sudo apt upgrade -y
```

Installer Apache et modules proxy :

```bash
sudo apt install apache2 -y
sudo a2enmod proxy proxy_http rewrite headers ssl
sudo systemctl restart apache2
```

Vérifier que Apache est actif :

```bash
systemctl status apache2
```

---

## 🔹 Étape 2 : Simuler deux applications internes

### Serveur App1 (port 8080) :

```bash
sudo apt install apache2 -y
sudo sed -i 's/Listen 80/Listen 8080/' /etc/apache2/ports.conf
echo "<h1>Bienvenue sur App1</h1>" | sudo tee /var/www/html/index.html
sudo systemctl restart apache2
```

Test :  
```bash
curl http://192.168.56.10:8080
```

---

### Serveur App2 (port 5000, Flask) :

```bash
sudo apt install python3-flask -y
cat << 'EOF' > app.py
from flask import Flask
app = Flask(__name__)

@app.route('/')
def home():
    return "<h1>Bienvenue sur App2</h1>"

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
EOF

python3 app.py
```

Test :  
```bash
curl http://192.168.56.20:5000
```

---

## 🔹 Étape 3 : Configuration du Reverse Proxy

Créer le fichier de configuration :

```bash
sudo nano /etc/apache2/sites-available/reverseproxy.conf
```

Contenu :

```apache
<VirtualHost *:80>
    ServerName app1.exemple.com

    ProxyPreserveHost On
    ProxyPass / http://192.168.56.10:8080/
    ProxyPassReverse / http://192.168.56.10:8080/
</VirtualHost>

<VirtualHost *:80>
    ServerName app2.exemple.com

    ProxyPreserveHost On
    ProxyPass / http://192.168.56.20:5000/
    ProxyPassReverse / http://192.168.56.20:5000/
</VirtualHost>
```

Activation :

```bash
sudo a2ensite reverseproxy.conf
sudo systemctl reload apache2
```

---

## 🔹 Étape 4 : Tests

Modifier `/etc/hosts` (si pas de DNS) :

```
192.168.56.100 app1.exemple.com
192.168.56.100 app2.exemple.com
```

Vérification :

```bash
curl http://app1.exemple.com
curl http://app2.exemple.com
```

---

## 🔹 Étape 5 : HTTPS avec Let’s Encrypt

Installer Certbot :

```bash
sudo apt install certbot python3-certbot-apache -y
```

Configurer SSL :

```bash
sudo certbot --apache -d app1.exemple.com -d app2.exemple.com
```

---

## 🎓 Questions / Validation
1. Différence entre **proxy sortant** et **reverse proxy** ?  
2. Pourquoi centraliser **SSL/TLS** au niveau du reverse proxy ?  
3. Sous-domaines ou sous-répertoires : quel choix pour ton projet ?  
4. Comment ajouter une **authentification** sur `app2.exemple.com` ?  
5. À quoi sert `ProxyPreserveHost On` ?  

---

<div align="center">
  <a href="https://github.com/0xCyberLiTech" target="_blank" rel="noopener">
    <img src="https://skillicons.dev/icons?i=linux,debian,bash,docker,nginx,git,vim,python,markdown" alt="Skills" width="440">
  </a>
</div>

<div align="center">
  <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>
</div>

