# System aukcyjny

## Wprowadzenie

Specyfikacja wymagań funkcjonalnych w ramach informatyzacji procesu sprzedaży produktów w oparciu o mechanizm aukcyjny. 

## Procesy biznesowe

---
<a id="bc1"></a>
### BC1: Sprzedaż aukcyjna 

**Aktorzy:** [Sprzedający](#ac1), [Kupujący](#ac2)

**Opis:** Proces biznesowy opisujący sprzedaż za pomocą mechanizmu aukcyjnego. |

**Scenariusz główny:**
1. [Sprzedający](#ac1) wystawia produkt na aukcję. ([UC1](#uc1))
2. [Kupujący](#ac2) oferuje kwotę za produkt wyższą od aktualnie najwyższej oferty. ([UC2](#uc2)) ([BR1](#br1))
3. [Kupujący](#ac2) wygrywa aukcję. ([BR2](#br2)) ([UC2](#uc2))
4. [Kupujący](#ac2) przekazuje należność Sprzedającemu. ([UC5](#uc5)) ([UC6](#uc6))
5. [Sprzedający](#ac1) przekazuje produkt Kupującemu. ([UC7](#uc7)) ([UC8](#uc8))

**Scenariusze alternatywne:** 

2.A. Oferta Kupującego została przebita, a [Kupujący](#ac2) pragnie przebić aktualnie najwyższą ofertę.
* 2.A.1. Przejdź do kroku 2.

3.A. Czas aukcji upłynął i [Kupujący](#ac2) przegrał aukcję. ([BR2](#br2))
* 3.A.1. Koniec przypadku użycia.

---

## Aktorzy

<a id="ac1"></a>
### AC1: Sprzedający

Osoba oferująca towar na aukcji.

<a id="ac2"></a>
### AC2: Kupujący

Osoba chcąca zakupić produkt na aukcji.


## Przypadki użycia poziomu użytkownika

### Aktorzy i ich cele

[Sprzedający](#ac1):
* [UC1](#uc1): Wystawienie produktu na aukcję
* [UC4](#uc4): Sprawdzenie wyniku aukcji przez [Sprzedającego](#ac1)
* [UC6](#uc6): Odebranie pieniędzy po zakończonej aukcji od [Kupującego](#ac2)
* [UC7](#uc7): Wysłanie produktu [Kupującemu](#ac2)
* [UC9](#uc9): Edycja danych aukcji i produktu przez [Sprzedającego](#ac1)
* [UC10](#uc10): Anulowanie aukcji przez [Sprzedającego](#ac1)
* [UC11](#uc11): Przeglądanie własnych aukcji przez [Sprzedającego](#ac1)

[Kupujący](#ac2):
* [UC2](#uc2): Złożenie własnej oferty
* [UC3](#uc3): Sprawdzenie wyniku aukcji przez [Kupującego](#ac2)
* [UC5](#uc5): Przesłanie pieniędzy po wygranej aukcji [Sprzedającemu](#ac1)
* [UC8](#uc8): Odebranie produktu
* [UC12](#uc12): Przeglądanie i wyszukiwanie aukcji przez [Kupującego](#ac2)
* [UC13](#uc13): Przeglądanie historii ofert w aukcji

---
<a id="uc1"></a>
### UC1: Wystawienie produktu na aukcję

**Aktorzy:** [Sprzedający](#ac1)

**Scenariusz główny:**
1. [Sprzedający](#ac1) zgłasza do systemu chęć wystawienia produktu na aukcję.
2. System prosi o podanie danych produktu i ceny wywoławczej.
3. [Sprzedający](#ac1) podaje dane produktu oraz cenę wywoławczą.
4. System weryfikuje poprawność danych.
5. System informuje o pomyślnym wystawieniu produktu na aukcję.

**Scenariusze alternatywne:** 

4.A. Podano niepoprawne lub niekompletne dane produktu.
* 4.A.1. System informuje o błędnie podanych danych.
* 4.A.2. Przejdź do kroku 2.

---

<a id="uc2"></a>
### UC2: Złożenie własnej oferty

**Aktorzy:** [Kupujący](#ac2)

**Scenariusz główny:**
1. [Kupujący](#ac2) zgłasza do systemu chęć złożenia własnej oferty.
2. System prosi o podanie wartości.
3. [Kupujący](#ac2) podaje wartość oferty.
4. System weryfikuje poprawność danych.
5. Jeśli wartość oferty była wyższa niż aktualna najwyższa oferta, [Kupujacy](#ac2) przebija aukcję. 

**Scenariusze alternatywne:** 

4.A. Podano niepoprawną wartość oferty.
* 4.A.1. System informuje o błędnie podanych danych.
* 4.A.2. Przejdź do kroku 2.

---

<a id="uc3"></a>
### UC3: Sprawdzenie wyniku aukcji przez [Kupującego](#ac2)

**Aktorzy:** [Kupujący](#ac2)

**Scenariusz główny:**
1. [Kupujący](#ac2) zgłasza do systemu chęć sprawdzenia wyniku aukcji.
2. System informuje [Kupującego](#ac2) o wygraniu aukcji.

**Scenariusze alternatywne:** 

2.A. Aukcja [Kupującego](#ac2) została przebita.
* 2.A.1. System informuje [Kupującego](#ac2) o przegranej aukcji.

---

<a id="uc4"></a>
### UC4: Sprawdzenie wyniku aukcji przez [Sprzedającego](#ac1)

**Aktorzy:** [Sprzedający](#ac1)

**Scenariusz główny:**
1. [Sprzedający](#ac1) zgłasza do systemu chęć sprawdzenia wyniku aukcji.
2. System informuje [Sprzedającego](#ac1) o zakupie produktu.

**Scenariusze alternatywne:** 

1.A. Nie złożono żadnej oferty kupna.
* 1.A.1. System informuje [Sprzedającego](#ac1) o braku ofert kupna produktu. 

---
## Obiekty biznesowe (inaczje obiekty dziedzinowe lub informatycjne)

### BO1: Aukcja

Aukcja jest formą zawierania transakcji kupna-sprzedaży, w której Sprzedający określa cenę wywoławczą produktu, natomiast Kupujący mogą oferować własną ofertę zakupu każdorazowo proponując kwotę wyższą od aktualnie oferowanej kwoty. Aukcja kończy się po upływie określonego czasu. Jeśli złożona została co najmniej jedna oferta zakupy produkt nabywa ten Kupujący, który zaproponował najwyższą kwotę. 

### BO2: Produkt

Fizyczny lub cyfrowy obiekt, który ma zostać sprzedany w ramach aukcji.

### BO3: Oferta

Kwota zaproponowana przez Kupującego w ramach danej aukcji.

### BO4: Płatność

Przekazanie należności za wygraną aukcję od Kupującego do Sprzedającego.

### BO5: Przesyłka

Przekazanie sprzedanego produktu od Sprzedającego do Kupującego.

## Reguły biznesowe

<a id="br1"></a>
### BR1: Złożenie oferty

Złożenie oferty wymaga zaproponowania kwoty wyższej niż aktualnie oferowana o minimum 1,00 PLN.


<a id="br2"></a>
### BR2: Rozstrzygnięcie aukcji

Aukcję wygrywa ten z [Kupujący](#ac2)ch, który w momencie jej zakończenia (upłynięcia czasu) złożył najwyższą ofertę.

## Macierz CRUDL

| Przypadek użycia                                                          | Aukcja | Produkt | Oferta | Płatność | Przesyłka |
| ------------------------------------------------------------------------- | ------ | ------- | ------ | -------- | --------- |
| UC1: Wystawienie produktu na aukcję                                       | C      | C       |        |          |           |
| UC2: Złożenie własnej oferty                                              | R, U   |         | C      |          |           |
| UC3: Sprawdzenie wyniku aukcji przez [Kupującego](#ac2)                   | R      |         | R      |          |           |
| UC4: Sprawdzenie wyniku aukcji przez [Sprzedającego](#ac1)                | R      | R       | R      |          |           |
| UC5: Przesłanie pieniędzy po wygranej aukcji [Sprzedającemu](#ac1)        | R      |         | R      | C        |           |
| UC6: Odebranie pieniędzy po zakończonej aukcji od [Kupującego](#ac2)      | R      |         |        | R, U     |           |
| UC7: Wysłanie produktu [Kupującemu](#ac2)                                 | R      | R       |        | R        | C         |
| UC8: Odebranie produktu                                                   | R      | R       |        |          | R, U      |
| UC9: Edycja danych aukcji i produktu przez [Sprzedającego](#ac1)          | R, U   | R, U    |        |          |           |
| UC10: Anulowanie aukcji przez [Sprzedającego](#ac1)                       | R, D   |         |        |          |           |
| UC11: Przeglądanie własnych aukcji przez [Sprzedającego](#ac1)            | L      | L       |        |          |           |
| UC12: Przeglądanie i wyszukiwanie aukcji przez [Kupującego](#ac2)         | L, R   | R       |        |          |           |
| UC13: Przeglądanie historii ofert w aukcji                                | R      |         | L      |          |           |