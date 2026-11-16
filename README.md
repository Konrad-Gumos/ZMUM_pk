# ZMUM_pk – predykcja rzeczywistego zużycia paliwa (OBFCM 2024)

Projekt z przedmiotu Zaawansowane Metody Uczenia Maszynowego. Regresja rzeczywistego zużycia paliwa
[l/100 km] samochodów spalinowych i hybryd (dane OBFCM, EEA, okres raportowy 2024).

## Dane
Plik `2024_Cars_Raw.csv` (~2 GB, nie jest w repozytorium) należy pobrać z:
https://sdi.eea.europa.eu/data/13e6fad9-149c-4b86-9d83-cdf3569ccfee?path=%2F
i umieścić w katalogu głównym repozytorium.

## Środowisko
Python 3.14, pakiety w `requirements.txt`. Zalecane ok. 16 GB RAM (pełny zbiór ma 7,7 mln wierszy po filtracji).

```bash
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
```

## Uruchomienie
```bash
jupyter nbconvert --to notebook --execute --inplace --ExecutePreprocessor.timeout=-1 Opis_Danych.ipynb
```
Pełny przebieg trwa kilkadziesiąt minut. Do szybkiego testu kodu można ograniczyć liczbę wczytywanych
wierszy zmienną środowiskową `ZMUM_NROWS` (np. `ZMUM_NROWS=800000`) – wyniki nie są wtedy reprezentatywne.

## Struktura
- `Opis_Danych.ipynb` – cały proces: czyszczenie, podział grupowy, EDA, imputacja, skalowanie, modele bazowe.
- `splits/split_seed42.csv.gz` – utrwalony podział (identyfikator pojazdu → train/val/test).
- `results/` – tabele wyników (CSV) i `results.json` z liczbami użytymi w raporcie.
- `raport/` – raport LaTeX (`main.tex`, `bibliography.bib`, `figures/`).
