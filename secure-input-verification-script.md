# Skrypt weryfikacji dostępu (Input Validation)
**Data:** 2026-05-05  
**Kategoria:** Bash Scripting / Security Fundamentals  

## 1. Cel (Goal)
Celem zadania było stworzenie skryptu automatyzującego proces autoryzacji skrytki bankowej użytkownika.
Skrypt musi zebrać trzy parametry wejściowe i przyznać dostęp tylko w przypadku pełnej zgodności z bazą (hardcoded credentials).

## 2. Metoda (Method)
Skrypt wykorzystuje strukturę kontrolną if-elif-else wewnątrz pętli for do interaktywnego pobierania danych. 
Kluczowym elementem jest walidacja logiczna przy użyciu operatorów koniunkcji.

### Kod źródłowy:
#!/bin/bash

# Zmienne
username=""
companyname=""
pin=""

# 1. ZRODLO (Input): Petla zbierajaca dane od uzytkownika
for i in {1..3}; do
    if [ "$i" -eq 1 ]; then 
        echo "Enter your Username:"
        read username
    elif [ "$i" -eq 2 ]; then
        echo "Enter your Company name:"
        read companyname
    else
        echo "Enter your PIN:"
        read pin
    fi
done

# 2. Logika: Weryfikacja danych (Boolean Logic)
if [ "$username" = "John" ] && [ "$companyname" = "Tryhackme" ] && [ "$pin" = "7385" ]; then
    echo "Authentication Successful. You can now access your locker, John."
else
    echo "Authentication Denied!!"
fi

## 3. Czego się nauczyłem (Key Takeaways)
1. **Matematyczna precyzja składni:** Bash wymaga spacji wewnątrz nawiasów kwadratowych `[ ]`.
2. Każdy warunek musi być odizolowany, aby został poprawnie zinterpretowany. Brak spacji to był mój błąd na początku.
3. **Logika koniunkcji (&&):** Zastosowanie operatora AND realizuje zasadę Zero Trust.
4. Każdy z trzech warunków musi być prawdziwy ($1 \land 1 \land 1 = 1$), aby system przepuścił użytkownika.
5. **Automatyzacja przepływu:** Użycie pętli `for` do sekwencyjnego zadawania pytań optymalizuje kod i czyni go bardziej czytelnym niż powtarzanie komendy `read`.
6. **Zarządzanie uprawnieniami:** Praca w terminalu wymaga zrozumienia systemu uprawnień (`chmod +x`), bez których skrypt nie zostanie uruchomiony przez system.

## 4. Dowód działania:
Skrypt przetestowany pomyślnie w środowisku Linux. Wynik pozytywny dla poświadczeń: John, Tryhackme, 7385.

<img width="1352" height="338" alt="Opera Snapshot_2026-05-05_131603_tryhackme com" src="https://github.com/user-attachments/assets/f5194939-e4c5-450b-acb0-9f937e55e318" />
<img width="1976" height="1594" alt="Opera Snapshot_2026-05-05_131457_tryhackme com" src="https://github.com/user-attachments/assets/53afffaa-4a41-4b4c-9331-3643aa9bcfb8" />


## 5. Wniosek
Skrypt skutecznie realizuje podstawową walidację.
W ramach rozwoju projektu warto rozważyć dodanie funkcji blokowania konta po 3 nieudanych próbach (ochrona przed Brute-force),
czym chcę się posłużyć w przyszłości.













