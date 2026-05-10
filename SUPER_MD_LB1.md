# SUPER-MD — MODUL 231 LB1 (Datenschutz & Datensicherheit)

---

## QR — QUICK ROUTER

Lies die Aufgabe → erkenne den Typ → springe zum Block:

| Schlüsselwörter | Typ | Block |
|---|---|---|
| CIA, Vertraulichkeit, Integrität, Verfügbarkeit, Schutzziel | CIA-Zuordnung | T-CIA |
| Enterprise Architecture, Ebene, Geschäftsprozess, Daten, Applikation, Infrastruktur | EA-Einordnung | T-EA |
| Datenschutz, Datensicherheit, IT-Sicherheit, Informationssicherheit, Begriff, Definition | Begriffe | T-BEGRIFFE |
| DSG, DSGVO, zulässig, Personendaten, Einwilligung, besonders schützenswert | Datenschutzgesetz | T-DSG |
| Massnahme, technisch, rechtlich, organisatorisch, administrativ | Massnahmen-Kategorisierung | T-MASS |
| Backup, Firewall, WLAN, Passwort, Authentisierung, RAID | Technische Massnahmen | T-TECH |
| Impressum, Datenschutzerklärung, Cookie, AGB, Webseite | Webseiten-Recht | T-WEB |
| Copyright, Creative Commons, Public Domain, Fair Use, Lizenz | Lizenzmodelle | T-LIZENZ |
| Bedrohung, Risiko, höhere Gewalt, Angriff, Social Engineering | Bedrohungen | T-BEDRO |
| ISMS, ISO 27001, BSI, Grundschutz | ISMS/Standards | T-ISMS |

---

## MI — MICRO INDEX

- QR: Quick Router
- AR: Answer Rules
- T-CIA: Schutzziele CIA
- T-EA: Enterprise Architecture
- T-BEGRIFFE: Definitionen
- T-DSG: Datenschutzgesetz (CH + EU)
- T-MASS: Massnahmen-Kategorisierung
- T-TECH: Technische Massnahmen
- T-WEB: Webseiten-Rechtliches
- T-LIZENZ: Lizenzierungsmodelle
- T-BEDRO: Bedrohungen
- T-ISMS: Management-Systeme
- X-TRAP: Fallen & häufige Fehler
- X-GLOSS: Glossar

---

## AR — ANSWER RULES

### Formatregeln (STRIKT)
- Kurz & präzis, keine Floskeln
- Stichwörter wo möglich, kurze Sätze
- Keine Einleitungen ("Hier ist...", "Die Antwort lautet...")
- Bei Zuordnung: nur Buchstabe/Kürzel + kurze Begründung (1 Satz max)
- Bei Ja/Nein: Entscheidung + Grund (1-2 Sätze)
- Bei Tabellen: nur die geforderten Felder ausfüllen

### Output-Muster
- Zuordnung: `C` oder `I` oder `A` — [Grund in 3-5 Wörtern]
- Zulässig/Nicht: `Zulässig` oder `Nicht zulässig` — [Kurzbegründung]
- Massnahme: `T` / `R` / `O` — [falls Begründung gefragt: 1 Satz]
- Definition: Begriff = [Definition in 1-2 Sätzen]

---

## T-CIA — SCHUTZZIELE CIA ⭐ PRIORITÄT 1

### Die drei Schutzziele

| Kürzel | Deutsch | Bedeutung | Fragestellung |
|---|---|---|---|
| **C** | Vertraulichkeit (Confidentiality) | Nur Berechtigte haben Zugriff | Wer darf die Daten sehen? |
| **I** | Integrität (Integrity) | Daten sind korrekt & unverändert | Sind die Daten manipulationssicher? |
| **A** | Verfügbarkeit (Availability) | Daten sind zugänglich wenn nötig | Kann ich zugreifen wenn ich muss? |

### Zuordnungs-Pattern

**Wann C (Vertraulichkeit)?**
- Unbefugter liest/sieht Daten
- Daten werden abgefangen
- Zugriffsrechte fehlen
- Passwort-Probleme (Zugang)
- Verschlüsselung fehlt

**Wann I (Integrität)?**
- Daten wurden verändert/manipuliert
- Falsche Daten gespeichert
- Übertragungsfehler
- Hashwerte stimmen nicht
- Daten sind korrupt

