<div align="center">

<a href="https://github.com/0xCyberLiTech">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&size=32&pause=1000&color=33FF33&center=true&vCenter=true&width=1050&lines=Cybersécurité+et+Pare-feu+UFW;Installation+et+Configuration+pas+à+pas;Filtrage+des+ports+et+sécurisation+des+connexions" alt="Titre dynamique UFW" />
</a>

<p>
  <em style="color:#888">Un dépôt <strong>pédagogique</strong> sur les firewalls Linux.</em><br>
  <strong>📘 Apprentissage – 🔐 Sécurité – 🧠 Compréhension</strong>
</p>

</div>

---


<div align="center">

<a href="https://github.com/0xCyberLiTech">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&size=32&pause=1000&color=33FF33&center=true&vCenter=true&width=1050&lines=Cybersécurité+et+Pare-feu+UFW;Installation+et+Configuration+pas+à+pas;Filtrage+des+ports+et+sécurisation+des+connexions" alt="Titre dynamique UFW" />
</a>

<p>
  <em style="color:#888">Un dépôt <strong>pédagogique</strong> sur les firewalls Linux.</em><br>
  <strong>📘 Apprentissage – 🔐 Sécurité – 🧠 Compréhension</strong>
</p>

</div>

---

## 👨‍💻 À propos de moi

> 🎓 Ce dépôt constitue mon **laboratoire numérique** où je consigne rigoureusement mes apprentissages et expérimentations.  
> Passionné par **l’écosystème Linux** et la **cybersécurité**, je documente ici mon parcours technique.  
> Vous y trouverez des **guides pratiques** sur la supervision (Zabbix, Nagios), la conteneurisation (Docker), et la sécurisation de serveurs Debian.  
> 📌 **Objectif :** partager des connaissances **claires, accessibles et reproductibles**.

🔗 [Profil GitHub 0xCyberLiTech](https://github.com/0xCyberLiTech)

<p align="center">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=linux,debian,bash,docker,nginx,grafana,prometheus,git,vim" />
  </a>
</p>

---

## 🔧 UFW : Installation & Configuration complète

### 🧭 Sommaire interactif

| 🧩 Chapitre | 📝 Description | 🔗 Accès |
|:--:|:--|:--:|
| 01 | Installation de UFW | [Explorer 🔗](#balise-01) |
| 02 | Politiques par défaut | [Explorer 🔗](#balise-02) |
| 03 | Autoriser les connexions SSH | [Explorer 🔗](#balise-03) |
| 04 | Activation d’UFW | [Explorer 🔗](#balise-04) |
| 05 | Autoriser d’autres connexions | [Explorer 🔗](#balise-05) |
| 06 | Refuser des connexions | [Explorer 🔗](#balise-06) |
| 07 | Suppression de règles | [Explorer 🔗](#balise-07) |
| 08 | Vérification de l’état/règles | [Explorer 🔗](#balise-08) |
| 09 | UFW + Zabbix & Grafana | [Explorer 🔗](#balise-09) |
| 10 | Réinitialisation ou désactivation | [Explorer 🔗](#balise-10) |

---

## 🎯 Introduction à UFW (Uncomplicated Firewall)

**UFW** signifie _"Uncomplicated Firewall"_, un outil de configuration simplifiée de pare-feu pour Linux. Il agit comme une interface conviviale au système complexe `iptables`, permettant aux utilisateurs — même débutants — de gérer efficacement leur sécurité réseau.

### 🧠 Concepts Clés :

- **Politique par défaut :**
  - Ex. : refuser toutes les connexions entrantes, autoriser les sortantes.
- **Exceptions :**
  - Autoriser uniquement les ports ou services nécessaires (SSH, HTTP...).

💡 *UFW est particulièrement utile pour sécuriser rapidement un serveur tout en gardant une vue claire sur les règles actives.*

---

## 📘 Extrait du Guide — Commandes essentielles

### 🔹 01 — Installation de UFW <a name="balise-01"></a>
```bash
sudo apt install ufw
```

### 🔹 02 — Politiques par défaut <a name="balise-02"></a>
```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

### 🔹 03 — Autoriser SSH <a name="balise-03"></a>
```bash
sudo ufw allow ssh
# ou
sudo ufw allow 22
```

### 🔹 04 — Activer UFW <a name="balise-04"></a>
```bash
sudo ufw enable
```

### 🔹 05 — Autoriser des ports précis <a name="balise-05"></a>
```bash
sudo ufw allow http
sudo ufw allow 443
sudo ufw allow 6000:6007/tcp
```

### 🔹 06 — Refuser une IP <a name="balise-06"></a>
```bash
sudo ufw deny from 203.0.113.4
```

### 🔹 07 — Supprimer une règle <a name="balise-07"></a>
```bash
sudo ufw delete 2
# ou
sudo ufw delete allow http
```

### 🔹 08 — Vérifier les règles <a name="balise-08"></a>
```bash
sudo ufw status verbose
```

### 🔹 09 — Exemple avec Zabbix + Docker <a name="balise-09"></a>
```bash
ufw limit in on enp86s0 from 192.168.50.118 to 192.168.50.250 port 2277 proto tcp comment 'SSH sécurisé'
ufw allow in on enp86s0 from 192.168.50.118 to 192.168.50.250 port 80 proto tcp comment 'HTTP'
```

### 🔹 10 — Réinitialisation d’UFW <a name="balise-10"></a>
```bash
sudo ufw disable
sudo ufw reset
```

---

<div align="center">
  <strong>🔒 Un guide par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour une cybersécurité accessible à tous.</strong>
</div>

-
