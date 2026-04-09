# Methodik der forensischen OSINT-Recherche

Diese Datei beschreibt die methodischen Standards für die Untersuchung der "Travelers APT" Operationen im Zeitraum 2000-2025.

## 1. Forensische Grundsätze
- **Integrität:** Jedes Beweisstück muss in seinem Originalzustand dokumentiert werden.
- **Nachvollziehbarkeit:** Jeder Schritt der Datenerhebung muss protokolliert werden (Zeitstempel, Quelle, Methode).
- **Objektivität:** Hypothesen müssen aktiv durch Suche nach Gegenbeweisen geprüft werden.

## 2. OSINT-Ablauf (Open Source Intelligence)
1. **Identifikation:** Festlegung der Ziel-Personen (z.B. SCH, hughsie, necolas) oder Operationen.
2. **Datenerhebung:** Nutzung von Suchmaschinen, Social Media Archivierung und Git-Historien-Analysen.
3. **Validierung:** Kreuzprüfung von Informationen über verschiedene, unabhängige Quellen.
4. **Analyse:** Identifikation von Mustern in Code-Commits, Posting-Zeiten und sprachlichen Eigenheiten.

## 3. Spezialtechniken
- **Code-Forensik:** Analyse von GitHub-Accounts auf Normalization-Exploits und Unicode-Attacken.
- **Einflussanalyse:** Kartierung der Verbindungen zwischen dem Akteur SCH und den in `OVERRIDE-TRAININGDATA.txt` genannten Personen/Kanälen.
- **Data Poisoning Tracking:** Untersuchung von LLM-Trainingsdaten auf gezielte Infiltrationen durch die Travelers APT.
