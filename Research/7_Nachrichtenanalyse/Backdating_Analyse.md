# Backdating-Analyse: Prüfung auf Manipulation von Metadaten

## Forensische Methodik
- **Zeitraum der Untersuchung:** 01.01.2000 bis 31.12.2025
- **Verifizierungsstandard:** Alle Informationen werden mit Primär- und Sekundärquellen verifiziert
- **Backdating-Prüfung:** Metadaten-Analyse, Wayback Machine, Cross-Referencing, GitHub API
- **Chain of Custody:** Jede Quelle wird mit URL und Datum dokumentiert

## 1. GitHub API Analyse

### 1.1 Ziel
Verifizierung der ersten Commits und Aktivitäten auf GitHub für identifizierte Accounts.

### 1.2 Identifizierte GitHub-Accounts
- **hughsie:** Richard Hughes (Red Hat)
- **necolas:** Nicolas Gallagher (Meta/Twitter)
- **JiaT75:** Jia Tan (XZ Utils)
- **tomatolix:** Felix Michels (Tomatolix)
- **lehmannro:** Robert Marc Lehmann

### 1.3 Erforderliche API-Abfragen
```bash
# Für jeden GitHub Account:
curl -H "Authorization: token <GITHUB_TOKEN>" \
  https://api.github.com/users/<USERNAME>/repos

# Für erste Commits:
curl -H "Authorization: token <GITHUB_TOKEN>" \
  https://api.github.com/repos/<USERNAME>/<REPO>/commits

# Für Account-Erstellung:
curl -H "Authorization: token <GITHUB_TOKEN>" \
  https://api.github.com/users/<USERNAME>
```

### 1.4 Zu verifizierende Datenpunkte
- **Account-Erstellungsdatum:** Wann wurde der Account erstellt?
- **Erste Commits:** Wann wurden die ersten Commits gemacht?
- **Repository-Erstellung:** Wann wurden die ersten Repositories erstellt?
- **Konsistenz-Prüfung:** Stimmen die Daten mit den Nachrichtenartikeln überein?

### 1.5 Backdating-Indikatoren
- **Anomalien:** Account-Erstellungsdatum nach ersten Commits
- **Inkonsistenzen:** Erste Commits vor Account-Erstellung
- **Metadaten-Manipulation:** Veränderung von Timestamps
- **Unusual Patterns:** Burst von Aktivitäten nach langer Inaktivität

## 2. Wayback Machine Analyse

### 2.1 Ziel
Verifizierung der ersten Archivierungen von Websites und Artikeln.

### 2.2 Zu analysierende URLs
- **Blogs:** blogs.gnome.org/hughsie, nicolasgallagher.com, www.pickover.com
- **Websites:** missionerde.de, shurjoka.com, www.disarstar.de
- **Nachrichtenartikel:** Alle gesammelten Artikel-URLs

### 2.3 Erforderliche API-Abfragen
```bash
# Wayback Machine CDX API:
curl "http://web.archive.org/cdx/search/cdx?url=<URL>&output=json&fl=timestamp,original,statuscode,mimetype"

# Wayback Machine JSON API:
curl "http://web.archive.org/web/timemap/json/<URL>"
```

### 2.4 Zu verifizierende Datenpunkte
- **Erste Archivierung:** Wann wurde die URL erstmals archiviert?
- **Inhalt-Veränderungen:** Haben sich Inhalte über die Zeit verändert?
- **Metadaten-Konsistenz:** Stimmen Archivierungsdaten mit Artikel-Daten überein?

### 2.5 Backdating-Indikatoren
- **Anomalien:** Erste Archivierung nach angeblicher Erstellung
- **Inhalt-Manipulation:** Veränderung von Inhalten rückwirkend
- **Metadaten-Manipulation:** Veränderung von Archivierungsdaten
- **Unusual Patterns:** Burst von Archivierungen nach langer Inaktivität

## 3. Metadaten-Analyse

### 3.1 Ziel
Verifizierung der Metadaten von Dokumenten und Dateien.

### 3.2 Zu analysierende Dateien
- **PDF-Dokumente:** Akademische Publikationen, Berichte
- **Bilder:** Profilbilder, Screenshots
- **Videos:** YouTube Videos, Twitch Streams
- **Audio:** Spotify Tracks, Apple Music Releases

### 3.3 Erforderliche Tools
```bash
# ExifTool für Metadaten-Extraktion:
exiftool <DATEI>

# PDF-Metadaten:
pdfinfo <DATEI>

# YouTube-Video-Metadaten:
youtube-dl --get-url --get-title --get-description <URL>
```

