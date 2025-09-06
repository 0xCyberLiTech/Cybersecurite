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

## 🧭 09 - **Proxy introduction, le rôle du proxy sortant :**.

Un **proxy** est comme un **intermédiaire** entre ton ordinateur et Internet.  
Imagine : au lieu de parler directement à un site web, ton ordinateur **parle d’abord au proxy**, qui se charge ensuite de transmettre le message au site.  
Le site, lui, ne voit que le proxy — pas ton ordinateur.  

---

# 🛡️ Le Proxy Sortant (Forward Proxy)

👉 Un **proxy sortant** est utilisé par les **clients internes** (ordinateurs, navigateurs, applis) qui veulent accéder à Internet.  
C’est le plus courant en entreprise ou dans un réseau scolaire.

### Ses rôles principaux :

1. **Contrôle d’accès**  
   - Le proxy décide qui peut aller où.  
   - Exemple : dans une école, il peut bloquer l’accès à *YouTube* ou aux sites de jeux.  

2. **Sécurité et anonymat**  
   - Les ordinateurs internes utilisent **l’adresse IP du proxy** pour sortir sur Internet.  
   - Résultat : les sites web ne voient que l’IP du proxy, pas celles des utilisateurs.  

3. **Cache (accélération)**  
   - Si plusieurs personnes consultent la même page, le proxy garde une **copie en mémoire**.  
   - Ainsi, la deuxième personne qui visite la page la reçoit **plus vite**, sans consommer de bande passante supplémentaire.  

4. **Journalisation (logs)**  
   - Le proxy enregistre toutes les connexions.  
   - Utile pour :  
     - vérifier l’utilisation d’Internet au travail,  
     - retrouver la cause d’un incident de sécurité,  
     - répondre à des obligations légales.  

---

# 📖 Exemple concret (entreprise)

Imaginons une entreprise avec 50 employés.  

**Sans proxy :**  
- Chacun de leurs ordinateurs sort directement sur Internet.  
- Difficile de contrôler qui va sur quel site, et impossible de centraliser les logs.  

**Avec un proxy sortant :**  
- Tous les ordinateurs passent par le proxy avant d’accéder au Web.  
- L’entreprise peut définir des règles :  
  - 🔒 Bloquer les réseaux sociaux de 9h à 18h.  
  - 🌍 Autoriser uniquement les sites liés au travail.  
  - ⚡ Mettre en cache les mises à jour Windows pour éviter de les télécharger 50 fois.  
- Les serveurs externes (Google, Amazon, etc.) voient uniquement **l’IP du proxy**, pas celles des 50 employés.  

---

# 🖼️ Petit schéma simplifié (ASCII)

```
[Ordinateur 1]   [Ordinateur 2]   [Ordinateur 3]
       |               |                |
       +---------------+----------------+
                       |
                 [ PROXY SORTANT ]
                       |
                 ===== Internet =====
                       |
                  [ Serveur Web ]
```

➡ Tous les ordinateurs **passent d’abord par le proxy** avant d’aller sur Internet.  

---

<div align="center">
  <a href="https://github.com/0xCyberLiTech" target="_blank" rel="noopener">
    <img src="https://skillicons.dev/icons?i=linux,debian,bash,docker,nginx,git,vim,python,markdown" alt="Skills" width="440">
  </a>
</div>

<div align="center">
  <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>
</div>