**Wann A (Verfügbarkeit)?**
- System nicht erreichbar
- Server down
- Daten gelöscht (nicht mehr da)
- DoS-Angriff
- Backup fehlt / Restore nicht möglich

### Beispiele aus Musterlösungen

| Szenario | Antwort |
|---|---|
| Unbefugte erhalten Zugang zu Server | C |
| Unbefugte kopieren Dateien | C |
| Falsche Preise in Datenbank | I |
| Bestellung wurde verfälscht | I |
| Mitarbeiter kann Webseite nicht aufrufen | A |
| Rechnung muss sofort erstellt werden | A |
| Umsatzreport zeigt falsche Zahlen | I |

### Verfügbarkeits-Einstufung (normal vs. hoch)

| Einstufung | Kriterien |
|---|---|
| **Normal** | Ausfall 1-2 Tage verkraftbar, kein grosser finanzieller Schaden |
| **Hoch** | Sofortiger Zugriff nötig, Geschäft steht still, Kundenbeziehung gefährdet |

---

## T-EA — ENTERPRISE ARCHITECTURE

### Die 4 Ebenen (von oben nach unten)

| Ebene | Beschreibung | Beispiele |
|---|---|---|
| **Geschäftsprozesse** | Abläufe im Unternehmen | Bestellung, Reklamation, Lohnzahlung |
| **Daten/Informationen** | Gespeicherte Daten | Kundendatenbank, Produktkatalog |
| **Applikationen** | Software/Anwendungen | ERP, CRM, Webshop |
| **IT-Infrastruktur** | Hardware & Netzwerk | Server, Firewall, Router, Clients |

### Begriffe-Einordnung

| Begriff | Ebene(n) |
|---|---|
| Datenschutz | Daten (Personendaten in Datensammlungen) |
| Datensicherheit | Daten + Infrastruktur |
| IT-Sicherheit | Infrastruktur (technisch) |
| Informationssicherheit | ALLE Ebenen (ganze Landkarte) |

### Personen/Stellen → Ebene zuordnen

| Rolle | Ebene | Begründung |
|---|---|---|
| Geschäftsleitung | Geschäftsprozesse | Verantwortlich für Abläufe |
| Buchhalter | Daten/Applikationen | Arbeitet mit Finanzdaten |
| Systemadministrator | Infrastruktur | Verwaltet Server/Netzwerk |
| Datenbankadmin | Daten | Verwaltet Datenbanken |
| Softwareentwickler | Applikationen | Entwickelt Anwendungen |

---

## T-BEGRIFFE — DEFINITIONEN

### Kernbegriffe (auswendig!)

| Begriff | Definition |
|---|---|
| **Datenschutz** | Schutz von Personendaten vor Missbrauch. Recht auf informationelle Selbstbestimmung. |
| **Datensicherheit** | Technischer Schutz von Datensammlungen und deren Infrastruktur. |
| **IT-Sicherheit** | Schutz der technischen IT-Infrastruktur (Hardware, Netzwerk). |
| **Informationssicherheit** | Schutz ALLER Informationen (digital + analog) im Unternehmen. Umfasst alles. |

### Unterschiede (Prüfungsklassiker!)

**Datensicherheit vs. IT-Sicherheit:**
- Datensicherheit = fokussiert auf DATEN
- IT-Sicherheit = fokussiert auf TECHNIK/INFRASTRUKTUR

**Datenschutz vs. Datensicherheit:**
- Datenschutz = RECHTLICH, Personendaten, Gesetze
- Datensicherheit = TECHNISCH, alle Daten, Massnahmen

**Informationssicherheit vs. IT-Sicherheit:**
- Informationssicherheit = ALLES (auch Papierakten!)
- IT-Sicherheit = nur digitale/technische Komponenten

---

## T-DSG — DATENSCHUTZGESETZ ⭐ PRIORITÄT 1

### Personendaten-Kategorien

| Kategorie | Beispiele |
|---|---|
| **Normale Personendaten** | Name, Adresse, E-Mail, Telefon, Geburtsdatum |
| **Besonders schützenswerte** | Gesundheit, Religion, politische Meinung, Ethnie, Genetik, Biometrie, Strafregister, Sozialhilfe |

### Grundsätze DSG (neu ab 2023)

