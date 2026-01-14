# Analiza Ekonometryczna PKB Indii w latach 1983-2020

## 📝 Opis Projektu
Celem projektu było zbudowanie i zweryfikowanie modelu ekonometrycznego objaśniającego kształtowanie się Produktu Krajowego Brutto (PKB) Indii. Badanie obejmuje pełen proces diagnostyczny — od selekcji zmiennych, przez weryfikację założeń Klasycznej Metody Najmniejszych Kwadratów (KMNK), aż po zastosowanie Uogólnionej Metody Najmniejszych Kwadratów (UMNK) w celu wyeliminowania autokorelacji.

## 📊 Dane
Dane zostały zaczerpnięte z serwisu Kaggle i dotyczą gospodarki Indii.

* **Zmienna zależna (Y):** Logarytm naturalny PKB Indii (ygdplg).
* **Zmienne objaśniające (finalne):**
    * **X1:** Liczba zgłoszeń patentowych (tys. sztuk).
    * **X2:** Damska populacja (wiek 5-9 lat) [%].
    * **X5:** Import towarów i usług (% PKB).
    * **X6:** Eksport towarów i usług (% PKB).

## ⚙️ Metodologia i Diagnostyka
W procesie modelowania wykonano następujące kroki badawcze:

1. **Selekcja zmiennych:** Wyeliminowano zmienną quasi-stałą X11 (oczekiwana długość życia), ponieważ jej współczynnik zmienności był niższy od założonego progu V* = 0,1.
2. **Weryfikacja istotności:** Wszystkie zmienne w modelu końcowym okazały się istotne statystycznie (wartość-p < 0,05).
3. **Testy diagnostyczne:**
    * **Normalność:** Test Jarque-Bera wykazał, że składnik losowy ma rozkład normalny.
    * **Homoskedastyczność:** Test White'a oraz test Goldfelda-Quandta potwierdziły stałość wariancji składnika losowego.
    * **Autokorelacja:** Test Durbina-Watsona wykazał obecność autokorelacji dodatniej pierwszego rzędu (d < dL).
    * **Współliniowość:** Stwierdzono występowanie wysokiej współliniowości (VIF > 10).
    * **Losowość:** Test serii potwierdził poprawną specyfikację postaci modelu.

## 📈 Modele Estymacji

### Model KMNK
y = 32,12 + 0,0194*X1 - 0,153*X2 + 0,029*X5 - 0,034*X6
* **R-kwadrat:** 0,9943 (model wyjaśnia 99% zmienności PKB).
* **Błąd standardowy reszt:** 0,07049.

### Model UMNK (Cochrane-Orcutt)
Ze względu na wykrytą autokorelację, zastosowano metodę Cochrane-Orcutt, aby uzyskać estymatory nieobciążone i efektywne.
y = 32,34 + 0,0179*X1 - 0,158*X2 + 0,033*X5 - 0,040*X6

## 💡 Główne Wnioski
* **Innowacje (X1):** Każdy dodatkowy tysiąc patentów zwiększa PKB, co świadczy o wzroście produktywności i innowacyjności.
* **Demografia (X2):** Zmiany w strukturze populacji kobiet mają istotny wpływ na wzrost gospodarczy.
* **Handel (X5, X6):** Zarówno eksport, jak i import są kluczowymi determinantami aktywności gospodarczej Indii.

---
**Autor:** Kacper Grzeszyk  
**Narzędzie:** Projekt przygotowany w programie Gretl,Excel.
