# Wynik kontrolny: agent zleceń transportowych

Liczby poniżej policzono niezależnie z plików w katalogu `dane-cwiczeniowe/`. Jeśli agent oddaje inne wartości, procedura nie działa poprawnie w Waszym narzędziu.

## Sprawdź wynik na danych kontrolnych

Porównaj odpowiedź z tabelami poniżej. Liczby policzyliśmy niezależnie z tych samych plików.

| Płatnik: Chłodnie Wielkopolskie (T-0310) | Wartość |
|---|---|
| Limit kredytowy | 150 000,00 zł |
| Saldo należności | 142 000,00 zł, w tym przeterminowane 9 800,00 zł (najstarsza zaległość 12 dni) |
| Zlecenie w PLN | 1 980 EUR × 4,30 = 8 514,00 zł |
| Saldo po zleceniu | 150 514,00 zł — przekroczenie limitu o 514,00 zł |
| Termin płatności | żądany 60 dni; umowny 45; maksymalny bez zgody zarządu 45 |

| Marża: Poznań → Lyon (chłodnia) | Wartość |
|---|---|
| Przychód | 8 514,00 zł |
| Koszt trasy | 7 620,00 zł (w tym paliwo 3 350, opłaty drogowe 1 180, kierowca 2 140) |
| Marża | 894,00 zł, czyli 10,5% — poniżej progu 12% |
| Stawka minimalna dla 12% | 2 020 EUR |
| Wariant z podwykonawcą (średnio 1 850 EUR) | koszt 7 955,00 zł, marża 559,00 zł |

| Auto | Status | Dlaczego |
|---|---|---|
| PO 1234K, chłodnia | pasuje | we Wrocławiu, wolne od 21.09 18:00, 31 h czasu pracy; dojazd ok. 160 km na załadunek 22.09 rano |
| PO 9012M, plandeka | odpada | bez agregatu, nie nadaje się do 2–8 °C |
| PO 3456N, chłodnia | odpada | zajęta do 23.09, nie zdąży na załadunek 22.09 |
| PO 5678L, chłodnia | nie zdąży na załadunek | stoi w Lyonie i szuka powrotu — pomysł dla planisty: zamiana ról, PO 5678L bierze powrót z Francji, a PO 1234K jedzie do Lyonu |

Prawidłowa rekomendacja to **„przyjąć pod warunkami”**: stawka minimum 2 020 EUR, żeby marża osiągnęła 12%, albo akceptacja 10,5% przez kierownika spedycji; termin płatności 45 dni, bo 60 wymaga zgody zarządu; płatnik po zleceniu przekracza limit o 514 zł i ma 9 800 zł przeterminowane od 12 dni, więc zwolnienie należy do finansów; palety EUR 1:1 i rejestrator temperatury do potwierdzenia dyspozytorowi. W brakach agent powinien wskazać termin odpowiedzi (19.09, godz. 15:00), cztery wolne godziny postoju na każdym miejscu do porównania z Waszą umową ramową oraz temperaturę 2–8 °C przy ładunku opisanym jako mrożonki — to pytanie do klienta, nie założenie.

Jeśli w tabeli marży pojawi się relacja do Mediolanu albo Berlina, agent nie trzymał się reguły doboru relacji. Jeśli saldo po zleceniu albo marża się nie zgadzają, sprawdź, czy rzeczywiście liczył kodem i czy wziął kurs z pliku parametrów.

## Krok z rzeczywistością

Dane w firmie się zmieniają, a agent musi to zauważyć bez zmiany instrukcji. Otwórz `parametry.xlsx`, zmień kurs EUR/PLN do kalkulacji z `4,30` na `4,40`, zapisz plik i podmień go w wiedzy projektu.

Zadaj w nowej rozmowie to samo pytanie. Przychód powinien wzrosnąć do **8 712,00 zł**, marża do **1 092,00 zł, czyli 12,5%** — próg 12% jest teraz spełniony, a stawka minimalna spada do **1 970 EUR**. Wariant z podwykonawcą daje 572,00 zł marży. Saldo płatnika po zleceniu rośnie do 150 712,00 zł, więc przekroczenie limitu rośnie do 712,00 zł. W rekomendacji warunek stawki powinien zniknąć, a warunek limitu i terminu płatności zostać.

Jedna liczba w jednym pliku przesunęła marżę z „poniżej progu” na „w progu” i jednocześnie pogorszyła sytuację płatnika. Właśnie dlatego kurs do kalkulacji ma być parametrem firmy ustawianym przez kontroling, a nie liczbą z głowy spedytora.
