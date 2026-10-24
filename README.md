# Mode d'emploi – Nœud packet BTSNOD (ON5EE-7)

Guide pour les OM de la section UBA **BTS** : messages APRS « SMS » et packet radio via le nœud **BTSNOD**.

> **Nœud de test** exploité par **ON5EE**, locator **JO20GQ**.
> Il sera ensuite déplacé sur le relais **ON0BTS** sous l'indicatif **ON0BTS-8**. Ce guide sera mis à jour à ce moment-là.

| Service | Indicatif | Alias |
|---|---|---|
| Nœud | ON5EE-7 | BTSNOD |
| BBS | ON5EE-1 | BTSBBS |
| Chat | ON5EE-4 | BTSCHT |

---

## 1. Messages APRS « SMS » (144,800 MHz)

### 1.1 Règle n°1 : un SSID unique par radio
Chaque station sur l'air doit avoir un indicatif + SSID **unique**. Deux appareils avec le même indicatif-SSID s'ignorent mutuellement : les messages ne s'affichent pas.

- `-7` : portatif (attention : **ON5EE-7 est pris par le nœud**)
- `-9` : mobile / voiture
- `-10`, `-5`… : autres usages

Exemple : ON4XYZ-9 dans la voiture, ON4XYZ-7 pour le portatif.

### 1.2 Envoyer un message au nœud
1. Radio sur **144,800 MHz**, APRS activé, votre indicatif-SSID configuré.
2. Menu messages → *Nouveau message* / *Compose*.
3. Destinataire : **ON5EE-7**.
4. Texte : **67 caractères maximum**, **sans accents** (ils s'affichent en « ? »).
5. Envoyer.

Le nœud **acquitte automatiquement** (ACK) : votre radio affiche alors « ACK », « Reçu » ou une coche. Sans ACK, la radio réessaie quelques fois puis abandonne.

### 1.3 Recevoir des messages
Le sysop peut vous envoyer un message direct : il s'affiche sur votre radio si elle porte **exactement** l'indicatif-SSID visé. Votre radio renvoie l'ACK automatiquement.

### 1.4 Lire les bulletins (BLN1…)
Les bulletins sont des messages pour tous, adressés à `BLN1`, `BLN2`… Sur la plupart des radios, ils apparaissent dans la liste des messages ou dans une rubrique *Bulletins*. Vérifiez que la réception des bulletins n'est pas filtrée dans le menu APRS.

### 1.5 Menus types (TH-D75, TH-D74, FTM-400, FTM-500, FT5D…)
Les noms varient, la logique est la même :
- **Kenwood TH-D74/D75** : touche *APRS* / *MSG* → *New* → saisie du destinataire puis du texte → *Send*. La liste des messages montre l'état (ACK).
- **Yaesu FTM / FT5D** : *APRS* → *Message* → *Nouveau* → *Callsign* puis *Text* → *TX*.
- Réglages à vérifier : indicatif + SSID, fréquence 144,800, *beacon* / *TX* autorisé, filtre messages/bulletins.

> Note : un TH-D75 utilisé en mode **KISS** (TNC pour PC) ne fait pas son APRS interne en même temps.

---

## 2. Packet radio : se connecter au nœud

**Fréquence packet : _fréquence à confirmer_** – 1200 bauds AFSK, VHF.

### 2.1 Matériel / logiciel
- **Radio avec TNC KISS intégré** (TH-D72/D74/D75…) en USB/Bluetooth + un logiciel terminal (QtTermTCP, Outpost, PuTTY via KISS, etc.).
- **Direwolf** (TNC logiciel) + interface son (Digirig, SignaLink…) + radio FM. Direwolf ouvre un port KISS (TCP 8001) ou AGW (8000) utilisé par le terminal.
- **TNC matériel** classique en mode terminal.
- Sous Linux : `ax25-tools` (`kissattach`, `axcall`) possible.

Réglages radio : FM, squelch ouvert juste au-dessus du bruit, pas de CTCSS, puissance modérée.

### 2.2 Connexion
Depuis le terminal :
```
C ON5EE-7
```
ou
```
C BTSNOD
```
Le nœud affiche sa bannière et l'invite `BTSNOD:ON5EE-7}`.

### 2.3 Commandes du nœud
| Commande | Rôle |
|---|---|
| `?` | Liste des commandes |
| `NODES` (`N`) | Nœuds connus |
| `MH 3` | Stations entendues récemment sur le port radio |
| `PORTS` | Ports du nœud |
| `INFO` (`I`) | Infos sur le nœud |
| `BBS` | Accès à la BBS |
| `CHAT` | Accès au chat |
| `BYE` (`B`) | Déconnexion |

### 2.4 Chat BTSCHT (ON5EE-4)
Tapez `CHAT` au nœud (ou `C BTSCHT` / `C ON5EE-4` directement).
- Tapez votre texte puis Entrée : il est diffusé à tous les présents.
- `/H` : aide · `/U` : qui est là · `/B` : quitter le chat.

### 2.5 BBS BTSBBS (ON5EE-1)
Tapez `BBS` (ou `C BTSBBS`). Première connexion : la BBS vous demande votre nom et éventuellement votre QTH.
| Commande | Rôle |
|---|---|
| `L` | Lister les nouveaux messages |
| `R n` | Lire le message n |
| `SP INDICATIF` | Envoyer un message personnel |
| `SB ALL` | Envoyer un bulletin |
| `KM` | Effacer ses messages lus |
| `H` | Aide |
| `B` | Quitter |

Pour envoyer : titre, puis texte, terminer par `/EX` sur une ligne seule.

---

## 3. Interface web
L'interface web du nœud (gestion, page SMS APRS) est **réservée au sysop**. Les OM utilisent l'APRS et le packet par radio.

---

## Bonnes pratiques
- Messages courts, pas d'accents, identifiez-vous.
- Pas de répétitions inutiles sur 144,800 (fréquence partagée).
- Problème ou suggestion : contactez **ON5EE** sur l'air ou via la section BTS.

73 – ON5EE, section UBA BTS
