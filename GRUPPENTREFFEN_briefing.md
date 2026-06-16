# DLDS-Klimaprojekt — Gruppentreffen-Briefing

Das gehst du morgen mit der Gruppe durch. Ziel des Treffens: Aufgaben verteilen + gemeinsamen Workflow festlegen, damit ab dann alle parallel arbeiten können.

**Kontext in 2 Sätzen:** Wir analysieren die DWD-Jahresmitteltemperaturen für Deutschland + Bundesländer (1881–2025) und zeigen, wie stark und wie schnell es sich erwärmt. Abgabe: ein Jupyter-Notebook + Datendatei (**13.07.**), Präsentation **14./15.07.**

---

## 1. Die Work Packages (WPs)

**Abhängigkeit:** WP1 ist das Fundament und blockiert alles → ist **fertig**. WP2–5 laufen danach **voll parallel** → WP6 Integration → WP7 Präsi.

| WP | Was | Liefert | Owner |
|----|-----|---------|-------|
| **WP1 Daten & Setup** ✅ | Rohdaten ziehen, putzen, gemeinsame CSV + Notebook-Skelett | `temp_annual_regions.csv` (145×18, geprüft), `klima_analyse.ipynb` | Yesunkh (fertig) |
| **WP2 = D1** | Deutschlandweite Erwärmung: Zeitreihe + Dekadenmittel | Fig 1+2 + Kennzahlen + Takeaway | ? |
| **WP3 = D2** | Erwärmung je Bundesland: Median/IQR/sd, Nord-Süd | Fig 5 + Takeaway | ? |
| **WP4 = I1** | Lineare Regression Temp~Jahr: Steigung **mit 95%-CI**, pre/post-1980 | Fig 3 + Rate/Dekade | ? |
| **WP5 = I2** | Bootstrap-CI Periodenvergleich + Welch-t + Cohen's d | Fig 4 + CI | ? |
| **WP6 Integration + QA** | scratch-Notebooks zusammenführen, „Restart & Run All", Mini-Audit | abgabefähiges `klima_analyse.ipynb` | ? |
| **WP7 Präsentation** | 5 Folien (1 pro Analyse) + Q&A-Drill | Deck | alle |

**Bewertet wird** (wichtig für alle): ≥2 deskriptive + ≥2 inferentielle Analysen (haben wir: D1,D2 / I1,I2), ≥5 Figures (haben wir: Fig 1–5), jede Code-Zelle mit Beschreibungstext, Notebook reproduzierbar (Seed gesetzt). Code-Vorlagen für jede Analyse liegen fertig in `projekt_schritte.md` (Blocks 2–5) — niemand startet bei null.

---

## 2. Workflow (Git + Modularisierung)

**Warum so:** Jupyter-Notebooks erzeugen bei gemeinsamem Editieren fiese Merge-Konflikte. Lösung: **jede/r ein eigenes `scratch_<name>.ipynb`**, alle starten von derselben CSV, **eine** Person merged am Ende ins `klima_analyse.ipynb`.

### Schritt 0 — Repo aufsetzen (einmalig, Yesunkh)
```bash
cd ~/Desktop/Claude/Claude\ Projects/Code/fdlds/Projekt/klima
printf "%s\n" ".ipynb_checkpoints/" ".DS_Store" "__pycache__/" "*.pyc" > .gitignore
git init
git add .
git commit -m "WP1: raw + clean CSV + notebook skeleton"
# leeres Repo auf GitHub anlegen (ohne README), dann:
git remote add origin https://github.com/<dein-user>/klima-dlds.git
git branch -M main
git push -u origin main
```
Danach die drei anderen als **Collaborators** einladen (GitHub → Settings → Collaborators). Die `temp_annual_regions.csv` + Rohdatei kommen mit ins Repo → alle haben identische Daten, Notebook läuft offline.

### Schritt 1 — alle anderen: einmal klonen
```bash
git clone https://github.com/<dein-user>/klima-dlds.git
cd klima-dlds
```

### Schritt 2 — täglicher Ablauf (jede/r)
```bash
git pull                         # IMMER zuerst
# arbeite NUR in deinem scratch_<name>.ipynb
git add scratch_<name>.ipynb figures/<deine_figuren>.png
git commit -m "D2: Erwärmung je Bundesland + Fig5"
git push
```

### Die 3 Regeln (das verhindert 90% der Probleme)
1. **Start immer von der CSV:** `df = pd.read_csv("data/clean/temp_annual_regions.csv")` — nie an der Rohdatei rumbasteln.
2. **Eigenes `scratch_<name>.ipynb`** — `klima_analyse.ipynb` rührt nur der Integrator an.
3. **`git pull` vor jedem Arbeiten, `git push` danach.** Figures unter `figures/figN_*.png` ablegen (Namen aus der Tabelle oben), damit nichts kollidiert.

### Fallback ohne Git
Falls Git nervt: CSV einmal an alle (Drive/WhatsApp), jede/r arbeitet lokal in seinem Notebook, am Ende schickt jede/r ihr scratch-Notebook + Figures an den Integrator. Funktioniert auch, nur weniger sauber.

---

## 3. Aufgabenverteilung — Vorschlag (im Treffen festklopfen)

4 Leute, 4 Analysen — sauber teilbar:

| Person | WP | Aufwand |
|--------|-----|---------|
| Yesunkh | WP1 ✅ + **WP6 Integration** (+ Repo-Owner) | mittel |
| Ali | **D1** Zeitreihe (Block 2) | klein |
| Oksana | **D2** Bundesländer (Block 3) | klein |
| Madlen | **I1** Regression (Block 4) | mittel |
| → **I2** Bootstrap (Block 5) | offen — wer Kapazität hat (oder Yesunkh dazu) | mittel |

**Im Treffen entscheiden:** (a) wer hostet das Repo + lädt ein, (b) wer nimmt welche Analyse + wer macht I2, (c) wer ist Integrator, (d) nächster Sync-Termin (Vorschlag: kurzer Check Ende der Woche).
