---
title: 13. A jednak się kręci! 🪐
layout: post
---

Kopernik wstrzymał Słońce, ruszył Ziemię. My poruszymy wszystkie 8 planet!

Pobierzcie naszą paczkę: [LINK](https://drive.google.com/file/d/1nbT2_pX-eKDJi1JIGvDzoB4Tr_rCfAjk/view)

W środku znajdziecie plik index.html, main.js oraz main.css.

Kiedy otworzycie plik index.html w przeglądarce zobaczycie 9 zdjęć planet.

Teraz zajrzyjmy do tego pliku w edytorze tekstu.

Nasze planety to elementy listy:

```markdown
<ul class="carousel">
    <li class="single-slide">…</li>
</ul>
```

Jak możecie się domyślić, naszym zadaniem jest stworzenie karuzeli. Zaczniemy od jej odpowiedniego ułożenia. Posłużą nam do tego style CSS które zamieścimy w pliku main.css. By podpiąć style do naszego pliku html musimy między tagami &lt;head&gt;&lt;/head&gt; dodać kolejny element:

```markdown
<link rel="stylesheet" type="text/css" href="sciezka/do/pliku.css">
```

Jeśli zrobicie to poprawnie, powinnyście zobaczyć rozgwieżdżone niebo.

Czas dodać nasze style. Pomoże Wam w tym strona [https://www.w3schools.com/css/](https://www.w3schools.com/css/). Nie bójcie się również korzystać z wyszukiwarki Google. By dodać jakiś styl odwołujmy się do klas poszczególnych elementów. By to zrobić w plku CSS musimy zapisać:

```css
.nazwaKlasy {
    wlasciwosc: wartosc;
}
```

np.:

```css
.carousel {
    background-color: green;
}
```

Tło całej karuzeli powinno zrobić się zielone.

Zacznijmy od ułożenia planet obok siebie. Niech każdy slajd ma szerokość \(`width`\) 800px.  Ustawmy szerokość całej karuzeli na ok. 7300px.

Sprawmy też, by każda planeta znajdowała się na środku slajdu \(`text-align: center;`\). Ale nadal widzimy więcej niż jedną planetę. Określmy więc szerokość \(`width`\) sceny \(`.carousel-stage`\), i schowajmy to, co się w niej nie zmieści \(`overflow: hidden;`\). Wycentrujmy też naszą scenę \(`.carousel_stage, margin-left: auto; margin-right: auto;`\).

Teraz nawigacja. Widzicie dwie strzałki pod karuzelą? Najpierw umieścimy je na odpowiedniej wysokości - czyli w połowie wysokości karuzeli. Na początku nadajmy karuzeli \(`.carousel`\) `position: relative`. To w stosunku do niej będziemy ustawiać strzałki. By strzałki nie były pod karuzelą, a 'unosiły się w powietrzu' nadajmy nawigacji \(`.carousel-nav`\) `position:absolute`. Umieśćmy strzałki w połowie wysokości karuzeli. Do styli dodajmy więc `top: 50%` \(nawigacja znajdzie się wtedy w 50% wysokości rodzica, który posiada `position: relative`\). Ale coś nie do końca się zgadza. Strzałki są trochę za nisko. Dokładnie połowę swojej wysokości za nisko. Dokonamy więc małej transformacji: `transform: translateY(-50%)`.

Następny krok to umieszczenie jednej strzałki po prawej, a drugiej po lewej stronie karuzeli. Odpowiednio `float: left;` i `float: right;`.

Czas na wprawienie naszych planet w ruch!

Na początek podepnijmy do naszej strony plik `main.js`. Robimy to podobnej zasadzie jak plik CSS z tym, że używamy tagu `script` , a ścieżkę wpisujemy w atrybucie `src`.

```markdown
<script src="sciezka/do/pliku.js"><script>
```

Wejdź na stronę, a następnie w konsolę przeglądarki. Jeśli wszystko działa, powinien pojawić się komunikat.

Pomyślmy, jak ma działać nasza karuzela. Wyobraźmy sobie, że jest to taśma filmowa i w określonych momentach \(po kliknięciu strzałki lub po upływie określonego czasu\) cała taśma ma się przesunąć o szerokość jednej klatki \(czyli jednego slajdu\).

Przejdźmy więc do pliku `main.js`. Usuńmy aktualny kod. Zaczniemy od określenia naszych zmiennych:

`carousel` dla karuzeli

`stage` dla sceny naszej karuzeli

`prev` dla przycisku "wstecz"

`next` dla przycisku "następny"

Nie zapomnij o słowach kluczach definiujących zmienne \(czyli używamy tu `let` albo `const`\).

Teraz pobierzemy elementy HTML do określonych przez nas zmiennych. Posłuży nam do tego znana już metoda `querySelector()`, która wyświetli nam pierwszy element na stronie o określonym atrybucie, np. klasie.

```js
var carousel = document.querySelector('.carousel');
```

Pobierz w ten sposób elementy dla reszty zdefiniowanych zmiennych \(czyli dla naszej sceny i dwóch przycisków\).

Zostanie nam jeszcze jedna zmienna do zdefiniowania: `slide` dla pojedynczych elementów karuzeli. Tu musimy wziąć wszystkie slajdy, dlatego skorzystamy z metody `querySelectorAll()`.

Zróbmy to ze wszystkimi elementami na stronie :\)

Kolejny krok, to określenie, o jaką szerokość ma się przesuwać nasza “taśma”. Jak już wspomnieliśmy, jest to szerokość jednego slajdu. Spróbujmy więc “wyciągnąć” tę wartość. Wykorzystamy do tego właściwość `clientWidth` która zwraca szerokośc danego elementu. Spróbujmy:

```js
var slideWidth = slide.clientWidth;
console.log(slideWidth);
```

Sprawdźmy, co wyświetli się w konsoli. Pojawił nam się komunikat, że wartość jest niezdefiniowana. Sprawdźmy więc, co kryje się pod zmienną `slide`. Pojawia się lista elementów. JS nie potrafi określić szerokości listy elementów. Nasza zmienna slide zawiera w sobie bowiem tablicę ze wszystkimi elementami o klasie `slide`, jakie udało jej się znaleźć w dokumencie. Nasz kod poradzi sobie za to z jednym elementem, np. pierwszym. Pierwszy element listy ma index zero, a więc:

```js
var slideWidth = slide[0].clientWidth;
console.log(slideWidth);
```

Kolejny krok to określenie, który slajd właśnie nam się wyświetla. Początkowo będzie to pierwszy slajd, ale jak wiemy w JS pierwszy element to element 0.

```js
var currentIndex = 0;
```

A co, gdy dotrzemy do ostatniego elementu? Powinniśmy wrócić do początku slajdu. Znajdźmy więc ostatni element. Najpierw określimy liczbę wszystkich elementów. Posłuży nam do tego właściwość length.

```js
var slidesNumber = slide.length - 1;
```

Skąd wzięło się -1? `Slide.length` to liczba slajdów. Czyli 9. Jednak w JavaScript liczenie elementów zaczynamy od 0, a nie 1. Ostatni slajd nie będzie miał wartości 9 tylko 8.

OK. Teraz czas na napisanie funkcji, które wprawi nasz układ słoneczny w ruch i przesunie całą karuzelę o odpowiednią szerokość. Wykorzystamy do tego style. Spróbujmy najpierw za pomocą CSSa przesunąć naszą karuzelę w lewo o jeden slajd, czyli 800px. Pomogą nam w tym właściwości `position`,` left` i `right`.

Gdy już się Wam uda wróćcie do pliku JS. Będziemy manipulować wartościami CSS za pomocą funkcji JavaScript.

Stwórzmy funkcję o nazwie `goToSlide()`Jej wynikiem ma być zmieniona wartość właściwości `left` naszej karuzeli. Ma ona wynieść tyle, by pokazać odpowiedni slajd. Mała podpowiedź - wykorzystamy do tego zmienną `slideWidth` i pozycję slajdu, który chcemy zobaczyć.

Zacznijmy od początku. Aby zmienić wartość `left` karuzeli wykorzystamy metodę `style.left`. Dzięki niej jesteśmy zmienić pozycję danego elementu w stosunku do jego lewej krawędzi.

```js
function goToSlide() {
    carousel.style.left = ...;
}
```

Zastanówmy się, jaką wartość powinno przyjąć `length` , by pokazać drugi slajd. Jaką, by pokazać trzeci, a czwarty? Czy dostrzegasz jakąś ogólną zasadę?

Tak! Mnożymy `slideWidth` razy pozycję konkretnego slajdu!

Więc spróbujmy:

Załóżmy, że zmienna `index` to pozycja naszego slajdu. Zdefiniujmy ją jako 3 \(pozycja 4 slajdu\).

```js
function goToSlide() {
    carousel.style.left = 3 * (-slideWidth);
}
```

Wywołajmy tę funkcję w konsoli.

Działa!

Tylko pojawia się pewien problem - mamy wiele slajdów, każdy ma inny `index`. Pisanie oddzielnej funkcji dla każdego slajdu byłoby mało wydajne. Wykorzystajmy więc parametry funkcji! Wtedy dla różnych wartości możemy użyć tej samej funkcji.

```js
function goToSlide(index) {
    carousel.style.left = index * (-slideWidth);
}
```

Wywołajmy tę funkcję w konsoli wpisując, np. `goToSlide(3);` `goToSlide(1);` `goToSlide(4);`

Działa! Tylko teraz `currentIndex` też powinien się zmienić. Powinien być równy numerowi, który wpisaliśmy jako argument. Dopiszmy wiec do naszej funkcji tę zmianę:

```js
function goToSlide(index) {
    carousel.style.left = index * (-slideWidth);
    currentIndex = index;
}
```

Przejdźmy do nawigacji :\)

