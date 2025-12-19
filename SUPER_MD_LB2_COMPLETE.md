# SUPER-MD: MODUL 117 (LB2) - SYSTEM INFRASTRUCTURE

## 0. QUICK ROUTER & RULES
**ROLE:** You are an Exam Architect. No fluff. No introductions.
**SOURCE:** Use ONLY this document.
**OUTPUT:** Strict exam style. Bullet points. Tables.

| KEYWORD | GOAL | SECTION TO USE |
| :--- | :--- | :--- |
| **"IP" / "Adresskonzept"** | Create IP Table, Subnets, Gateway | [2.0 LOGISCHES NETZ] |
| **"Name" / "DNS"** | Hostname rules, FQDN | [2.2 NAMENSKONZEPT] |
| **"Berechtigung" / "NTFS"** | NTFS vs Share Matrix | [3.0 STORAGE & PERMS] |
| **"Laufwerk" / "Mapping"** | Drive Mapping (S:, P:) | [3.3 MAPPING] |
| **"Diagramm" / "Netzplan"** | Drawing Logic, Labels | [4.0 DIAGRAMS] |
| **"Konzept" / "Vorlage"** | Full Concept Tables | [5.0 TEMPLATES] |

---

## 2.0 LOGISCHES NETZ (IP & DNS)

### 2.1 IP-Adressierung (Regeln)
* **Private Ranges (RFC 1918):**
    * Class A: `10.0.0.0/8`
    * Class B: `172.16.0.0/12`
    * Class C: `192.168.0.0/16` (**Standard für LB2**)
* **Gerätetypen & Adressbereiche:**
    * **Netzwerkkomponenten (Router/Switch):** Immer erste oder letzte IP (`.1` oder `.254`). *Standard Gateway = .1*
    * **Server (Statisch):** Niedriger Bereich (z.B. `.10 - .29`).
    * **Drucker (Statisch):** Mittlerer Bereich (z.B. `.30 - .49`).
    * **Clients (DHCP):** Hoher Bereich (z.B. `.100 - .199`).
    * **Reservations:** DHCP-Reservierung via MAC-Adresse für Geräte, die eine fixe IP brauchen, aber via DHCP verwaltet werden.

### 2.2 Namenskonzept (DNS)
* **Syntax:** Muss logisch und konsistent sein. Formel: `[Ort]-[Typ]-[Nr]` oder `[Abteilung]-[Gerät]-[Nr]`
* **Beispiele:**
    * `SRV-BE-01` (Server, Bern, Nr. 01)
    * `CL-HR-02` (Client, HR, Nr. 02)
    * `PR-Sales-01` (Printer, Sales, Nr. 01)
* **Wichtig:** Keine Namen wie "Müller-PC" (Mitarbeiter wechseln).

### 2.3 Protokolle
* **DHCP (DORA):** Discover, Offer, Request, Acknowledge. Verteilt: IP, Subnetzmaske, Gateway, DNS-Server.
* **DNS:** Namensauflösung (`SRV01` -> `192.168.1.10`).
* **ARP:** Adressauflösung (IP-Adresse -> MAC-Adresse).

---

## 3.0 STORAGE & PERMISSIONS (BERECHTIGUNGEN)

### 3.1 Die "Goldene Regel" (Freigabe vs. NTFS)
* **Freigabeberechtigungen (Share):** Tor zum Haus. **IMMER auf "Jeder" -> "Ändern" (Change) setzen.** Hier wird nicht gefiltert!
* **NTFS-Berechtigungen (Sicherheit):** Zimmerschlüssel. **HIER wird gefiltert.** Gruppen (z.B. `G_HR_RW`) werden hier auf den Ordner berechtigt.
* **Resultat:** Die *restriktivste* Berechtigung gilt (Offene Freigabe + Strenges NTFS = Streng).