1. **Rechtmässigkeit** — Legale Grundlage nötig
2. **Treu und Glauben** — Transparent, nicht heimlich
3. **Verhältnismässigkeit** — Nur nötige Daten sammeln
4. **Zweckbindung** — Nur für angegebenen Zweck nutzen
5. **Richtigkeit** — Daten aktuell halten
6. **Speicherbegrenzung** — Löschen wenn nicht mehr nötig
7. **Sicherheit** — Angemessener Schutz

### Zulässig / Nicht zulässig — Muster

| Szenario | Antwort | Grund |
|---|---|---|
| Mitarbeiter-Adressen für Newsletter ohne Einwilligung | Nicht zulässig | Keine Einwilligung, anderer Zweck |
| Kundendaten für Bestellabwicklung nutzen | Zulässig | Vertragszweck |
| Gesundheitsdaten ohne explizite Einwilligung | Nicht zulässig | Besonders schützenswert |
| Daten an Dritte ohne Wissen des Betroffenen | Nicht zulässig | Keine Transparenz |
| Daten löschen nach Ablauf Aufbewahrungsfrist | Zulässig | Speicherbegrenzung |

### DSG Schweiz vs. DSGVO (EU)

| Aspekt | DSG (CH) | DSGVO (EU) |
|---|---|---|
| Gilt für | CH-Unternehmen | EU + wer EU-Bürger-Daten verarbeitet |
| Bussen | Bis CHF 250'000 (Person) | Bis 4% Jahresumsatz / 20 Mio € |
| DPO Pflicht | Nein (empfohlen) | Ja (in vielen Fällen) |
| Einwilligung | Opt-out möglich | Opt-in erforderlich |

### Wann gilt DSGVO für CH-Unternehmen?

- Waren/Dienstleistungen an EU-Bürger anbieten
- Verhalten von EU-Bürgern beobachten (Tracking)
- Niederlassung in EU haben

---

## T-MASS — MASSNAHMEN-KATEGORISIERUNG ⭐ PRIORITÄT 1

### Die 3 Kategorien

| Kürzel | Kategorie | Beschreibung |
|---|---|---|
| **T** | Technisch | Hardware, Software, IT-Systeme |
| **R** | Rechtlich | Verträge, Gesetze, Vereinbarungen |
| **O** | Organisatorisch | Prozesse, Richtlinien, Schulungen |

### Zuordnungs-Beispiele (aus Musterlösungen)

| Massnahme | Kategorie |
|---|---|
| Firewall installieren | T |
| Backup durchführen | T |
| Verschlüsselung aktivieren | T |
| Virenschutz | T |
| Passwort-Policy | O |
| Nutzungsreglement | O (R wenn rechtlich bindend) |
| Mitarbeiterschulung | O |
| Clear-Desk Policy | O |
| Geheimhaltungsvereinbarung (NDA) | R |
| Datenschutzerklärung | R |
| AGB | R |
| Arbeitsvertrag mit IT-Klauseln | R |
| Auftragsbearbeitungsvertrag | R |
| Archivierungspflicht einhalten | R |

### Grenzfälle

- **Zutrittskontrolle (Badge):** T (wenn technisch) oder O (wenn Prozess)
- **Passwort-Richtlinie:** O (die Richtlinie) + T (die Umsetzung im System)
- **Nutzungsreglement:** O (intern) oder R (wenn rechtlich bindend)

---

## T-TECH — TECHNISCHE MASSNAHMEN

### Backup

| Typ | Beschreibung |
|---|---|
| **Vollbackup** | Alles sichern |
| **Inkrementell** | Nur Änderungen seit letztem Backup |
| **Differentiell** | Änderungen seit letztem Vollbackup |

**Generationenprinzip (Grossvater-Vater-Sohn):**
- Täglich (Sohn), Wöchentlich (Vater), Monatlich (Grossvater)

**3-2-1 Regel:**
- 3 Kopien, 2 verschiedene Medien, 1 Offsite

### Firewall-Typen

| Typ | Funktion |
|---|---|
| Paketfilter | Prüft IP/Port |
| Stateful | + Verbindungsstatus |
| Application Layer | + Inhalt prüfen |
| Next-Gen (NGFW) | + IDS/IPS, Deep Inspection |

### WLAN-Sicherheit