Klikanie na przycisk `carousel-next` powinno nas przenosić do slajdu o indeksie większym o 1. Klikanie na przycisk `carousel-prev` powinno nas przenosić do slajdu o indeksie mniejszym o 1 od aktualnego indeksu.

Stwórzmy więc dwie funkcje. Na początek

```js
 function slideToNext() {
 }
```

Ma ona przesuwać slajdy do przodu o 1 przy każdym wywołaniu. Czyli wykorzystujemy tu funkcję `goToSlide()`. Tylko co będzie naszym argumentem? Jak wspomnieliśmy wcześniej, każde wywołanie naszej funkcji ma przenosić nas do slajdu o indeksie o 1 większym od indeksu aktualnego slajdu. Indeks aktualnego slajdu przechowujemy w zmiennej `currentIndex`. Czyli nasz argument to `currentIndex + 1`.

```js
function slideToNext() {
    goToSlide(currentIndex + 1);
}
```

Zróbmy analogicznie z `slideToPrev`.

Kolejny krok to wywołanie obu funkcji podczas klikania na przyciski. Klikanie to wydarzenia \(eventy\), kóre odbywają się na stronie. Mogą być one wywołane prze użytkownika \(jak kliknięcie\), albo jakiś element na stronie. Wysłanie formularza, załadowanie obrazka, to też zdarzenie. Przykładowe zdarzenia na stronie to:

