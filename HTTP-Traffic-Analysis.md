# HTTP Traffic Analysis

Analiza ruchu sieciowego w celu detekcji anomalii, takich jak nietypowe porty, nagłe skoki transferu danych czy podejrzane kierunki połączeń (np. kraje wysokiego ryzyka).

## 1. Problem (Input)
Wykrycie nieautoryzowanej ekstrakcji danych (**data exfiltration**) oraz identyfikacja anomalii w nagłówkach protokołu HTTP.

## 2. Metoda
* **Narzędzie:** Wireshark.
* **Filtrowanie:** Zastosowanie filtra `http` w celu izolacji ruchu warstwy aplikacji.
* **Analiza Strumienia:** Wykorzystanie funkcji `Follow HTTP Stream` do pełnej rekonstrukcji sesji klient-serwer.
* **Weryfikacja Błędów:** Użycie `Expert Info` do namierzenia anomalii strukturalnych w pakietach i nagłówkach.

## 3. Dowód
* **Wykryto:** Przesyłanie wrażliwych danych (lista 3 rekordów: artyści) w otwartym tekście (**Cleartext**).
* **Anomalie:** Potwierdzono błędy w nagłówkach HTTP, sugerujące niestandardowe zachowanie aplikacji lub błędną konfigurację serwera.
* **Wniosek:** Brak szyfrowania TLS umożliwia pasywny podsłuch i kradzież danych.
