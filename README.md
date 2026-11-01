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
> [!TIP]
> <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-target.svg" width="18" height="18" align="absmiddle" alt="" /> **Guide de Lecture &amp; Progression par Niveau (Cybersecurite)**
> - **Rôle de la brique :** L'ingénierie de **Cybersécurité & Défense en Profondeur (*Defense-in-Depth*)** superpose des barrières de sécurité complémentaires : réduction de la surface d'attaque, durcissement du noyau (`sysctl`), filtrage réseau **Nftables**, détection d'intrusion **Suricata (IDS/IPS)** et remédiation comportementale **CrowdSec / Fail2ban**.
> - **Parcours recommandé :** **Niveau 1 (Fondamentaux &amp; Installation initiale)** pour déployer une base saine &rarr; **Niveau 2 (Configuration &amp; Intégration)** &rarr; **Niveau 3 (Haute Disponibilité, Durcissement &amp; Exploitation)**.

<details>
<summary><img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-puzzle.svg" width="18" height="18" align="absmiddle" alt="" /> <b>Synthèse d'Architecture, Standards Officiels &amp; Diagnostic (Niveau 1 : Fondamentaux · Niveau 2 : Repères · Niveau 3 : Diagnostic)</b></summary>

- **Niveau 1 — Fondamentaux &amp; Principe d'Architecture :** L'ingénierie de **Cybersécurité & Défense en Profondeur (*Defense-in-Depth*)** superpose des barrières de sécurité complémentaires : réduction de la surface d'attaque, durcissement du noyau (`sysctl`), filtrage réseau **Nftables**, détection d'intrusion **Suricata (IDS/IPS)** et remédiation comportementale **CrowdSec / Fail2ban**.
- **Niveau 2 — Repères Officiels (Ports IANA, Fichiers Debian &amp; Commandes de Validation) :** **Commandes de contrôle :** `ss -tulnp` (Audit des sockets en écoute) · `sudo suricata -T -c /etc/suricata/suricata.yaml` (Test syntaxique IDS) · `sudo cscli metrics` (État CrowdSec) · `sudo sysctl --system`.
- **Niveau 3 — Diagnostic d'Incidents &amp; Ingénierie Avancée :** **Diagnostic & Architecture :** Un système **IDS** (*Intrusion Detection System*) analyse le trafic pour lever des alertes qualifiées, tandis qu'un système **IPS** (*Intrusion Prevention System*) ou un bouncer pare-feu intercepte et bloque activement les adresses IP malveillantes au niveau de la couche Netfilter/Nftables.
- **Sources de Vérité Officielles Éditeurs &amp; Standards :** [Guides Officiels ANSSI (Durcissement Linux)](https://cyber.gouv.fr/) &nbsp;·&nbsp; [Documentation Officielle Suricata](https://docs.suricata.io/) &nbsp;·&nbsp; [Documentation Officielle CrowdSec](https://docs.crowdsec.net/)
- **Livres Blancs &amp; 67 Podcasts Audio R&amp;D :** [Portail 0xCyberLiTech](https://0xcyberlitech.com/) &nbsp;·&nbsp; [Livre Blanc SOC Cockpit v5.5](https://0xcyberlitech.com/soc-rd.html) &nbsp;·&nbsp; [Livre Blanc JARVIS Mark-VII](https://0xcyberlitech.com/jarvis-rd.html) &nbsp;·&nbsp; [Blueprint Logiciel &amp; Matériel RTX 5080](https://0xcyberlitech.com/blueprint-jarvis.html)

</details>
<!-- CIEL-PEDAGOGY-END -->


## <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-plan.svg" width="18" height="18" align="absmiddle" alt="" /> Plan d'apprentissage
<img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/glow-section-cyan.svg" width="100%" alt="" />
### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-brain.svg" width="18" height="18" align="absmiddle" alt="" /> I. Fondamentaux de la cybersécurité

- `01` - [Fiche réflexe (synthèse globale)](CYBERSECURITE-01-FICHE-REFLEX.md)
- `02` - [Définition de la cybersécurité](CYBERSECURITE-02-definition.md)
- `03` - [Acronymes clés du domaine](CYBERSECURITE-03-ACRONYMES.md)

---

### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-threat.svg" width="18" height="18" align="absmiddle" alt="" /> II. Menaces : comprendre l’attaque

- `04` - [Kill Chain : les 7 étapes d'une attaque](CYBERSECURITE-04-KILL-CHAIN.md)
- `05` - [Logiciels malveillants : introduction](CYBERSECURITE-05-LOGICIELS-MALVEILLANTS-introduction.md)
- `06` - [Techniques de protection contre les malwares](CYBERSECURITE-06-LOGICIELS-MALVEILLANTS-techniques_de_protection.md)

---

### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-shield.svg" width="18" height="18" align="absmiddle" alt="" /> III. Outils de défense & contrôle
#### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-crypto.svg" width="18" height="18" align="absmiddle" alt="" /> A. Cryptographie

- `07` - [Introduction au chiffrement](CYBERSECURITE-07-CRYPTOGRAPHIE-introduction.md)
- `08` - [Outils de cryptographie (exemples concrets)](CYBERSECURITE-08-CRYPTOGRAPHIE-OUTILS-Mise-en-pratique-avec-des-outils-concrets.md)

#### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-network.svg" width="18" height="18" align="absmiddle" alt="" /> B. Contrôle réseau

- `09` - [Proxy sortant : introduction](CYBERSECURITE-09-PROXY-INTRODUCTION-Le-rôle-du-proxy-sortant.md)
- `10` - [Proxy sortant : installation](CYBERSECURITE-10-PROXY-INSTALLATION-Mise-en-œuvre-pratique.md)
- `11` - [Reverse proxy : introduction](CYBERSECURITE-11-REVERSE-PROXY-INTRODUCTION-Le-rôle-du-proxy-entrant.md)
- `12` - [Reverse proxy : installation](CYBERSECURITE-12-REVERSE-PROXY-INSTALLATION-Mise-en-œuvre-pratique.md)
- `12.1 ` - [Introduction : analyse des logs ](CYBERSECURITE-12-1-PROXY_Suivi_&_Analyse_des_logs_Squid_sous_Debian_12_&_13.md)
- `12.2 ` - [Installation & Utilisation : SquidAnalyzer](CYBERSECURITE-12-2-Installation-&-Utilisation-de-SquidAnalyzer-Debian-12-&-13.md)


#### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-puzzle.svg" width="18" height="18" align="absmiddle" alt="" /> C. Plateformes de sécurité

- `13` - [EPP, EDR, SIEM, SOAR, XDR : comparatif](CYBERSECURITE-13-EPP-EDR-SIEM-SOAR-et-XDR-comprendre-la-différence-entre-ces-acronymes.md)
- `14` - [EDR (Endpoint Detection and Response)](CYBERSECURITE-14-EDR.md)
- `15` - [Installation & Utilisation : Wazuh](CYBERSECURITE-15-TP-install-Wazuh-Debian12-13.md)
- `16` - [Architecture Cyberdéfense Active : IDS/IPS Suricata 7, CrowdSec & Bouncer Nftables sur Debian 12, 13 (Trixie) & 14 (Forky)](CYBERSECURITE-SURICATA-CROWDSEC-NFTABLES-DEBIAN-13-14.md)

---

### <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-crypto.svg" width="18" height="18" align="absmiddle" alt="" /> Sujets abordés

- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> Définitions & concepts fondamentaux
- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> Menaces numériques (kill chain, malwares)
- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> Cryptographie symétrique et asymétrique
- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> Réseau sécurisé (proxies, pare-feux)
- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-ok.svg" width="42" height="16" align="absmiddle" alt="[OK]" /> Plateformes SIEM/EDR/XDR
- <img src="https://raw.githubusercontent.com/0xCyberLiTech/0xcyberlitech/main/assets/icons/wire-rd.svg" width="46" height="16" align="absmiddle" alt="[R&D]" /> À venir : pentest, forensic, logs avancés...

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