| Zdarzenie | Opis: |
| :--- | :--- |
| blur | obiekt przestał być aktywny |
| change | obiekt zmienił swoją zawartość \(np. pole formularza\) |
| click | kliknięcie na obiekt |
| dblclick | podwójne klikniecie na obiekt |
| focus | wybrnie danego obiektu na stronie |
| keydown | naciśniemy klawisz na klawiaturze |
| input | w czasie trzymania klawisza |
| keyUp | puścimy klawisz na klawiaturze |
| load | gdy obiekt został załadowany \(może to być nawet cała strona\) |
| mouseover | gdy kursor znalazł się na danym obiekcie |
| mouseout | gdy kursor opuścił dany obiekt |
| contextmenu | gdy kliknięto prawym klawiszem myszki i pojawiło się menu kontekstowe |
| wheel | gdy kręcimy kółeczkiem myszki |
| resize | gdy zmieniamy rozmiar okna przeglądarki |
| select | gdy zawartość obiektu została zaznaczona |
| submit | gdy formularz został wysłany |
| unload | użytkownik opuszcza dana stronę |
| animationstart | animacja css się zacznie |
| animationend | animacja css się zacznie |

Do śledzenia, czy dane wydarzenie miało miejsce posłuży nam metoda `addEventListener`

```js
element.addEventListener('event_jako_string', co_ma_się_wydarzyć, opcjonalnie_true_lub_false);
```

