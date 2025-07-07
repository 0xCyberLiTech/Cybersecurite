<div align="center">

<a href="https://github.com/0xCyberLiTech">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&size=32&pause=1000&color=33FF33&center=true&vCenter=true&width=1000&lines=CRYPTOGRAPHIE+%26+CYBERSÉCURITÉ;Chiffrement+•+Hachage+•+Authentification;Comprendre+les+bases+pour+mieux+protéger" alt="Typing SVG" />
</a>

<p align="center">
  <em>Un dépôt pédagogique autour des fondamentaux de la cybersécurité.</em><br>
  <b>📘 Apprentissage – 🔐 Sécurité – 🧠 Compréhension</b>
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

### 🎯 **Objectif de ce dépôt.**

> Ce dépôt a pour vocation de centraliser un ensemble de notions clés en cybersécurité. Il s’adresse aux passionnés, étudiants, et professionnels souhaitant mieux comprendre les menaces informatiques, apprendre  > à sécuriser leurs environnements et se familiariser avec les concepts et outils de défense.

---

# 🔐 Cours de Cryptographie sous Debian 12

# Cours de Cryptographie sous Debian 12

## 1. 🔐 Introduction à la Cryptographie

La cryptographie permet de **protéger la confidentialité, l'intégrité et l’authenticité** des données :

- **Confidentialité** : seules les personnes autorisées peuvent lire les données.
- **Intégrité** : les données ne sont pas modifiées.
- **Authenticité** : on peut vérifier l’identité de l’émetteur.

### Types de cryptographie

| Type        | Exemples d’outils      | Usage                           |
| ----------- | ---------------------- | ------------------------------- |
| Symétrique  | `openssl`, `gpg` (AES) | Chiffrer rapidement un fichier  |
| Asymétrique | `gpg`, `ssh-keygen`    | Signature, chiffrement de mails |
| Hachage     | `sha256sum`, `md5sum`  | Vérifier l’intégrité            |

---

## 2. ⚙️ Installer les outils nécessaires

```bash
sudo apt update
sudo apt install -y gnupg openssl gpg ssh
```

---

## 3. 🔐 Cryptographie symétrique avec `openssl`

### Exemple : Chiffrer un fichier avec AES-256

```bash
openssl enc -aes-256-cbc -salt -in secret.txt -out secret.txt.enc
```

**Explication :**

- `-aes-256-cbc` : algorithme symétrique fort
- `-salt` : ajoute du sel pour renforcer le chiffrement
- `-in` / `-out` : fichier source et résultat

### Déchiffrer :

```bash
openssl enc -aes-256-cbc -d -in secret.txt.enc -out secret.txt
```

---

## 4. 🛡️ Hachage d’un fichier

### Créer un hash SHA256

```bash
sha256sum fichier.txt > hash.txt
```

**Explication :** Cette commande génère un fichier `hash.txt` contenant le hachage SHA256 du fichier, suivi de son nom.

### Vérifier l’intégrité

```bash
sha256sum -c hash.txt
```

> `hash.txt` doit contenir une ligne comme :
> `abc123...  fichier.txt`

### Alternatives : SHA1 et SHA512

```bash
sha1sum fichier.txt
sha512sum fichier.txt
```

---

## 5. 🔐 GPG (GNU Privacy Guard)

### Générer une paire de clés

```bash
gpg --full-generate-key
```

**Explication :** Cette commande vous guide pour créer une clé (type, taille, nom, expiration, mot de passe).

### Lister les clés disponibles

```bash
gpg --list-keys
```

### Exporter sa clé publique

```bash
gpg --armor --export votreadresse@email.com > ma_cle.pub
```

### Importer une clé publique

```bash
gpg --import cle_contact.pub
```

### Chiffrer un fichier pour un contact

```bash
gpg -e -r contact@email.com fichier.txt
```

**Explication :** Crée `fichier.txt.gpg`, lisible uniquement par le détenteur de la clé privée associée.

### Déchiffrer un fichier

```bash
gpg -d fichier.txt.gpg
```

**Remarque :** Nécessite votre clé privée et mot de passe.

---

## 6. ✍️ Signatures numériques avec GPG

### Signer un fichier (mode texte clair)

```bash
gpg --clearsign mon_fichier.txt
```

**Résultat :** un fichier signé nommé `mon_fichier.txt.asc`

### Vérifier une signature

```bash
gpg --verify mon_fichier.txt.asc
```

**But :** S'assurer que le fichier est authentique et non modifié.

---

## 7. 🔐 Génération de clés SSH

### Créer une paire de clés

```bash
ssh-keygen -t ed25519 -C "monemail@domaine.com"
```

**Explication :**
- `ed25519` est un algorithme moderne, plus rapide que RSA
- Le fichier est enregistré dans `~/.ssh/id_ed25519`

### Copier la clé publique sur un serveur

```bash
ssh-copy-id utilisateur@ip_du_serveur
```

**Effet :** Permet de se connecter sans mot de passe via SSH.

---

## 8. 🧪 Exemples avancés

### Chiffrer un dossier avec tar + openssl

```bash
tar czf - mon_dossier | openssl enc -aes-256-cbc -salt -out mon_dossier.tar.gz.enc
```

**Explication :** Le dossier est compressé et chiffré en une seule ligne.

### Déchiffrer

```bash
openssl enc -d -aes-256-cbc -in mon_dossier.tar.gz.enc | tar xz
```

**Résultat :** Le dossier est restauré après déchiffrement et extraction.

---

## 9. 📚 Bonnes pratiques

- Ne partagez jamais vos clés privées !
- Protégez vos clés avec un mot de passe fort.
- Utilisez des algorithmes modernes (RSA ≥ 4096, Ed25519).
- Faites des sauvegardes de vos clés dans des emplacements sécurisés.
- Révoquez rapidement les clés compromises.

---

## 10. 📌 Résumé visuel

| Action                | Commande principale              |
| --------------------- | -------------------------------- |
| Chiffrer (symétrique) | `openssl enc -aes-256-cbc`       |
| Hachage               | `sha256sum`                      |
| Clés GPG              | `gpg --full-generate-key`        |
| Chiffrer avec GPG     | `gpg -e -r destinataire fichier` |
| Signer avec GPG       | `gpg --clearsign fichier`        |
| Générer une clé SSH   | `ssh-keygen -t ed25519`          |
| Installer les outils  | `apt install gnupg openssl gpg`  |

---

<p align="center">
  🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessible à tous.
</p>