**Unsicher:**
- WEP (veraltet, knackbar)
- Offenes WLAN
- Standard-Passwörter

**Sicher:**
- WPA2/WPA3
- Starkes Passwort
- SSID nicht verstecken (kein echter Schutz)
- MAC-Filter (schwacher Zusatzschutz)

### Authentisierung

| Faktor | Beispiel |
|---|---|
| Wissen | Passwort, PIN |
| Besitz | Token, Smartphone, Badge |
| Sein (Biometrie) | Fingerabdruck, Gesicht |

**MFA = 2+ Faktoren aus verschiedenen Kategorien**

### RAID (Redundanz)

| Level | Beschreibung | Ausfallsicherheit |
|---|---|---|
| RAID 0 | Striping (schnell) | Keine |
| RAID 1 | Mirroring | 1 Disk |
| RAID 5 | Striping + Parity | 1 Disk |
| RAID 6 | Doppelte Parity | 2 Disks |

---

## T-WEB — WEBSEITEN-RECHTLICHES

### Impressum (Pflichtangaben CH/EU)

- Firmenname / Name
- Adresse (physisch)
- E-Mail
- UID (bei Handelsregistereintrag)
- Kontaktmöglichkeit

### Datenschutzerklärung (Pflichtinhalt)

- Wer sammelt Daten (Verantwortlicher)
- Welche Daten werden gesammelt
- Zweck der Datensammlung
- Rechtsgrundlage
- Empfänger/Weitergabe
- Speicherdauer
- Rechte der Betroffenen
- Kontakt Datenschutz

### Cookie-Banner

**Erforderlich wenn:**
- Tracking-Cookies (Analytics, Marketing)
- Personalisierung

**Nicht erforderlich für:**
- Technisch notwendige Cookies (Session, Warenkorb)

**DSGVO-konform:**
- Opt-in für nicht-essentielle Cookies
- Ablehnungs-Button gleich sichtbar wie Akzeptieren
- Keine vorausgewählten Checkboxen

### AGB

- Nicht gesetzlich vorgeschrieben
- Regeln Vertragsbeziehung
- Müssen zugänglich sein VOR Vertragsschluss

---

## T-LIZENZ — LIZENZIERUNGSMODELLE

| Lizenz | Bedeutung | Darf man... |
|---|---|---|
| **Copyright ©** | Alle Rechte vorbehalten | Nur mit Erlaubnis nutzen |
| **Public Domain** | Gemeinfrei, keine Rechte | Alles, keine Einschränkungen |
| **Fair Use** | Eingeschränkte Nutzung (US) | Zitat, Bildung, Kritik |
| **Creative Commons** | Modulare Lizenzen | Je nach CC-Typ |

### Creative Commons Bausteine

| Kürzel | Bedeutung |
|---|---|
| **BY** | Namensnennung erforderlich |
| **SA** | Share Alike — gleiche Lizenz weitergeben |
| **NC** | Non-Commercial — keine kommerzielle Nutzung |
| **ND** | No Derivatives — keine Bearbeitung |

**Beispiele:**
- CC BY = Namensnennung, sonst alles erlaubt
- CC BY-NC = Namensnennung, nicht kommerziell
- CC BY-SA = Namensnennung, gleiche Lizenz
- CC BY-NC-ND = Namensnennung, nicht kommerziell, keine Bearbeitung

---

## T-BEDRO — BEDROHUNGEN

### Bedrohungskategorien

| Kategorie | Beispiele |
|---|---|
| **Höhere Gewalt** | Feuer, Wasser, Erdbeben, Stromausfall |
| **Technisches Versagen** | Hardwaredefekt, Softwarefehler, Netzwerkausfall |
| **Vorsätzliche Handlung** | Hacking, Malware, Sabotage, Diebstahl |
| **Menschliche Fehlhandlung** | Versehentliches Löschen, Fehlkonfiguration |
| **Organisatorische Mängel** | Fehlende Richtlinien, mangelnde Schulung |

### Social Engineering

| Angriff | Beschreibung |
|---|---|
| Phishing | Fake-E-Mail/Webseite |
| Spear Phishing | Gezielt auf Person/Firma |
| Pretexting | Vorwand erfinden |
| Baiting | Köder (USB-Stick) |
| Tailgating | Hinterher-Einschleichen |

