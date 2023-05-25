---
title: 5. Typy
layout: post
---

`sum` z wartością 99 to zmienna typu liczbowego \(**number**\). Oprócz liczb JS korzysta też z innych typów danych:

**string** - ciąg znaków. Są zapisywane w cudzysłowiu lub apostrofach, np. 'Programiści JS są super'

**zmienna typu logicznego \(boolean\) **- true \(logiczna prawda\) lub false \(logiczny fałsz\)

**null **- czyli pusty obiekt

**undefined **- wartość niezdefiniowana

Jak sprawdzić typ zmiennej? Służy do tego instrukcja `typeof`, np. `typeof sum`

Spróbuj teraz stworzyć zmienną ze swoim imieniem. W konsoli wpisz `let name = "tu podaj swoje imię";` Następnie napisz `console.log(name);`. Powinnaś zobaczyć swoje imię w konsoli. Sprawdź jakiego typu jest Twoja zmienna `name` przez wpisanie w konsoli `console.log(typeof name);`

### Liczby i operatory

Na liczbach możemy wykonywać działania matematyczne. Służą nam do tego operatory przedstawione w poniższej tabelce.

Załóżmy, że mamy następujące zmienne: 

```js
let y = 8;

let z = 4;

```

|  | Operator | Równanie | Wynik |
| :--- | :--- | :--- | :--- |
| + | Dodawanie | x = y + z | x = 12 |
| - | Odejmowanie | x = y - z | x = 4 |
| \* | Mnożenie | x = y \* z | x = 32 |
| / | Dzielenie | x = y / z | x = 2 |
| % | Reszta z dzielenia | x = y % 3 | x = 2 |
| ++ | Inkrementacja | x = ++y | x = 9 |
|  |  | x = y++ | x=8; y = 9; |
| -- | Dekrementacja | x = --y | x = 7 |
|  |  | x = y-- | x = 8; y = 7 |

Spróbuj teraz zapisać kilka takich działań w konsoli. Najpierw stwórz dwie dowolne zmienne liczbowe, a potem wypisz przy pomocy `console.log` w konsoli wyniki działań.

### Stringi

**Na stringach również można robić pewne operacje. Możemy je do siebie dodawać \(nazywa się to konkatenacja\).**

```js
let text_1 = "Hello";
let text_2 = "Jack";
let text3 = text_1 + ', ' + text_2 + '!'; // Hello, Jack!
```

Stwórz zmienną `surname` i przypisz do niej swoje nazwisko. Następne zdefiniuj kolejną zmienną o nazwie `fullName` i spraw, by jej wartością były Twoje dwie wcześniejsze zmienne, czyli imię i nazwisko. Wypisz wartość zmiennej `fullName` w konsoli.

**Do sprawdzenia długości tekstu służy właściwość **`length`

```js
text_3.length; // 12
```

Sprawdź, wypisując w konsoli, jaka jest długość trzech Twoich zmiennych tekstowych \(`name`, `surname`, `fullName`\).

**Możemy też zmienić znaki w tekście na duże lub małe:**

```js
text_3.toUpperCase(); // HELLO, JACK!
text_3.toLowerCase(); // hello, jack!
```

Spraw, aby Twoje imię w zmiennej `name` było napisane wielkimi literami.

**Kolejną metodą jest sprawdzanie pozycji podtekstu:**

```js
text_3.indexOf('Jack'); // 7
```

Sprawdź, jaką pozycję zajmuje w Twoim imieniu literka 'a'.

**Możemy również zamienić fragmenty tekstu:**

```js
text_3.replace('Jack', 'Mary');
```

W ten sposób zastąpimy pierwsze wystąpienie danego ciągu znaków \(w naszym przypadku 'Jack'\) nowym stringiem \('Mary'\).

### Zadanie

Stwórz zmienną `hello` i przypisz do niej następujący tekst: "Hello, \[tu podaj swoje imię\]!". Następnie, korzystając z metody `replace`, spraw, aby tekst wyglądał tak: "Hello, JavaScript!".

