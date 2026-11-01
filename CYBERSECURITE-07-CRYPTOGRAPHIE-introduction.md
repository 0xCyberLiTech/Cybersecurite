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
- **Livres Blancs &amp; 67 Podcasts Audio R&amp;D :** [Portail 0xCyberLiTech](https://0xcyberlitech.com/) &nbsp;·&nbsp; [Livre Blanc SOC Cockpit v5.5](https://0xcyberlitech.com/soc-rd.html) &nbsp;·&nbsp; [Livre Blanc JARVIS Mark-VII](https://0xcyberlitech.com/jarvis-rd.html) &nbsp;·&nbsp; [Blueprint Logiciel &amp; Matériel RTX 5080](https://0xcyberlitech.com/blueprint-jarvis.html)

</details>
<!-- CIEL-PEDAGOGY-END -->


# <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-crypto.svg" width="18" height="18" align="absmiddle" alt="" /> Introduction à la Cryptographie

La **cryptographie** est la science qui permet de **protéger les informations** en les rendant illisibles pour toute personne non autorisée. Elle est au cœur de la cybersécurité moderne, utilisée dans des domaines variés comme les communications, les transactions bancaires, ou encore les systèmes de messagerie.

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-brain.svg" width="18" height="18" align="absmiddle" alt="" /> Pourquoi la cryptographie est-elle importante ?
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

Imagine que vous envoyez une lettre secrète à un ami. Si quelqu’un l’intercepte, il peut lire son contenu. La cryptographie agit comme une **enveloppe blindée** : elle rend le message incompréhensible sans une **clé secrète**.

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-crypto.svg" width="18" height="18" align="absmiddle" alt="" /> Concepts clés
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

- **Chiffrement** : Transformer un message clair (texte lisible) en un message codé (texte chiffré).
- **Déchiffrement** : Revenir du message codé au message original à l’aide d’une clé.
- **Clé** : Élément secret ou public permettant le chiffrement et/ou le déchiffrement.
- **Algorithme cryptographique** : Méthode utilisée pour chiffrer/déchiffrer les données (ex : AES, RSA).
- **Hachage** : Créer une empreinte unique d’un fichier ou message. Très utile pour vérifier l’intégrité.

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-puzzle.svg" width="18" height="18" align="absmiddle" alt="" /> Deux grandes familles de cryptographie
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-target.svg" width="18" height="18" align="absmiddle" alt="" /> 1. Cryptographie symétrique

<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-crypto.svg" width="18" height="18" align="absmiddle" alt="" /> Une seule clé est utilisée pour chiffrer et déchiffrer. 
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> Rapide, mais nécessite un échange sécurisé de la clé.

### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-target.svg" width="18" height="18" align="absmiddle" alt="" /> 2. Cryptographie asymétrique

<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-crypto.svg" width="18" height="18" align="absmiddle" alt="" /> Utilise une paire de clés : une **publique** (partagée) et une **privée** (secrète). 
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> Plus sécurisée pour les échanges à distance (ex : RSA).

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-shield.svg" width="18" height="18" align="absmiddle" alt="" /> Utilisations courantes
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

- **Connexion HTTPS** sur les sites web
- **Messageries sécurisées** (Signal, WhatsApp)
- **Signatures numériques** pour valider l’authenticité d’un document
- **Stockage chiffré** sur vos appareils

---

## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-doc.svg" width="18" height="18" align="absmiddle" alt="" /> Conclusion
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />

La cryptographie est essentielle pour garantir la **confidentialité**, **l'intégrité**, et **l'authenticité** des données. Bien qu’elle repose sur des mathématiques complexes, ses applications sont partout dans notre vie numérique.

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
