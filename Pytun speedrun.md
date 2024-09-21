### 1 - Podstawowe informacje 
1. Python jest językiem interpretowanym 
2. Python jest wysoko-poziomowy, przez co nie pozwala kontrolować pamięci z pomocą pointerów bądź innych narzędzi.

### 2 - Zmienne
Zmienna to określone miejsce w pamięci zarezerwowane dla danej wartości. Prościej mówiąc - Coś co trzyma jakąś wartość.

**Przykład**
```python
zmienna1 = 10
zmienna2 = "jakis tekst"
```

#### Przypisanie wielu zmiennych za jednym razem
```python
zmienna1, zmienna2 = 3,4, True
```
#### Nazewnictwo zmiennych 
Zmienne najlepiej nazywać opisowo, np. `nazwa_uzytkownika`, `baza` etc. jednak nie można nazywać ich słowami zarezerwowanymi dla języka:

![[Pasted image 20240921010207.png]]

Zwykle wyrzuci to błąd jednak czasami, możemy przez przypadek nadpisać jakąś funkcję, np. tak:
```python
print = 1
```
Nie wyrzuci to błędu, jednak może stanowić problemy w przyszłości.

#### Typy danych
| Typ       | Wartość                                                      | Przykład wartości   |
| --------- | ------------------------------------------------------------ | ------------------- |
| `int`     | Liczba bez przecinka                                         | `10`. `-4`          |
| `float`   | Liczba z przecinkiem (ważne, aby przecinek deklarować kropką) | `43.4`, `-3.543`    |
| `boolean` | Wartość `True`, `False` (1,0)                                | `True`, `False`     |
| `string`  | Po prostu tekst                                              | `"dfas"`, `"FDAS1"` |
#### Operacje na zmiennych 
Zmiennym możemy przypisywać wartości innych zmiennych:
```python
zmienna1 = 4 
zmienna2 = zmienna1
```

Kompletnie nadać jej inną wartość:
```python 
zmienna1 = 2
zmienna2 = 5
```

Dodawać je ze sobą bądź prowadzić na nich inne operacje arytmetyczne (dotyczy tylko i wyłącznie typów liczbowych):
```python
zmienna1 = 2 
zmienna2 =  5
zmienna3 = zmienna1 + zmienna2
zmienna4 = zmienna1 / zmienna2 
```
#### Konkatenacja stringów
Skomplikowane słowo na dodawania ze sobą Stringów
```python
zdanie1 = "abc"
zdanie2 = "def"
zdanie3 = zdanie1 + zdanie2
zdanie3 = zdanie1 + "  chuj " + zdanie2
```
#### Czy **string** tak naprawdę jest typem danych?
W języku C - w którym głównie jest napisany interpreter Pythona, nie ma dedykowanego typu danych dla tekstu. String jest określany z pomocą *Array* (z ang. *Szyk*, Podstawowa struktura danych, pozwala na sklejenie wielu wartości o tym samym typie danych z użyciem jednej zmiennej).

```c
#include <stdio.h>

int main(void){
  char zmienna1[] = "sbc";
  return 0;
}
```

Python, pomimo że ma osobny typ danych dla tekstu, zachował nieco funkcjonalności z C, np. możliwość otrzymania znaku pod indeksem z użyciem operatora indeks(`[]`).

```python
zmienna1 = "string1"
print(zmienna1[2])
```

Jednak [Zgodnie z opinią profesjonalisty z StackOverflow](https://stackoverflow.com/questions/77393230/string-data-type-or-data-structure) String jest uważany za typ danych i strukturę danych. 

#### Konwersja typów danych 
Typy danych mogą być konwertowane w zależności od potrzeb, np.
```python
zmienna1 = 1
zmienna2 = float(zmienna1)
zmienna3 = str(zmienna1)
```

Wspierane konwersje:

| a      | b      | Uwagi                       |
| ------ | ------ | --------------------------- |
| int    | float  |                             |
| float  | int    | Ucina wartość po przecinku  |
| int    | string |                             |
| float  | string |                             |
| string | int    | Możliwe z dedykowaną metodą |
| string | float  | Możliwe z dedykowaną metodą |
| bool   | string |                             |
| string | bool   | Możliwe z dedykowaną metodą |

### 3 - Funkcja `print()` i formatowanie 
Funkcja print pozwala na wydrukowanie jakieś wartości do konsoli
np.
```python
print("Hello world!")
```

Również pozwala na drukowanie zmiennych:
```python
zmienna1 = "a
print(zmienna1)
```

I na operacje w funkcji:
```python
zmienna1 = 12
print(zmienna1 + 45)
```

#### fstring
fstring pozwala na łatwiejsze łącznie ze sobą zmiennych, np.
```python
imie = "papaj"
wiek = 34
ruchable = True 
print(f"mam na imie {imie} mam {34} lata i nwm co dalej (ruchable)")
```

Co ciekawe, fstringi można używać w zmiennych:
```python
imie = "papaj"
wiek = 34
ruchable = True 
bimbom = f"mam na imie {imie} mam {34} lata i nwm co dalej (ruchable)"
print(bimbon)
```

#### Metoda `format()`
Metoda `format()` jest bardzo zbliżona do funkcji `printf()` w C, dla przykładu:

```python
#include <stdio.h>

int main(void){
  float zmienna1 = 56.5;
  char* zmienna2 = "chuj ci w dupe";
  int zmienna3 = 2;
  printf("sprzedam %f Opla %s %i", zmienna1, zmienna2, zmienna3);

  return 0;
}
```

Gdzie `%`  oznacza miejsce, do którego ma trafić zmienna, co poprzedza zmienne, które mają zostać wstawione.

Ten sam program, w Python może zostać napisany w ten sposób:
```python 
zmienna1 = 56.5
zmienna2 = ''chuj ci w dupe"
zmienna3 = 2 
print("sprzedam Opla {} {} ".format(zmienna1, zmienna2, zmienna3))
```

Po więcej informacji odsyłam do [dokumentacji](https://docs.python.org/3/library/string.html#formatstrings)

#### Escape sequence
Pozwala na użycie znaków stringach, których normalnie by się nie dało. Najważniejsza: `\n` Nowa linia, przykład:

```python
print("tutaj bedzie nowa linia \n fr fr \n idk")
```

Co ciekawe, w języku C, istnieje coś jak `\a` (alert/buzz). Na starszych komputerach, które to wspierają po użyciu tej flagi rozbrzmiewał brzęczek. 

```c
#include <stdio.h>
int main(void){
  printf("konkuter ci jebnie\a");
  return 0;#28 (02:21:17​) string format 💬
}
```

Takich flag jest dużo, po resztę informacji odsyłam do [Tego artykułu](https://www.geeksforgeeks.org/escape-sequence-in-c/)


### Funkcja ` input()`
Funkcja `input()` pozwala użytkownikowi na wprowadzanie danych, użycie jej wygląda w ten sposób:

```python
ui = input("Podaj swoje imie:  ")
print(f"Witaj! {ui}")
```

Można również na wstępie zdeterminować jaki typ danych ma zostać użyty, nie jest to najlepsza metoda, jednak jak na razie wystarczająca. 

```python
ui = str(input("Podaj swoje imie: "))
```
