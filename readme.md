# Analiza Ekonometryczna PKB Indii w latach 1983-2020

## 📝 Opis Projektu
[cite_start]Celem projektu było zbudowanie i zweryfikowanie modelu ekonometrycznego objaśniającego kształtowanie się Produktu Krajowego Brutto (PKB) Indii[cite: 1, 2]. [cite_start]Badanie obejmuje pełen proces diagnostyczny — od selekcji zmiennych, przez weryfikację założeń Klasycznej Metody Najmniejszych Kwadratów (KMNK), aż po zastosowanie Uogólnionej Metody Najmniejszych Kwadratów (UMNK) w celu wyeliminowania autokorelacji[cite: 23, 117].

## 📊 Dane
[cite_start]Dane zostały zaczerpnięte z serwisu Kaggle i dotyczą gospodarki Indii[cite: 9, 10].
* [cite_start]**Zmienna zależna (Y):** Logarytm naturalny PKB Indii (ygdplg)[cite: 6, 42].
* **Zmienne objaśniające (finalne):**
    * [cite_start]**X1:** Liczba zgłoszeń patentowych (tys. sztuk)[cite: 6].
    * [cite_start]**X2:** Damska populacja (wiek 5-9 lat) [%][cite: 6].
    * [cite_start]**X5:** Import towarów i usług (% PKB)[cite: 6].
    * [cite_start]**X6:** Eksport towarów i usług (% PKB)[cite: 6].

## ⚙️ Metodologia i Diagnostyka
W procesie modelowania wykonano następujące kroki badawcze:

1. [cite_start]**Selekcja zmiennych:** Wyeliminowano zmienną quasi-stałą X11 (oczekiwana długość życia), ponieważ jej współczynnik zmienności był niższy od założonego progu $V^* = 0,1$[cite: 16, 17, 19].
2. [cite_start]**Weryfikacja istotności:** Wszystkie zmienne w modelu końcowym okazały się istotne statystycznie (wartość-p < 0,05)[cite: 24, 45, 52].
3. **Testy diagnostyczne:**
    * [cite_start]**Normalność:** Test Jarque-Bera wykazał, że składnik losowy ma rozkład normalny ($JB < \chi^2$)[cite: 97, 100, 101].
    * [cite_start]**Homoskedastyczność:** Test White'a oraz test Goldfelda-Quandta potwierdziły stałość wariancji składnika losowego (brak podstaw do odrzucenia $H_0$)[cite: 151, 165, 171, 354].
    * [cite_start]**Autokorelacja:** Test Durbina-Watsona ($D = 1,10446$) wykazał obecność autokorelacji dodatniej pierwszego rzędu ($d < dL$)[cite: 112, 115].
    * [cite_start]**Współliniowość:** Stwierdzono występowanie wysokiej współliniowości ($VIF = 27,88$), co może wpływać na stabilność estymatorów[cite: 35, 37].
    * [cite_start]**Losowość:** Test serii potwierdził poprawną specyfikację postaci modelu oraz losowość składnika $\epsilon$[cite: 72, 91, 92].

## 📈 Modele Estymacji
W projekcie porównano dwa podejścia:

### [cite_start]Model KMNK [cite: 42, 372, 373]
$$\hat{y} = 32,12 + 0,0194x_1 - 0,153x_2 + 0,029x_5 - 0,034x_6$$
* [cite_start]**R-kwadrat:** 0,9943 (model wyjaśnia ok. 99% zmienności PKB)[cite: 24, 64, 65].
* [cite_start]**Błąd standardowy reszt:** 0,07049[cite: 24, 61].

### [cite_start]Model UMNK (Cochrane-Orcutt) [cite: 118, 374]
[cite_start]Ze względu na wykrytą autokorelację, zastosowano metodę Cochrane-Orcutt ($\rho = 0,446$), aby uzyskać estymatory nieobciążone i efektywne[cite: 117, 120, 400].
$$\hat{y} = 32,34 + 0,0179x_1 - 0,158x_2 + 0,033x_5 - 0,040x_6$$

## [cite_start]💡 Główne Wnioski [cite: 361]
* [cite_start]**Innowacje (X1):** Każdy dodatkowy tysiąc patentów zwiększa PKB, co świadczy o wzroście produktywności i innowacyjności[cite: 378, 379].
* [cite_start]**Demografia (X2):** Zmiany w strukturze populacji kobiet mają istotny wpływ na wzrost gospodarczy[cite: 382].
* [cite_start]**Handel (X5, X6):** Zarówno eksport, jak i import są kluczowymi determinantami aktywności gospodarczej Indii[cite: 384, 386].

---
[cite_start]**Autor:** Kacper Grzeszyk [cite: 3]
[cite_start]**Narzędzie:** Projekt przygotowany w programie Gretl[cite: 152].