Dla wszystkich wydarzeń na stronie stworzymy osobną funkcję. Nazwiemy ją `bindEvents`:

```js
function bindEvents() {
}
```

Zacznijmy od przycisku wstecz. Jest on pod zmienną `prev`. Na tej zmiennej wywołajmy metodę `addEventListener`:

```js
function bindEvents() {
    prev.addEventListener();
}
```

I teraz argumenty. Chcemy śledzić `event` kliknięcia, czyli 'click'. Ma on wywołać funkcję `slideToPrev`. Wstawmy je w odpowiednim miejscu:

```js
function bindEvents() {
    prev.addEventListener('click', slideToPrev);
}
```

Dodajmy analogiczny event do funkcji `bindEvents` z tym, że dla przycisku `next`.

Wywołajmy funkcję `bindEvents`, by sprawdzić, czy przyciski działają :\)

Super! Spójrz jednak, co się będzie działo, jeśli ciągle będziemy klikać "dalej" lub "cofnij" - planety znikają. Nasza karuzela ciągle się przesuwa o 800px. Musimy ją ograniczyć. Po ostatniej planecie niech wraca do pierwszej, a gdy będziemy chcieli cofnąć się z pierwszej, niech pokaże nam ostatnią planetę.

Spójrzmy się jeszcze raz na naszą funkcje:

```js
function goToSlide(index) {
    carousel.style.left = index * (-slideWidth);
    currentIndex = index;
}
```

Wszystko, co się dzieje zależy od indeksu. Zróbmy więc tak, by indeks większy od indeksu ostatniej planety wyniósł 0, a indeks mniejszy od indeksu pierwszej planety był równy indeksowi pierwszej.

Posłużą nam do tego instrukcje warunkowe \(if... else\). Czyli, jeśli indeks jest mniejszy od 0 zmieniamy go na wartość `slidesNumber`

```js
function goToSlide(index) {
    if (index < 0) {
        index = slidesNumber;
    }

    carousel.style.left = index * (-slideWidth);
    currentIndex = index;
}
```

A jeśli jest większy od `slidesNumber` - zmieniamy go na 0.

```js
function goToSlide(index) {
    if (index < 0) {
        index = slidesNumber;
    } else if (index > slidesNumber) {
        index = 0;
    }

    carousel.style.left = index * (-slideWidth);
    currentIndex = index;
}
```

Sprawdźmy teraz.

Dodajmy trochę więcej życia do karuzeli - niech sama się kręci. Wykorzystamy do tego znaną nam już metodę `setInterval`.

Stwórzmy funkcję `autorotate`

```js
function autorotate() {
}
```

Niech co 4s \(4000 ms\) wykonuje się funkcja `slideToNext`:

```js
function autorotate() {
    setInterval(slideToNext, 4000);
}
```

I wywołajmy funkcję `autorotate`.

I teraz wszystko się kręci! :\)

