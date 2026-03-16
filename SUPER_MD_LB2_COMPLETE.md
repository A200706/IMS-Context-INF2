# MODUL 114 — SUPER MD: KAPITEL 7–11 (LB1 Teil 2 / LB2 Prüfungsstoff)

> Codierungs-, Kompressions- und Verschlüsselungsverfahren einsetzen
> Quelle: Smartlearn Modul 114 Onlinekurs — Daniel Schär

---

## K07 — KOMPRESSION (verlustfrei)

### Begriffe
- **Kompression**: Redundante Informationen entfernen → kürzere Darstellung
- **Dekompression**: Umkehrung der Kompression
- **Verlustfrei**: Originaldaten können exakt wiederhergestellt werden
- **Verlustbehaftet**: Teil der Information geht verloren (nur "unwichtige" Daten)

### Kompressionsfaktor & Kompressionsrate
- **Kompressionsfaktor** = Dateigrösse_unkomprimiert / Dateigrösse_komprimiert
- **Kompressionsrate** = Dateigrösse_komprimiert / Dateigrösse_unkomprimiert = 1 / Kompressionsfaktor

Beispiel: Unkomprimiert 400 Bit, komprimiert 73 Bit → Faktor = 400/73 ≈ 5.5 → Rate ≈ 18%

### Ansätze verlustfreie Kompression

| Verfahren | Prinzip | Einsatz |
|---|---|---|
| Lauflängencodierung | Zählt aufeinanderfolgende gleiche Zeichen (z.B. 0000 → 4×0) | Nur Spezialfälle |
| Wörterbuchverfahren | Häufige Muster → kurzer Code | Gleichartige Muster |
| Huffman-Code | Optimierter Code pro Datei, häufige Zeichen = kurz | ZIP, JPEG (Teilschritt) |

### Huffman-Code — Algorithmus (PRÜFUNGSRELEVANT)
1. Jedes Zeichen aufschreiben
2. Häufigkeit über jedes Zeichen schreiben
3. Die beiden niedrigsten (freien) Häufigkeiten zu einem Summenknoten verbinden
4. Schritt 3 wiederholen bis Stammknoten (Totalsumme) erreicht
5. An jeder Verzweigung: links = 0, rechts = 1 (oder umgekehrt, konsistent bleiben)
6. Binärcode jedes Zeichens vom Stammknoten ablesen

Wichtig: Code-Tabelle muss der komprimierten Datei beigefügt werden (für Dekompression).

Beispiel "IM WESTEN NICHTS NEUES":
- Unkomprimiert (Unicode 16 Bit): 21 Zeichen × 16 = 336 Bit
- Huffman-codiert: 73 Bit
- Kompressionsfaktor ≈ 336/73 ≈ 4.6 → Rate ≈ 22%

---

## K08 — REDUKTION (verlustbehaftet)

### Begriff
- **Reduktion** = verlustbehaftete Kompression
- Aufnahmegeräte sind empfindlicher als menschliche Sinne → Daten entfernen die der Mensch nicht wahrnimmt
- Qualität wird reduziert soweit die Anwendung es erlaubt
- Danach oft noch verlustfreie Kompression (z.B. Huffman)

### Audio-Dateien

#### AD-Wandlung (Aufnahme)
- Analoges Signal (Schallwelle) wird in regelmässigen Abständen abgetastet
- Amplitudenwert wird binär gespeichert

