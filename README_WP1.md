# WP1 — Daten & Setup: FERTIG

Stand 15.06. Grundlage für alle anderen WPs. Quelle: DWD CDC (Gebietsmittel Jahres-Lufttemperatur, 1881–2025).

## Was vorliegt
- `klima/data/raw/regional_averages_tm_year.txt` — DWD-Rohdatei (= Abgabe-Datendatei).
- `klima/data/clean/temp_annual_regions.csv` — **gemeinsame Startdatei**, 145 Zeilen × 18 Spalten, 0 NaN, geprüft.
- `klima/klima_analyse.ipynb` — Skelett: Abschnitt 1–2 lauffähig (lädt, putzt, speichert die CSV), Abschnitte 3–8 als Überschriften für die WPs.
- Ordner `data/raw`, `data/clean`, `figures` angelegt.

Verifiziert (Block 1.4): Shape (145,18), Jahre 1881–2025, 0 fehlende Werte, DE-Mittel 8,44 °C, wärmstes Jahr **2024 = 10,89 °C**, 2025 kühler (10,03 °C).

## Modularisierungs-Vertrag (für alle)
1. **Jede/r startet von `data/clean/temp_annual_regions.csv`** — nicht von der Rohdatei.
2. Eigenes Scratch-Notebook pro Person. `klima_analyse.ipynb` **nicht gleichzeitig** editieren — eine Person merged am Ende.
3. Einstieg (eine Zelle):
   ```python
   import pandas as pd
   df = pd.read_csv("data/clean/temp_annual_regions.csv")
   de = df[["jahr", "Deutschland"]].copy()
   ```

## Aufgabenverteilung (Code-Vorlagen in `projekt_schritte.md`)
- **D1** Zeitreihe + Dekaden → Fig 1+2 (Block 2)
- **D2** Erwärmung je Bundesland → Fig 5 (Block 3)
- **I1** Regression Temp~Jahr, 95%-CI, pre/post-1980 → Fig 3 (Block 4)
- **I2** Bootstrap-CI + Welch-t + Cohen's d → Fig 4 (Block 5)

17 Regionsspalten (inkl. Kombis wie Brandenburg/Berlin) + `jahr`. 16 echte Länder-Aggregate + Deutschland.

## Fakten fürs Treffen
DE +~1,9 °C (frühe vs. letzte Dekade) · Erwärmung seit ~1980 deutlich beschleunigt · alle Regionen erwärmt, Spread klein → nationales Phänomen.