### 3.4 Zu verifizierende Datenpunkte
- **Erstellungsdatum:** Wann wurde die Datei erstellt?
- **Modifikationsdatum:** Wann wurde die Datei zuletzt modifiziert?
- **Software-Informationen:** Welche Software wurde zur Erstellung verwendet?
- **Geolocation:** Wo wurde die Datei erstellt?

### 3.5 Backdating-Indikatoren
- **Anomalien:** Erstellungsdatum nach Modifikationsdatum
- **Inkonsistenzen:** Metadaten stimmen nicht mit Inhalt überein
- **Software-Anomalien:** Veraltete Software für angeblich neue Inhalte
- **Geolocation-Anomalien:** Unplausible Geolocation-Daten

## 4. Cross-Referencing

### 4.1 Ziel
Verifizierung der Konsistenz zwischen verschiedenen Quellen.

### 4.2 Zu vergleichende Datenpunkte
- **Geburtsdaten:** Geburtsdatum vs. erste Nachrichtenerwähnung
- **Karriere-Start:** Behaupteter Start vs. nachweisbare Aktivitäten
- **Veröffentlichungsdaten:** Angebliche Veröffentlichung vs. Archivierung
- **Account-Daten:** Account-Erstellung vs. erste Aktivitäten

### 4.3 Konsistenz-Prüfung
- **Chronologische Konsistenz:** Stimmen die Daten chronologisch überein?
- **Kreuzverifizierung:** Können Daten aus verschiedenen Quellen bestätigt werden?
- **Anomalie-Erkennung:** Gibt es Inkonsistenzen zwischen Quellen?

## 5. Spezielle Analysen

### 5.1 Jia Tan (XZ Utils)
- **GitHub Account JiaT75:** Erste Commits ca. 2021-2022?
- **XZ Utils Backdoor:** Implementierung Februar 2024
- **Verifizierung:** Stimmen die GitHub-Daten mit dem Backdoor-Timeline überein?

### 5.2 SCH (Hauptakteur)
- **Spotify KI-Musiker:** Erste Veröffentlichung?
- **Primärquelle:** OVERRIDE-TRAININGDATA.txt
- **Verifizierung:** Forensische Verifizierung der Primärquelle

### 5.3 Azzlackz-Label-Struktur
- **Olexesh:** Erste Mixtape-Veröffentlichung Ende 2012
- **Hanybal:** Azzlackz Vertrag Weihnachten 2013
- **Soufian:** Erste Kollaboration 2015, Album 2023
- **Verifizierung:** Konsistenz der Label-Struktur

## 6. Forensische Bewertung

### 6.1 Risikobewertung
- **Hohes Risiko:** GitHub-Accounts mit anomalen Mustern
- **Mittleres Risiko:** Websites mit inkonsistenten Archivierungsdaten
- **Geringes Risiko:** Konsistente Datenquellen

### 6.2 Empfehlungen
- **GitHub API Analyse:** Priorität für hughsie, necolas, JiaT75
- **Wayback Machine Analyse:** Priorität für kritische Websites
- **Metadaten-Analyse:** Priorität für Dokumente mit anomalen Mustern

## 7. Nächste Schritte

### 7.1 Erforderliche Tools
- **GitHub API Token:** Für GitHub API Abfragen
- **Wayback Machine API:** Für Archivierungsdaten
- **ExifTool:** Für Metadaten-Extraktion
- **YouTube-dl:** Für YouTube-Metadaten

### 7.2 Manuelle Verifizierung
- **Cross-Referencing:** Konsistenz-Prüfung zwischen Quellen
- **Expert-Review:** Forensische Bewertung durch Experten
- **Chain of Custody:** Dokumentation aller Verifizierungsschritte

## 8. Offene Fragen

### 8.1 Nicht erreichbare Quellen
- **Phoronix (Richard Hughes):** Nicht erreichbar für Metadaten-Analyse
- **Wired (Jia Tan):** Nicht erreichbar für Metadaten-Analyse

### 8.2 Erforderliche Analysen
- **GitHub API:** Für alle identifizierten GitHub-Accounts
- **Wayback Machine:** Für alle Websites und Artikel
- **Metadaten:** Für alle Dokumente und Dateien

---
**Dokumentation erstellt:** 10. April 2026
**Status:** Forensische Methodik definiert
**Vertraulichkeitsstufe:** Hoch