---

## T-ISMS — INFORMATIONSSICHERHEIT-MANAGEMENT

### Was ist ein ISMS?

- Systematischer Ansatz zur Informationssicherheit
- Kontinuierlicher Verbesserungsprozess (PDCA)
- Dokumentation, Richtlinien, Kontrollen

### Standards

| Standard | Beschreibung |
|---|---|
| ISO 27001 | Internationaler ISMS-Standard, zertifizierbar |
| ISO 27002 | Massnahmenkatalog zu 27001 |
| BSI-Grundschutz | Deutscher Standard, sehr detailliert |

### PDCA-Zyklus

1. **Plan** — Risiken analysieren, Massnahmen planen
2. **Do** — Massnahmen umsetzen
3. **Check** — Wirksamkeit prüfen
4. **Act** — Verbessern, anpassen

---

## X-TRAP — FALLEN & HÄUFIGE FEHLER

| # | Falle | Fix |
|---|---|---|
| 1 | C/I/A verwechseln | C=Wer sieht's, I=Ist's korrekt, A=Ist's da |
| 2 | Datenschutz ≠ Datensicherheit | Datenschutz=RECHT, Datensicherheit=TECHNIK |
| 3 | IT-Sicherheit = Informationssicherheit | NEIN! IT-Sicherheit ist nur Teil davon |
| 4 | Alle Personendaten gleich behandeln | Besonders schützenswerte = strengere Regeln |
| 5 | Technisch/Organisatorisch verwechseln | Passwort-RICHTLINIE=O, Passwort-SYSTEM=T |
| 6 | DSGVO ignorieren für CH | Gilt auch für CH wenn EU-Bezug |
| 7 | Cookie-Banner immer nötig | Nur für Tracking, nicht für technische |
| 8 | Public Domain = Creative Commons | NEIN! PD = keine Rechte, CC = definierte Rechte |
| 9 | RAID = Backup | NEIN! RAID = Verfügbarkeit, Backup = Recovery |
| 10 | WPA2 Passwort reicht | Muss STARK sein, nicht "12345678" |

---

## X-GLOSS — GLOSSAR

| Begriff | Bedeutung |
|---|---|
| CIA | Confidentiality, Integrity, Availability |
| DSG | Datenschutzgesetz (Schweiz) |
| DSGVO | Datenschutz-Grundverordnung (EU) |
| ISMS | Informationssicherheit-Management-System |
| MFA/2FA | Multi-/Zwei-Faktor-Authentisierung |
| NDA | Non-Disclosure Agreement (Geheimhaltung) |
| PII | Personally Identifiable Information |
| DPO | Data Protection Officer |
| BSI | Bundesamt für Sicherheit in der Informationstechnik (DE) |
| NCSC | Nationales Zentrum für Cybersicherheit (CH) |
| Opt-in | Aktive Zustimmung erforderlich |
| Opt-out | Widerspruch möglich |
| CC | Creative Commons |
| AGB | Allgemeine Geschäftsbedingungen |

---

## PREDICTED TEST STRUCTURE — LB1 (40%)

Basierend auf Übungsaufgaben-Analyse:

| Aufgabentyp | Punkte (ca.) | Wahrscheinlichkeit |
|---|---|---|
| CIA-Zuordnung (Szenarien) | 4-6 | ⭐⭐⭐ Sehr hoch |
| Begriffe definieren/unterscheiden | 3-4 | ⭐⭐⭐ Sehr hoch |
| Enterprise Architecture Einordnung | 2-4 | ⭐⭐ Hoch |
| DSG-Szenarien (zulässig/nicht) | 4-6 | ⭐⭐⭐ Sehr hoch |
| Massnahmen kategorisieren (T/R/O) | 4-6 | ⭐⭐⭐ Sehr hoch |
| Technische Massnahmen empfehlen | 3-4 | ⭐⭐ Hoch |
| Webseiten-Pflichten (Impressum etc.) | 2-3 | ⭐⭐ Hoch |
| Lizenzmodelle | 2-3 | ⭐ Mittel |
| Bedrohungen kategorisieren | 2-3 | ⭐ Mittel |

**Erwartete Dauer:** 45-60 Minuten
**Erwartete Punkte:** 30-40 total
**Notenformel:** (Punkte × 5 / Max) + 1
