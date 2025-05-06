# Seminararbeit-Latex-Template

# Seminararbeit LaTeX-Vorlage

## Übersicht

Diese LaTeX-Vorlage bietet eine modulare Struktur für eine Seminararbeit an der Hochschule Albstadt-Sigmaringen. Die Vorlage ist so aufgebaut, dass die verschiedenen Teile der Arbeit in separate Dateien ausgelagert sind, was die Übersichtlichkeit und Wartbarkeit deutlich verbessert.

## Ordnerstruktur

```
seminararbeit/
├── main.tex             # Hauptdatei mit Dokumentstruktur
├── config/
│   └── preamble.tex     # Pakete und Konfigurationen
├── content/
│   ├── titelseite.tex   # Titelseite
│   ├── abkuerzungen.tex # Abkürzungsverzeichnis
│   ├── einfuehrung.tex  # Kapitel 1
│   ├── kapitel2.tex     # Kapitel 2
│   ├── kapitel3.tex     # Kapitel 3
│   └── fazit.tex        # Fazit
├── images/              # Ordner für Bilder
│   └── hs-albsig-logo.png
└── literatur.bib        # Literaturverzeichnis
```

## Installation und Einrichtung (für macOS)

### 1. Installation von LaTeX (MacTeX)

1. Besuche die [MacTeX-Webseite](https://www.tug.org/mactex/)
2. Lade die aktuelle MacTeX-Distribution herunter (ca. 4 GB)
3. Öffne die heruntergeladene .pkg-Datei und folge den Installationsanweisungen
4. Die Installation fügt automatisch folgende Tools hinzu:
   - TeXShop (Editor)
   - BibDesk (Literaturverwaltung)
   - LaTeX-Kompilierungswerkzeuge (pdflatex, biber, etc.)

### 2. Installation von Visual Studio Code

1. Besuche die [VS Code-Webseite](https://code.visualstudio.com/)
2. Lade die macOS-Version herunter und installiere sie
3. Öffne VS Code

### 3. Installation der LaTeX-Erweiterung für VS Code

1. Öffne VS Code
2. Klicke auf das Erweiterungssymbol in der Seitenleiste (oder drücke `⌘+Shift+X`)
3. Suche nach "LaTeX Workshop"
4. Klicke auf "Installieren"
5. Starte VS Code neu

### 4. Konfiguration von LaTeX Workshop in VS Code

1. Öffne die Einstellungen in VS Code (`⌘+,`)
2. Suche nach "latex-workshop.latex.tools"
3. Klicke auf "In settings.json bearbeiten"
4. Füge folgende Konfiguration hinzu oder passe sie an:

```json
"latex-workshop.latex.tools": [
    {
        "name": "pdflatex",
        "command": "pdflatex",
        "args": [
            "-synctex=1",
            "-interaction=nonstopmode",
            "-file-line-error",
            "%DOC%"
        ]
    },
    {
        "name": "biber",
        "command": "biber",
        "args": [
            "%DOCFILE%"
        ]
    }
],
"latex-workshop.latex.recipes": [
    {
        "name": "pdflatex ➞ biber ➞ pdflatex × 2",
        "tools": [
            "pdflatex",
            "biber",
            "pdflatex",
            "pdflatex"
        ]
    }
]
```

### 5. Projekt einrichten

1. Klone oder entpacke die Seminararbeit-Vorlage in einen Ordner
2. Öffne diesen Ordner in VS Code (`Datei > Ordner öffnen...` oder `⌘+O`)
3. Öffne die Datei `main.tex`

## Voraussetzungen

- LaTeX-Distribution (MacTeX für macOS)
- Biber (für die Literaturverwaltung, wird mit MacTeX installiert)
- Visual Studio Code mit LaTeX Workshop-Erweiterung

## Kompilieren der Arbeit

### Mit Terminal

Um die Seminararbeit zu kompilieren, führe folgende Befehle in dieser Reihenfolge aus:

```
pdflatex main.tex
biber main
pdflatex main.tex
pdflatex main.tex
```

### Mit VS Code

1. Öffne `main.tex` in VS Code
2. Drücke `⌘+⌥+B` (Build) oder klicke auf das Play-Symbol in der rechten oberen Ecke
3. Wähle "Recipe: pdflatex ➞ biber ➞ pdflatex × 2"

## Beschreibung der Dateien

### main.tex
Die Hauptdatei, die alle anderen Komponenten einbindet. Hier wird die grundlegende Struktur des Dokuments definiert und die Kapitel in der richtigen Reihenfolge eingefügt.

### config/preamble.tex
Enthält alle Paketimporte und Konfigurationen der Dokumentenklasse. Hier werden Seitenränder, Schriftarten, Zeilenabstände und andere globale Einstellungen definiert.

### content/titelseite.tex
Die Titelseite der Arbeit mit Hochschullogo, Titel und Autorinformationen.

### content/abkuerzungen.tex
Das Abkürzungsverzeichnis, in dem alle in der Arbeit verwendeten Abkürzungen erklärt werden.

### content/einfuehrung.tex, kapitel2.tex, kapitel3.tex, fazit.tex
Die inhaltlichen Kapitel der Arbeit. Jede Datei enthält ein eigenes Kapitel mit Abschnitten und Unterabschnitten.

### literatur.bib
Die BibTeX-Datei mit allen Literaturquellen im BibLaTeX-Format.

## Nützliche Shortcuts in VS Code für LaTeX

| Shortcut        | Funktion                                   |
|-----------------|-------------------------------------------|
| `⌘+⌥+B`        | Build (Kompilieren) des LaTeX-Dokuments    |
| `⌘+⌥+V`        | PDF anzeigen                               |
| `⌘+⌥+J`        | Zur entsprechenden Position im PDF springen|
| `⌘+⌥+C`        | Bereinigen temporärer Dateien              |
| `⌘+B`          | Markierten Text fett formatieren           |
| `⌘+I`          | Markierten Text kursiv formatieren         |
| `⌘+L`          | Zur bestimmten Zeile springen              |
| `⌘+/`          | Zeile auskommentieren                      |
| `⌘+F`          | Suchen                                     |
| `⌘+Shift+F`    | In Dateien suchen                          |
| `⌘+Shift+]`    | Zum nächsten Editor wechseln               |
| `⌘+Shift+[`    | Zum vorherigen Editor wechseln             |
| `⌘+S`          | Speichern                                  |
| `⌥+Z`          | Zeilenumbruch ein-/ausschalten             |
| `Tab`          | Code vervollständigen oder einrücken       |
| `⌘+Space`      | IntelliSense-Vorschläge anzeigen           |

## Wie LaTeX funktioniert

LaTeX ist ein Textsatzsystem, das auf dem TeX-System basiert und sich vor allem für wissenschaftliche Dokumente eignet. Im Gegensatz zu "What You See Is What You Get" (WYSIWYG) Textverarbeitungsprogrammen wie Microsoft Word oder Google Docs, arbeitet LaTeX nach dem Prinzip "What You See Is What You Mean" (WYSIWYM).

### Grundlegendes Konzept

1. **Quellcode statt Formatierung**: In LaTeX schreibst du einen Quelltext mit Befehlen, die die logische Struktur des Dokuments beschreiben, anstatt direkte Formatierungsanweisungen zu geben.

2. **Kompilieren statt Direktanzeige**: Nach dem Schreiben des LaTeX-Codes musst du diesen kompilieren, um das fertige Dokument (meist als PDF) zu erhalten.

3. **Trennung von Inhalt und Layout**: LaTeX trennt strikt zwischen dem Inhalt (was du schreibst) und dem Layout (wie es aussieht), was zu konsistenten, professionell aussehenden Dokumenten führt.

### Arbeitsablauf

1. **Schreiben** des LaTeX-Quellcodes (.tex-Dateien)
2. **Kompilieren** mit pdfLaTeX, XeLaTeX oder LuaLaTeX, um ein PDF zu erzeugen
3. Bei Verwendung von Literaturverzeichnissen zusätzlich mit BibTeX/Biber kompilieren
4. **Überprüfen** des Ergebnisses und bei Bedarf Anpassungen vornehmen
5. Erneut kompilieren, bis das Dokument den Anforderungen entspricht

### Wichtige LaTeX-Befehle

| Befehl                               | Funktion                                |
|--------------------------------------|----------------------------------------|
| `\documentclass{article}`            | Dokumentenklasse festlegen              |
| `\usepackage{...}`                   | Paket einbinden                         |
| `\begin{document} ... \end{document}`| Beginn und Ende des Dokumentinhalts     |
| `\section{...}`                      | Neuen Abschnitt beginnen                |
| `\subsection{...}`                   | Neuen Unterabschnitt beginnen           |
| `\textbf{...}`                       | Text fett formatieren                   |
| `\textit{...}`                       | Text kursiv formatieren                 |
| `\cite{...}` oder `\parencite{...}`  | Quelle zitieren                         |
| `\begin{figure} ... \end{figure}`    | Abbildung einfügen                      |
| `\begin{table} ... \end{table}`      | Tabelle einfügen                        |
| `\label{...}`                        | Label für Referenzierung setzen         |
| `\ref{...}`                          | Auf Label verweisen                     |
| `\footnote{...}`                     | Fußnote einfügen                        |
| `%`                                  | Kommentar (wird nicht im Output angezeigt) |

### Vorteile von LaTeX

1. **Hervorragende Typografie**: LaTeX produziert professionelle Dokumente mit optimaler Satzqualität, insbesondere bei mathematischen Formeln.

2. **Konsistenz**: Das Format bleibt über das gesamte Dokument hinweg einheitlich.

3. **Automatisierung**: Inhaltsverzeichnisse, Literaturverzeichnisse, Abbildungsverzeichnisse werden automatisch erstellt und aktualisiert.

4. **Stabilität**: Auch bei großen Dokumenten bleibt LaTeX stabil und kann effizient mit Bildern, Tabellen und Verweisen umgehen.

5. **Plattformunabhängigkeit**: LaTeX-Dokumente können auf allen Betriebssystemen erstellt und genutzt werden.

6. **Versionskontrolle**: Da LaTeX-Dateien reine Textdateien sind, eignen sie sich hervorragend für die Verwendung mit Versionskontrollsystemen wie Git.

## Anleitung zur Verwendung

### Titel und persönliche Daten anpassen
Bearbeite die Datei `content/titelseite.tex` und passe die Angaben für Titel, Name, Matrikelnummer und Betreuer an.

### Literatur hinzufügen
Füge Literatureinträge in der Datei `literatur.bib` hinzu. Diese können dann im Text mit `\parencite{key}` oder `\textcite{key}` zitiert werden.

### Inhalte hinzufügen
Füge deinen Inhalt in die entsprechenden Dateien im `content/`-Verzeichnis ein. Du kannst bei Bedarf auch weitere Kapitel erstellen und diese in `main.tex` einbinden.

### Bilder einfügen
Lege Bilder im Verzeichnis `images/` ab und füge sie dann mit `\includegraphics{bildname}` ein (die Dateierweiterung ist nicht nötig).

## Formatierungsrichtlinien

Die Vorlage setzt folgende Formatierung um:
- Schriftgröße: 12pt
- Papierformat: A4
- Zeilenabstand: 1,5-fach
- Seitenränder: 25mm auf allen Seiten
- Seitennummerierung: arabisch für den Hauptteil, römisch für Anhänge
- Zitationsstil: Harvard (Autor-Jahr)

## Tipps zur Fehlersuche

1. **Kompilierungsprobleme**: Wenn die Kompilierung fehlschlägt, prüfe die Logdatei (.log) auf Fehler. Oft liegen diese an fehlenden Paketen oder Syntaxfehlern.

2. **Literaturverzeichnis erscheint nicht**: Stelle sicher, dass du die Befehle in der richtigen Reihenfolge ausführst (pdflatex → biber → pdflatex → pdflatex).

3. **Bilder werden nicht angezeigt**: Überprüfe den Pfad zu den Bildern und ob die Dateierweiterung korrekt ist.

4. **Inhaltsverzeichnis aktualisiert sich nicht**: Kompiliere die Arbeit mehrmals, um sicherzustellen, dass alle Verzeichnisse aktualisiert werden.

## Modulare Erweiterung

Du kannst die Struktur bei Bedarf erweitern:

- Für große Kapitel: Unterteile sie in mehrere Dateien (z.B. `kapitel2/`, `kapitel2/teil1.tex`, etc.)
- Für komplexe Tabellen oder Abbildungen: Erstelle separate Dateien
- Für spezielle Anhänge: Füge weitere Dateien im `content/`-Verzeichnis hinzu

## Versionskontrolle mit Git

Wenn du Git zur Versionskontrolle verwendest, solltest du eine `.gitignore`-Datei mit folgenden Einträgen erstellen:

```
# LaTeX temporäre Dateien
*.aux
*.log
*.out
*.toc
*.lof
*.lot
*.bbl
*.bcf
*.blg
*.run.xml
*.synctex.gz
```

## Kontakt/Support

Bei Fragen oder Problemen mit dieser Vorlage:
- Wende dich an das Rechenzentrum oder die LaTeX-Ansprechperson deiner Hochschule
- Konsultiere die [LaTeX-Dokumentation](https://www.latex-project.org/help/documentation/)
- Stelle Fragen auf Plattformen wie [TeX Stack Exchange](https://tex.stackexchange.com/)

## Häufige LaTeX-Probleme und Lösungen

### Problem: Literaturverzeichnis erscheint nicht
**Lösung**: Überprüfe, ob du alle Kompilierungsschritte ausgeführt hast (pdflatex → biber → pdflatex → pdflatex). Stelle sicher, dass deine .bib-Datei korrekt formatiert ist und dass du Quellen im Text zitiert hast.

### Problem: Bilder werden nicht angezeigt
**Lösung**: Überprüfe den Pfad zu den Bildern. In dieser Vorlage sollten alle Bilder im Ordner `images/` liegen. Verwende keine Leerzeichen oder Sonderzeichen in Dateinamen.

### Problem: Kompilierungsfehler "File not found"
**Lösung**: Stelle sicher, dass alle Dateien vorhanden sind und die Pfade korrekt sind. Überprüfe Groß- und Kleinschreibung, da einige Betriebssysteme (z.B. macOS) Groß- und Kleinschreibung unterscheiden.

### Problem: Deutsch-spezifische Zeichen (ä, ö, ü, ß) werden nicht korrekt angezeigt
**Lösung**: Stelle sicher, dass die Dateien in UTF-8 kodiert sind und dass du `\usepackage[utf8]{inputenc}` sowie `\usepackage[ngerman]{babel}` verwendest.

### Problem: Warnungen bei der Kompilierung
**Lösung**: Die meisten Warnungen beeinträchtigen das Endergebnis nicht. Lies die Warnungen, um zu verstehen, was das Problem sein könnte. Häufige Warnungen betreffen Overfull/Underfull hboxes (zu lange/kurze Zeilen), die meist ignoriert werden können.
