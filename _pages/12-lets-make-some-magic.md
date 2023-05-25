---
title: 12. Let's make some magic! ✨ 
layout: post
---

Spróbujmy nieco ożywić naszą naszą stronę i dodać jej trochę koloru.

Stwórzmy naszą pierwszą funkcję w projekcie!

W Twoim pliku JS zdefiniujemy następującą funkcję:

```js
function getRandomColor() {
    console.log('Wylosujmy kolor!')
}

getRandomColor();
```

Odświeżmy naszą stronę w przeglądarce, przejdźmy do konsoli i zobaczmy co się wydarzyło.

Pojawił się wpisany przez nas napis. Czas poszukać kolorów!

Na większości stron internetowych kolory zapisuje się w formie szesnastkowej. Przykładowo: \#FFFFFF to kolor biały,  \#000000 to kolor czarny a FF A5 00 to pomarańczowy. Jak widzisz, w zapisie tym każdy kolor zaczyna się o symbolu ‘\#’ po którym występuje 6 znaków \(liter \(ABCDEF\) i/lub cyfr \(0123456789\)\). By stworzyć losowy kolor musimy losowo zestawić ze sobą owe znaki.

Zacznijmy od tego, by stworzyć zmienną zawierającą wszystkie możliwe znaki:

```js
var letters = '0123456789ABCDEF';
```

Naszą drugą zmienną będzie kolor. Jej jedynym stałym elementem jest znak ‘\#’ więc na razie tylko on będzie się krył pod naszą zmienną.

```js
var color = '#';
```

Później bedziemy do niego dodawać losowe litery spośród tych zawartych w letters.

Funkcja getRandomColor\(\) powinna wyglądać teraz tak:

```js
function getRandomColor() {
    var letters = '0123456789ABCDEF';
    var color = '#';

}
```

Teraz chcemy wyciągnąć z naszej zmiennej letter losowe litery i stworzyć z nich ciąg składający się z 6 znaków. Najłatwiej będzie więc 6-krotnie wyciągnąć z letters losowe znaki. Posłuży nam do tego pętla.

```js
function getRandomColor() {
    var letters = '0123456789ABCDEF';
    var color = '#';

    for (var i = 0; i < 6; i++) {

    }
}
```

Spróbujmy ją przeczytać:

Dla każdego i, które na początku ma wartość zero i jest mniejsze od 6, wykonaj polecenie znajdujące się w klamrze a potem przejdź do i większego o 1.

Jak zapewne się domyślasz, 6 wynika z tego, że musimy 6-krotnie wyciągnąć naszego stringa ‘letters’ po jednej literze. Więc zacznijmy losowanie.

By wyciągnąć jakiś element listy musimy podać jego numer. Co ważne, liczenie elementów listy zaczynamy od cyfry zero. Patrząc na naszą zmienną:

```js
var letters = '0123456789ABCDEF';
```

By wyciągnąć pierwszy elementy \(czyli cyfrę 0\) musimy napisać letters\[0\].

By wyciągnąć literę B użyjemy zapisu letters\[10\]. Ok, ale co z naszym losowaniem?

