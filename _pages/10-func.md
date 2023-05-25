---
title: 10. Funkcje
layout: post
---

Czasami chcemy wykonywać podobne rzeczy dla różnych wartości. Np. chcemy pomalować całe mieszkanie i musimy policzyć powierzchnię ścian dla każdego pokoju. Mamy pokoje o różnych wymiarach, ale samo liczenie będzie wyglądać dokładnie tak samo:

Malujemy pokój o wymiarach 6m x 5m i wysokości 2,5 m.

Sumujemy szerokości ścian: 2\*6 + 2\*5 = 22

Wyliczamy powierzchnię ścian: 22 × 2,5 = 55

Wyliczamy powierzchnię sufitu: 6 × 5 = 30

Dodajemy powierzchnię ścian i sufitu: 55 + 30 = 85

I tak dla 7 różnych pomieszczeń w naszym domu. Ale możemy to skrócić. W końcu chodzi o to by zrobić coś takiego:

```js
let x = jedna_sciana;
let y = druga_sciana;
let z = wysokosc;
let szerScian = 2*x + 2*y;
let powScian = szerScian * wysokosc;
let powSufitu = x * y;
let powmalowania = powScian + powSufitu;
```

Nasze zmienne elementy to x, y i z.

Do wykonywania takich czynności przyda nam się funkcja. Definicja funkcji wygląda następująco:

```js
function nazwaFunkcji() {
    co ma się wydarzyć;
}

np.:
function powitanie() {
    console.log('Hello World!');
}
```

Teraz funkcję należy wywołać:

```js
nazwaFunkcji();
powitanie();
```

Przy każdym wywołaniu funkcji zadziała ona tak samo.

Ale co z naszymi zmiennymi parametrami? Otóż w nawiasach przy nazwie funkcji określmy właśnie te parametry. Np.

```js
function powitanie(name) {
    console.log('Hello ' + name);
}
```

Przy wywołaniu w miejscu parametru należy wstawić istniejące dane, np.

```js
powitanie('Marta');
>>> Hello Marta
powitanie('Ania');
>>> Hello Ania
```

Wróćmy do liczenia powierzchni: nasze zmienne parametry to szerokość jednej ściany, drugiej ściany i wysokość, czyli:

```js
function powierzchniaMalowania(sciana1, sciana2, wysokosc) {
    ....
}
```

Teraz wnętrze naszej funkcji:

```js
function powierzchniaMalowania(sciana1, sciana2, wysokosc) {
    var x = sciana1;
    var y = sciana2;
    var z = wysokosc;
    var szerScian = 2*x + 2*y;
    var powScian = szer_scian * wysokosc;    
    var powSufitu = x * y;
    var powMalowania = powScian + powSufitu;

    console.log(powMalowania)
}
```

I jej wywołanie:

```js
powierzchniaMalowania(6, 5, 2.5);
powierzchniaMalowania(3, 4, 2.5);
```

### Zadanie:

W swoim pliku JS napisz funkcję o nazwie `helloGirlsJS`, która po wywołaniu wyświetli następujący napis: "Cześć, \[tu poda imię osoby podanej w wywołaniu\]! Witaj na girls.js!".