#### Sampling-Rate
- Wie oft das Signal abgetastet wird (Abtastungen pro Sekunde)
- Höhere Rate = mehr Messpunkte = genauer = grössere Datei
- CD-Qualität: **44.1 kHz** (44'100 Abtastungen/s)

#### Sampling-Tiefe
- Wie fein der Messwert auf der Y-Achse angegeben wird
- 8 Bit = 256 Stufen, 16 Bit = 65'536 Stufen
- Verdoppelung der Tiefe = Verdoppelung der Dateigrösse
- CD-Qualität: **16 Bit**

#### CD-Qualität komplett
- 2 Kanäle (Stereo) × 44'100 Hz × 16 Bit = 1'411'200 Bit/s ≈ 176 KB/s
- Format: **.wav** (unkomprimiert)

#### Psychoakustische Reduktion (z.B. MP3)
Nutzt Schwächen des menschlichen Gehörs:

| Effekt | Beschreibung | Einsparung |
|---|---|---|
| **Hörschwelle** | Töne unter bestimmter Lautstärke (abhängig von Frequenz) sind unhörbar | Alles unter der Hörschwelle weglassen |
| **Maskierung** | Lauter Ton verdeckt leisere Töne in Nachbarfrequenzen | Verdeckte Frequenzen weglassen |
| **Nachmaskierung** | Nach lautem Ton können leisere Töne kurzzeitig nicht gehört werden | Nachfolgende leise Töne weglassen |

### Bild-Dateien

#### Aufnahme
- Bild wird in Pixel aufgeteilt
- Pro Pixel: Farbinformation gespeichert
- Dateigrösse = Anzahl Pixel × Farbtiefe

#### Farbtiefe

| Typ | Bit/Pixel | Farben | Format-Beispiel |
|---|---|---|---|
| Schwarzweiss | 1 | 2 (schwarz/weiss) | - |
| Graustufen | 4 | 16 Schattierungen | - |
| GIF | 8 | 256 | .gif |
| Real Color | 15 | 32'768 | - |
| True Color | 24 | 16'777'216 | .bmp |

- True Color: je **8 Bit für R, G, B** (Rot, Grün, Blau)
- Real Color: je **5 Bit für R, G, B**

#### JPEG-Reduktion
- Pixel werden zu grösseren Einheiten zusammengefasst
- Vor allem dort wo wenig Kontraste sind
- Stärke der Kompression einstellbar (Qualitätsstufe)

### Berechnung Dateigrösse (Audio)
Formel: Kanäle × Sampling-Rate × Sampling-Tiefe × Dauer = Dateigrösse in Bit

Beispiel 10s Stereo CD: 2 × 44'100 × 16 × 10 = 14'112'000 Bit = 1'764'000 Byte ≈ 1.7 MB

### Berechnung Dateigrösse (Bild)
Formel: Breite × Höhe × Farbtiefe = Dateigrösse in Bit

Beispiel 1920×1080 True Color: 1920 × 1080 × 24 = 49'766'400 Bit ≈ 5.9 MB

---

## K09 — VEKTORGRAFIKEN

### Bitmap vs. Vektor

| Eigenschaft | Bitmap (Raster) | Vektor (SVG) |
|---|---|---|
| Speicherung | Jedes Pixel einzeln | Zeichenanleitung (Koordinaten + Befehle) |
| Skalierung | Qualitätsverlust beim Vergrössern | Kein Qualitätsverlust (wird neu berechnet) |
| Dateigrösse | Gross (jedes Pixel) | Klein (nur Befehle) |
| Geeignet für | Fotos, komplexe Bilder | Zeichnungen, Pläne, Logos |
| Nachteil | Pixelig bei Zoom | Nicht für komplexe Bilder mit vielen Farben |

### SVG (Scaleable Vector Format)
- HTML-ähnlicher Code
- Koordinatensystem: Ursprung **oben links**

### SVG-Grundstruktur
```
<svg width="200" height="200">
  <circle cx="100" cy="100" rx="50" ry="50" fill="red" stroke="black"/>
  <path d="M 10 10 L 100 100" fill="none" stroke="blue"/>
</svg>
```

### SVG-Tags
- `<svg>` / `</svg>` — Zeichnungsfeld mit Höhe/Breite definieren
- `<circle>` — Ellipse: cx, cy (Mittelpunkt), rx, ry (Radien X/Y)
- `<path>` — Linienstrang
- `fill` — Füllfarbe (oder "none")
- `stroke` — Stiftfarbe

### Path-Befehle (PRÜFUNGSRELEVANT)

| Befehl | Bedeutung |
|---|---|
| M | moveto (Cursor bewegen, ohne zu zeichnen) |
| L | lineto (gerade Linie zum Punkt) |
| C | curveto |
| S | smooth curveto |
| Q | quadratic Bezier curve |
| A | elliptical arc |
| Z | closepath (Pfad schliessen) |

### Gross- vs. Kleinschreibung
- **GROSS** (M, L, C...) = **absolute** Koordinaten (bezogen auf Ursprung 0,0)
- **klein** (m, l, c...) = **relative** Koordinaten (bezogen auf aktuelle Cursor-Position)

### Tools
- w3schools.com — Online-Editor für SVG
- SCRIBUS — Open-Source SVG-Software
- Visual Studio mit SVG Add-In

---

## K10 — VERSCHLÜSSELUNG: Geschichte & Grundsätzliches

### Schutzziele CIA (PRÜFUNGSRELEVANT)

| Buchstabe | Ziel | Deutsch | Erreicht durch |
|---|---|---|---|
| **C** | Confidentiality | Vertraulichkeit | Verschlüsselung |
| **I** | Integrity | Integrität | Hash-Funktion |
| **A** | Authenticity | Authentizität | Digitale Signatur |

Hinweis: Bei allgemeinem Informationsschutz steht A oft für "Availability" (Verfügbarkeit).

### Steganographie
- **Definition**: Kunst des Versteckens von Informationen in einem Trägermedium (Container)
- Der Empfänger braucht nur die Anleitung zum Auffinden
- Dritte schöpfen keinen Verdacht

Beispiele:
- Text in Text
- Bilder in Bildern
- First Letter Messages
- Bitströme in Dateien
- Skytalen (Stab mit Papierstreifen)

### Monoalphabetische Chiffren
- Jeder Buchstabe → genau ein Geheimzeichen (immer dasselbe)
- Beispiele: Freimaurer-Chiffre, Tempelritter-Chiffre

#### Caesar-Chiffre (PRÜFUNGSRELEVANT)
- Buchstaben um feste Anzahl Stellen im Alphabet verschieben
- Schlüssel = Buchstabe der Verschiebung (A=0, B=1, C=2, ...)
- Beispiel: Schlüssel D → A wird D, B wird E, ...
- Caesar-Scheibe: innerer Ring drehbar

#### Mary Stuart Chiffre
- Monoalphabetisch + Zusätze:
  - Zeichen ohne Bedeutung (Verwirrung)
  - "Dowbleth" = nächster Buchstabe doppelt
  - Eigene Zeichen für häufige Wörter
- Wurde trotzdem geknackt

### Kryptoanalyse monoalphabetischer Chiffren
- **Buchstabenhäufigkeit**: Jede Sprache hat eigenen "Fingerabdruck"
- Bei längeren Texten reicht Häufigkeitsanalyse zum Entschlüsseln
- Verfeinert durch: häufigste Nachbarn der Buchstaben

### Symmetrische vs. Asymmetrische Verschlüsselung

| Eigenschaft | Symmetrisch | Asymmetrisch |
|---|---|---|
| Schlüssel | Gleicher Schlüssel für Sender & Empfänger | Public Key + Private Key |
| Problem | Schlüsselaustausch unsicher | - |
| Vorteil | Schnell, wenig Rechenleistung | Schlüsselaustausch sicher |
| Nachteil | Schlüssel muss übermittelt werden | Langsam, viel Rechenleistung |
| Beispiel | IPSec | RSA, IKE |

### Hybride Verfahren (PRÜFUNGSRELEVANT)
Kombination beider Vorteile:
1. **Verbindungsaufbau**: Asymmetrisch (z.B. IKE) → sicherer Schlüsselaustausch
2. **Datenübertragung**: Symmetrisch (z.B. IPSec) → schnelle Verschlüsselung

Praxisbeispiel: **Site-to-Site VPN**
- IKE (asymmetrisch, langsam) tauscht den symmetrischen Schlüssel aus
- IPSec (symmetrisch, schnell) verschlüsselt die IP-Pakete

---

## K11 — VERSCHLÜSSELUNG: Moderne Verfahren

### RSA-Verfahren (Vertraulichkeit) (PRÜFUNGSRELEVANT)
- **RSA** = Rivest–Shamir–Adleman
- Asymmetrisches Verfahren
- Schl üsselpaar: Public Key (öffentlich) + Private Key (geheim)
- Public Key → verschlüsseln / Signaturen prüfen
- Private Key → entschlüsseln / signieren
- Private Key kann nicht aus Public Key berechnet werden (mit realistischem Aufwand)

### XOR-Verschlüsselung (PRÜFUNGSRELEVANT)
Anwendung eines binären Schlüssels auf eine binäre Datei:

```
Klartext  XOR  Schlüssel  =  Chiffrat
Chiffrat  XOR  Schlüssel  =  Klartext
```

XOR-Wahrheitstabelle:
| A | B | A XOR B |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

Beispiel:
- Klartext:  1 0 1 1 0 1
- Schlüssel: 1 1 0 1 1 0
- Chiffrat:  0 1 1 0 1 1
- Chiffrat XOR Schlüssel: 1 0 1 1 0 1 = Klartext ✓

### Hash-Funktionen (Integrität) (PRÜFUNGSRELEVANT)
- Mathematische Funktion → generiert "Fingerabdruck" einer Datei
- Kleinste Änderung → komplett anderer Hash-Wert
- Grosse Eingabemenge → kleinere Zielmenge (feste Länge)
- Nicht injektiv (verschiedene Eingaben können gleichen Hash haben, aber extrem unwahrscheinlich)
- Einsatz: Prüfen ob Datei verändert wurde

### Digitale Signatur (Authentizität) (PRÜFUNGSRELEVANT)
Kombination aus Hash-Funktion + asymmetrischer Verschlüsselung:

**Signieren (Sender):**
1. Hash der Nachricht berechnen
2. Hash mit eigenem **Private Key** verschlüsseln → das ist die Signatur
3. Nachricht + Signatur senden

**Verifizieren (Empfänger):**
1. Hash der empfangenen Nachricht berechnen
2. Signatur mit **Public Key** des Senders entschlüsseln → ergibt Original-Hash
3. Beide Hashes vergleichen → stimmen überein = authentisch + integer

---

## PRÜFUNGSHINWEISE (LB1 Teil 2)

- **Stoff**: Kapitel 06–11
- **Dauer**: 60 Minuten
- **Hilfsmittel**: Spicker (2 Seiten A4) + Taschenrechner erlaubt
- **LB2**: Gruppenarbeit (Vortrag/PDF), 20% der Modulnote — separates Projekt

### Typische Rechenaufgaben
1. Kompressionsfaktor / Kompressionsrate berechnen
2. Huffman-Baum erstellen und Bitstrom codieren
3. Audio-Dateigrösse berechnen (Kanäle × Rate × Tiefe × Dauer)
4. Bild-Dateigrösse berechnen (Breite × Höhe × Farbtiefe)
5. Caesar-Chiffre ver-/entschlüsseln
6. XOR-Verschlüsselung durchführen
7. RSA-Beispiel (vereinfacht)
8. SVG-Code lesen/schreiben

### Typische Erklärungsaufgaben
1. Verlustfrei vs. verlustbehaftet erklären
2. CIA-Schutzziele erklären
3. Symmetrisch vs. asymmetrisch vs. hybrid erklären
4. Psychoakustische Effekte beschreiben
5. Bitmap vs. Vektor vergleichen
6. Steganographie erklären
7. Hash-Funktion Zweck erklären
8. Digitale Signatur Ablauf beschreiben