JavaScript posiada wbudowany obiekt zawierający własności i metody związane z funkcjami i stałymi matematycznymi. Ten obiekt nazywa się **Math**. Przykładowo Math.PI zwróci nam wartość liczby Pi. Więcej o obiekcie Math możecie znaleźć [tutaj](https://developer.mozilla.org/pl/docs/Web/JavaScript/Referencje/Obiekty/Math).  Jedną z metod Math jest metoda random\(\), która zwraca losową wartość z przedziału 0-1. Spróbujmy! Wpisz w konsoli przeglądarki kilkukrotnie Math.random\(\).

My jednak chcemy wylosować liczbę całkowitą z przedziału 0-16. Pomnóżmy więc naszą losową wartość razy 16:

```js
Math.random()*16;
```

Jesteśmy już bliżej. Teraz jednak potrzebujemy liczb całkowitych, nie ułamkowych. Tu z pomocą przychodzi nam kolejna metoda obiektu Math, floor\(\), która zaokroglą liczby do liczb całkowitych. Spróbujmy wpisać w konsoli:

```js
Math.floor(14.567);
Math.floor(-1.38);
```

Naszym celem jest jednak zaokrąglić wynik losowania liczb pomiędzy 0 a 16, czyli:

```js
Math.floor(Math.random() * 16);
```

Będziemy robić kolejne losowanie 6 razy. Czyli proces ten powinniśmy zamieścić wewnątrz naszej pętli. Przypiszmy go do zmiennej:

```js
 function getRandomColor() {
    var letters = '0123456789ABCDEF';
    var color = '#';

    for (var i = 0; i < 6; i++) {
       var randomNumber = Math.floor(Math.random() * 16);
    }
}
```

Kolejny krok to 'wyciągnięcie' literki o wylosowanej pozycji z naszego stringa letters. Gdybyśmy chcieli wyciągnąć literę A wpisalibyśmy

```js
letters[10]
```

My jednak przy każdym przejściu pętli chcemy wyciągnąć literę, która w tym momencie znajduje się pod zmienną randomNumber. Dlatego zamiast 10 wpiszemy randomNumber. Dla przejrzystości przypiszemy tę wartość do zmiennej:

```js
function getRandomColor() {
    var letters = '0123456789ABCDEF';
    var color = '#';

    for (var i = 0; i < 6; i++) {
        var randomNumber = Math.floor(Math.random() * 16);
        var randomLetter = letters[randomNumber];
    }
}
```

Sprawdźmy co się stanie gdy wyświetlimy wylosowaną literę.

```js
function getRandomColor() {    
    var letters = '0123456789ABCDEF';
    var color = '#';

    for (var i = 0; i < 6; i++) {
        var randomNumber = Math.floor(Math.random() * 16);
        var randomLetter = letters[randomNumber];
        console.log(randomLetter);
    }
}
```

I wywołajmy naszą funkcję:

```js
function getRandomColor() { 
    var letters = '0123456789ABCDEF';
    var color = '#';

    for (var i = 0; i < 6; i++) {
        var randomNumber = Math.floor(Math.random() * 16);
        var randomLetter = letters[randomNumber];
        console.log(randomLetter);
    }
}

getRandomColor();
```

Mamy losowe litery spośród letters! My jednak chcemy by były one dodawane co zmiennej color. Tylko w ten sposób uzyskamy kolor. Możemy to zrobić przez dodawanie do istniejącej wartości color nowego elementu \(nowej litery\):

```js
function getRandomColor() {    
    var letters = '0123456789ABCDEF';
    var color = '#';

    for (var i = 0; i < 6; i++) {
        var randomNumber = Math.floor(Math.random() * 16);
        var randomLetter = letters[randomNumber];

        color += randomLetter;
    }
    console.log(color);
}

getRandomColor();
```

Super! My jednak nie chcemy wyświetlać tego koloru a jedynie go zwrócić, by móc używać w przyszłości.

Do zwracania wartości służy polecenie return:

```js
function getRandomColor() {       
    var letters = '0123456789ABCDEF';
    var color = '#';

    for (var i = 0; i < 6; i++) {
        var randomNumber = Math.floor(Math.random() * 16);
        var randomLetter = letters[randomNumber];

        color += randomLetter;
    }

    return "#" + color;
}

getRandomColor();
```

Mamy losowy kolor! Teraz musimy go przypisać do styli tekstu.

By oddzielić poszczególne elementy strony używamy różnych znaczników. Przykładowo między znacznikami &lt;p&gt;&lt;/p&gt; zamieszczamy zawartość paragrafów. &lt;div&gt;&lt;/div&gt; to cały blok, czy też cała sekcja. &lt;table&gt;&lt;/table&gt; to oczywiście tabela. &lt;ul&gt;&lt;/ul&gt; to nieuporządkowana lista; &lt;ol&gt;&lt;/ol&gt; to lista uporządkowana \(ponumerowana\). &lt;li&gt;&lt;/li&gt; to poszczególne elementy listy. &lt;h1&gt;&lt;/h1&gt;, &lt;h2&gt;&lt;/h2&gt;, &lt;h3&gt;&lt;/h3&gt;, &lt;h4&gt;&lt;/h4&gt;, &lt;h5&gt;&lt;/h5&gt;, &lt;h6&gt;&lt;/h6&gt; to nagłówki kolejnego stopnia. W niektórych elementach możemy zagnieżdzać kolejne. Niektóre z nich mogą wystąpić wielokrotnie na stronie. By móc się odwołać do konkretynch elementów nadajemy im id \(przypisane tylko do jednego elementu\) oraz klasę \(class\), którą moga dzielić różne elementy. Np.

```
<p id="magic" class="title">Let’s make some magic!</p>
```

Zamieśćmy napis na naszej stronie pomiędzy znacznikami i nadajmy mu id.

Teraz wróćmy do kodu JS. By znaleźć na stronie element o konkretnym id użyjemy polecenia document.getElementById\(\); W nawiasie zamieszczamy nazwę id. Warto przypisać ten element do zmiennej.

```js
var title = document.getElementById('magic');
```

Teraz stworzymy kolejną funkcję odpowiedzialną za zmianę koloru tekstu.

```js
function changeColor() {

}
```

By zmienić kolor odwołamy się do obiektu style. Gdy wpiszemy

```js
console.log(title.style)
```

JavaScript zwróci nam wszystkie właściwości obiektu style.[ Tutaj ](https://www.w3schools.com/jsref/dom_obj_style.asp)znajdziesz uporządkowaną listę. Nam potrzebna jest właściwość color.

```js
function changeColor() {
    title.style.color
}
```

Dodatkowo chcemy zmienić tę właściwość, czyli nadać jej nową wartość. Robimy to tak, jak zmieniamy wartość zmiennej:

```js
function changeColor() {
    title.style.color = nowy_kolor;
}
```

Nasz nowy kolor zostanie wylosowany podczas wywołania funkcji getRandomColor:

```js
function changeColor() {
    title.style.color = getRandomColor();
}
```

Wywołajmy funkcję changeColor i odświeżmy naszą stronę kilkukrotnie.

Ale może byłoby lepiej, gdyby nasza funkcja była wielokrotnego użytku i można było ją przypisać do różnych elementów na stronie a nie tylko tytułu?

Jeśli się na to zdecydujemy musimy naszej funkcji przypisać parametr. Zamieszczamy go w nawiasie przy nazwie funkcji.

```js
function changeColor(text) {
}
```

Teraz polecenie zmiany koloru musimy przypisać nie do zmiennej title, ale do parametru funkcji który będzie się zmieniał:

```js
function changeColor(text) {
    text.style.color = getRandomColor();
}
```

Teraz wywołując funkcję musimy zastąpić nasz parametr istniejącym elementem strony:

```js
changeColor(title);
```

Ale to jeszcze nie koniec pracy! Nasz napis może mieć dowolny kolor. Ale sprawmy by było jeszcze ciekawiej. Zmieniajmy nasz kolor co 2 sekundy!

Aby uzyskać taki efekt musimy co dwie sekundy wywoływać naszą funkcję changeColor\(title\);

Posłuży nam do tego metoda setInterval\(\); Wygląda ona następująco:

```js
setInterval(function() { 
    co_ma_się_wydarzyć; 
}, coJakiCzas);
```

Czas odmierzamy w milisekundach. 2 sekundy to 2000 milisekund. Czyli:

```js
setInterval(function() { 
    changeColor(title); 
}, 2000);
```

✨ Jest i magia! ✨ 

