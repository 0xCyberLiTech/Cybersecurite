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

### 👨‍💻 **À propos de moi.**

> Ce dépôt constitue mon laboratoire numérique où je consigne rigoureusement mes apprentissages et expérimentations.
> Passionné par l'écosystème Linux et la cybersécurité, je documente mon parcours et mes projets sur mon GitHub.
> Vous y trouverez des guides pratiques sur la supervision (Zabbix, Nagios), la conteneurisation (Docker) et la sécurisation de serveurs Debian.
> Mon objectif : partager mes connaissances de manière claire et pédagogique.
> N'hésitez pas à y jeter un œil : https://github.com/0xcyberlitech

<p align="center">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=linux,debian,bash,docker,nginx,grafana,prometheus,git,vim" />
  </a>
</p>

---

## 🔧 UFW : Installation & Configuration complète

### 🧭 Sommaire interactif

| 🔢 **Chapitre** | 📝 **Description** | 🚀 **Accès Rapide** |
|----------------|--------------------|---------------------|
| 01. Installation                | Mise en place initiale de UFW.                                        | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](#balise-01) |
| 02. Politiques par défaut      | Définir les règles par défaut (deny, allow).                          | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](#balise-02) |
| 03. Connexions SSH             | Autoriser les connexions SSH entrantes.                               | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](#balise-03) |
| 04. Activation                 | Activer UFW et appliquer les règles.                                  | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](#balise-04) |
| 05. Autres connexions          | Autoriser des services supplémentaires (HTTP, etc.).                  | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](#balise-05) |
| 06. Refus de connexions        | Bloquer certains ports ou services.                                   | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](#balise-06) |
| 07. Suppression de règles      | Supprimer des règles existantes.                                      | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](#balise-07) |
| 08. État & règles d’UFW        | Vérifier l’état du pare-feu et les règles appliquées.                 | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](#balise-08) |
| 09. Zabbix & Grafana           | Supervision : Zabbix (natif), Grafana (conteneur Docker).             | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](#balise-09) |
| 10. Réinitialisation d’UFW     | Réinitialiser ou désactiver UFW (facultatif).                         | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](#balise-10) |

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
