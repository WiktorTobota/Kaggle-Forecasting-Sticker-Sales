# Prognozowanie sprzedaży naklejek – Tabular Playground Series 2025

Repozytorium zawiera pipeline rozwiązania wyzwania [Kaggle Tabular Playground Series 2025]([https://www.kaggle.com/](https://www.kaggle.com/competitions/playground-series-s5e1/overview)), którego celem jest przewidywanie dziennej sprzedaży naklejek (`num_sold`) w różnych krajach, sklepach i dla różnych produktów. Metryką oceny jest **Mean Absolute Percentage Error (MAPE)**.

## Cel projektu
Zminimalizować wartość MAPE w prognozie liczby sprzedanych naklejek, wykorzystując odpowiednie przetwarzanie danych i modele predykcyjne.

---

## Dane
- **Wejściowe pliki:**
  - `train.csv` – dane treningowe z brakami w zmiennej docelowej (`num_sold`).
  - `test.csv` – dane testowe bez wartości docelowej.
- **Wyjściowy plik:**
  - `predictions.csv` – plik wynikowy z kolumnami `id` oraz przewidywanymi wartościami `num_sold`.

---

## Pipeline rozwiązania

1. **Wstępna obróbka danych**
   - Obsłużono braki w kolumnie `num_sold` poprzez:
     - Wstępne wytrenowanie modelu do predykcji brakujących wartości.
     - Uzupełnienie braków w danych treningowych.

2. **Inżynieria cech**
   - Rozbicie kolumny `date` na:
     - `year` (rok),
     - `month` (miesiąc),
     - `day` (dzień).
   - Przygotowanie danych do wejścia dla modeli predykcyjnych.

3. **Modelowanie**
   - Porównano wydajność następujących modeli:
     - **LinearRegression**
     - **RandomForestRegressor**
     - **XGBRegressor**
   - Zastosowano krzyżową walidację (5-fold) i oceniono modele na podstawie metryki MAPE.

4. **Wybór najlepszego modelu**
   - Wybrano model z najniższym błędem MAPE.
   - Ponownie wytrenowano go na pełnym zbiorze danych treningowych.

5. **Predykcja i zapis wyników**
   - Na podstawie najlepszego modelu wygenerowano prognozy dla danych testowych.
   - Wyniki zapisano w pliku `predictions.csv`.

---
## Wyniki
1. **Predykcje**: Zapisane w pliku predictions.csv.
2. **Ocena**:
   -Model 1: XGBoost: 0.15283456747451746
   -Model 2: Random Forest: 0.14696988698255328
3. **Wynik na platformie Kaggle**: 0.16846