### 3.2 Berechtigungsstufen (Windows Terms)
1.  **Vollzugriff (Full Control):** Lesen, Schreiben, Löschen, **Rechte ändern**, Besitz übernehmen. (Nur für Admins).
2.  **Ändern (Modify):** Lesen, Schreiben, Löschen, Ausführen. (Standard für "Schreibrechte").
3.  **Lesen & Ausführen (Read & Execute):** Dateien öffnen, Programme starten. Keine Änderungen. (Standard für "Leserechte").
4.  **Verweigern (Deny):** Überschreibt alles. Nur im Notfall nutzen.

### 3.3 Laufwerksmapping (Drive Mapping)
* **H:** (Home) -> `\\Server\Home\%Username%` (Privat)
* **P:** (Public/Austausch) -> `\\Server\Public` (Alle Lesen/Schreiben)
* **S:** (Share/Abteilung) -> `\\Server\Data` (Abteilungsordner sichtbar via ABE - Access Based Enumeration).
* **Umsetzung:** Via GPO (Group Policy) oder Login Script (`net use S: \\Server\Data`).

---

## 4.0 DIAGRAMME & HARDWARE

### 4.1 Topologie (Physisch & Logisch)
* **Ablauf:** Internet -> Modem/Router -> Firewall -> Switch -> Patchfeld -> Dose -> Client.
* **Verkabelung:**
    * Horizontale Verkabelung (Etagenverteiler zu Dose): Twisted Pair (Kupfer).
    * Vertikale Verkabelung (Gebäude zu Gebäude): Glasfaser (LWL).

### 4.2 Beschriftung im Netzplan (Pflicht)
Im Diagramm MÜSSEN stehen:
1.  **Hostname** (`SRV-01`)
2.  **IP-Adresse** (`192.168.1.10`)
3.  **Schnittstelle** (bei Router: `eth0` / `LAN1`)
4.  **Netzadresse** (z.B. `192.168.1.0/24`)

---

## 5.0 TEMPLATES (EXACT EXAM HEADERS)

### TEMPLATE A: IP-ADRESSKONZEPT (Tabelle)
*Benutze exakt diese Spaltenüberschriften.*

| Gerätetyp | Hostname | Schnittstelle | IP-Adresse | Subnetzmaske | Gateway | DNS | Bemerkung |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Router | R-01 | LAN | 192.168.1.1 | 255.255.255.0 | - | - | GW für LAN |
| Server | S-DC-01 | NIC1 | 192.168.1.10 | 255.255.255.0 | 192.168.1.1 | 127.0.0.1 | DC/DNS |
| Client | C-HR-01 | ETH | DHCP | DHCP | DHCP | DHCP | Range .100+ |

### TEMPLATE B: BERECHTIGUNGSMATRIX (Grid)
*X = Zugriff erlaubt. Level in Legende definieren.*

| Ressource (Ordner) | Freigabename | User/Gruppe: **Admins** | User/Gruppe: **HR** | User/Gruppe: **Sales** | NTFS Level (HR) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| D:\Data\Public | Public$ | Vollzugriff | Ändern | Ändern | Ändern |
| D:\Data\HR | HR$ | Vollzugriff | Ändern | - | Ändern |
| D:\Data\Sales | Sales$ | Vollzugriff | - | Ändern | - |

*Wichtig: Freigabeberechtigung ist immer "Jeder: Ändern". Die Spalte "NTFS Level" definiert den echten Schutz.*

### TEMPLATE C: REALISIERUNG CHECKLIST (Praxis Part)
1.  **Verkabelung:** PC mit Switch/Dose verbinden. Link-LED prüfen.
2.  **IP-Konfig:** Statische IP setzen (Adapteroptionen) oder `ipconfig /all` prüfen bei DHCP.
3.  **Ping-Test:** `ping [Gateway]` -> `ping [Server IP]` -> `ping google.ch`.
4.  **Freigaben:**
    * Server: Ordner erstellen -> Eigenschaften -> Freigabe -> Erweiterte Freigabe -> Berechtigungen -> Jeder: Ändern.
    * Server: Reiter "Sicherheit" -> Bearbeiten -> Gruppe hinzufügen -> "Ändern" oder "Lesen" wählen.
5.  **Mapping:** Explorer -> Netzlaufwerk verbinden -> `S:` -> `\\Server\Freigabe`.
