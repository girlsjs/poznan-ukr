---
title: 15. Wyprawy kosmiczne
layout: post
---

Programiści zmieniają świat. Ich praca jest niezbędna do eksploracji kosmosu. Spróbujmy i my :D

Jako że nam nie udało się jeszcze nikogo wysłać w kosmos, skorzystamy z pomocy i zasobów NASA.

## Co słychać na Marsie?

Najpierw musimy zdobyć klucz dostępu. Zrobimy to tu: [https://api.nasa.gov/index.html\#apply-for-an-api-key](https://api.nasa.gov/index.html#apply-for-an-api-key).

Pomoże nam on dostać się zasobów udostępnianych przez NASA. Ich listę możecie znaleźć tu: [https://api.nasa.gov/api.html\#how-do-i-see-my-current-usage?](https://api.nasa.gov/api.html#how-do-i-see-my-current-usage?)

Na początek zaczniemy od zdjęcia dnia :\)

Kiedy wejdziecie na ten adres [https://api.nasa.gov/planetary/apod?api\_key=DEMO\_KEY](https://api.nasa.gov/planetary/apod?api_key=DEMO_KEY) zobaczycie... obiekt.

Mamy datę, opis, adresy do zdjęć w dwóch rozmiarach, typ oraz tytuł. Stworzymy stronę, której tłem będzie zdjęcie dnia. Sprawdźmy, jakie jest dzisiaj :D

Na początek pobierz paczkę z plikiem HTML, CSS i JS, która dostępna jest [TUTAJ](https://drive.google.com/open?id=1HEAG_bmuEWIsIX939rXJP3xV-8PFj-0F).

Zaczniemy od tego, by zmieniać tło body na obraz. W CSS służy do tego `background-image`. By zmienić tło za pomocą JSa stworzymy funkcję, której argumentem będzie ścieżka do obrazka:

```js
function changeBackground(imageURL) {

}
```

Posłużymy się właściwością `style` , którą już znamy. Na liście wszystkich styli jest też `backgroundImage`. To do niego przypiszemy adres do naszego obrazka.

Standardowo wyglądałoby to tak:

```js
document.body.style.backgroundImage = "url('img_unicorn.png')";
```

Ale nasz adres obrazka będzie się zmieniał i będzie przyjmował wartość, którą wpiszemy jako argument funkcji, więc:

```js
function changeBackground(imageURL) {
    document.body.style.backgroundImage = "url('" + imageURL + "')";
}
```

Teraz czas na podłączenie się do api NASA!

Na początek stworzymy zmienną z adresem URL, pod którym kryje się obiekt z naszym obrazkiem. Zamiast DEMO\_KEY wpisujemy nasz klucz.

```js
let dataURL = 'https://api.nasa.gov/planetary/apod?api_key=DEMO_KEY';
```

Teraz stwórzmy funkcję `getPicture`. W jej wnętrzu napiszemy kod który będzie pobierał dane z adresu wskazanego pod `dataURL`. Posłuży nam do tego `fetch API` - narzędzie do dynamicznego pobierania danych. Jest to dość nowe rozwiązanie, obsługiwane przez nowe przeglądarki.

Spróbujemy po kolei:

```js
function getPicture() {
    fetch(dataURL)
    .then((resp) => {
        console.log(resp);
    })
}
```

Po uruchemieniu `fetch` zwraca nam Promise. Promise'y pozwalają nam kontrolować kolejność kodu. Jeżeli jakaś obietnica została spełniona zaczyna działaś kolejny kawałek kodu \(then\). Jeśli pod adresem `dataURL` coś się znajduje, uzyskujemy dostęp do odpowiedzi z tej strony i ją wyświetlamy.

Kolejny nowy elemeny to strzałki `=>`. Jest to prostszy zapis znanych nam funkcji. Nasza funkcja ma jeden argument \(`resp`\) i ten argument wyświetla w konsoli. Wywołajmy funkcję i spójrzmy na naszą konsolę. Mamy w niej odpowiedź z serwera. Zamieńmy ją na przyjaźniejszy format, np. json. Najczęściej dane w formacie JSON są pobierane z serwera jako tekst, a następnie przekształcane w obiekt. By przekształcić naszą odpowiedź z serwera dopiszmy do niej metodę `json()`.

```js
function getPicture() {
    fetch(dataURL)
    .then((resp) => {
        return resp.json();
    })
}
```

To także jest obietnica \(Promise\). Po jej spełnieniu powinniśmy móc wyświetlić nasz obiekt. Sprawdźmy to.

```js
function getPicture() {
    fetch(dataURL)
        .then((resp) => {
            return resp.json();
        })
        .then((data) => {
            console.log(data);
        });
}
```

Mamy nasz obiekt! Nam jednak zależy na konkretnym elemencie: `hdurl`. Pamiętasz jak w obiekcie wyświetlamy daną wartość? Dokładnie - odwołując się do klucza.

```js
function getPicture() {
    fetch(dataURL)
        .then((resp) => {
            return resp.json();
        })
        .then((data) => {
            console.log(data.hdurl);
        });
}
```

Jest i nasz url, który powinniśmy użyć jako argument w funkcji `changeBackground`:

```js
function getPicture() {
    fetch(dataURL)
        .then((resp) => {
            return resp.json();
        })
        .then((data) => {
            changeBackground(data.hdurl);
        });
}
```

Wiemy już jakie jest zdjęcie dnia?

### Na podbój Marsa!

Teraz zróbmy krok dalej. Sprawdźmy, co słychać na Marsie. Pomoże nam w tym łazik, który dzielnie fotografuje swoje dzienne przygody, a dane z tych wypraw znajdziecie pod tym linkiem: [https://api.nasa.gov/mars-photos/api/v1/rovers/curiosity/photos?sol=1000&api\_key=DEMO\_\_KEY](https://api.nasa.gov/mars-photos/api/v1/rovers/curiosity/photos?sol=1000&api_key=DEMO__KEY)

Zobaczcie, że teraz czeka nad pod linkiem o wiele więcej obiektów, niż przed chwilą. Zróbmy z nich użytek!

Zacznijmy od przypisania naszego URLa do zmiennej:

```js
let urlMars = "https://api.nasa.gov/mars-photos/api/v1/rovers/curiosity/photos?sol=1000&apikey=DEMO_KEY";
```

Stwórzmy nową funkcję, która będzie korzystała ze znanego nam narzędzia `fetch API`:

```js
function getMarsPicture() {
    fetch(urlMars)
        .then((resp) => {
            return resp.json();
        })
        .then((data) => {
            console.log(data);
        });
}
```

Wywołajmy funkcję i sprawdźmy, co dzieje się w konsoli. Mamy obiekt z kluczem `photos`\(to mogło chwilę potrwać, zanim coś pojawiło się w konsoli\). Sprawdźmy, co jest w środku, czyli pod kluczem `photos`:

```js
function getMarsPicture() {
    fetch(urlMars)
        .then((resp) => {
            return resp.json();
        })
        .then((data) => {
            console.log(data.photos);
        });
}
```

W środku mamy tablicę obiektów. Sprawdźmy teraz, ile jest obiektów:

```js
function getMarsPicture() {
    fetch(urlMars)
        .then((resp) => {
            return resp.json();
        })
        .then((data) => {
            console.log(data.photos.length);
        });
}
```

Bardzo dużo! Sprawdźmy, co jest w środku pierwszego z nich:

```js
function getMarsPicture() {
    fetch(urlMars)
        .then((resp) => {
            return resp.json();
        })
        .then((data) => {
            console.log(data.photos[0]);
        });
}
```

To już jest bliższe naszym oczekiwaniom. Z czegoś takiego możemy coś zrobić :\) Mamy obiekt, w środku jest klucz `img_src` z adresem obrazka. Wykorzystamy go. Zróbmy na naszej stronie galerię. Będzie się ona znajdować w znaczniku `div` o id `content`. Stwórzmy więc zmienną:

```js
let gallery = document.getElementById('content');
```

Teraz stwórzmy funkcję `createGallery` z argumentem `dataList`. Będzie to właśnie ta bardzo długa tablica, którą wyciągnęliśmy z `data.photos` :

```js
function createGallery(dataList) {
}
```

Wewnątrz funkcji za pomocą pętli stworzymy 9 obrazków i dodamy je do strony. W HTML obraz wyświetlamy za pomocą tagu `img`:

```markdown
<img src="adres_obrazka" class="klasa/klasy" alt="co_sie_wyswietli_jesli pod danym adresem nie ma obrazka">
```

Tak będzie on wyglądać w HTML. A jak to zrobić za pomocą JS? Zacznijmy od pętli, która będzie się powtarzać 9 razy:

```js
function createGallery(dataList) {
    for(let i = 0; i < 9; i++) {

    }
}
```

Za każdym razem będziemy tworzyć nowy element. Będziemy go przypisywać do zmiennej `img`. Nowy element tworzymy za pomocą:

```js
document.createElement('nazwa_tagu');
```

U nas nazwą tagu będzie `img`, czyli:

```js
function createGallery(dataList) {
    for(let i=0; i < 9; i++) {
        let img = document.createElement('img');
    }
}
```

Kolejny krok to wstawienie nowego elementu do diva `content`. Służy do tego metoda `appendChild('nazwa_wstawianego_elementu')`

```js
function createGallery(dataList) {
    for(let i=0; i < 9; i++) {
        let img = document.createElement('img');
        gallery.appendChild(img);
    }
}
```

Sprawdźmy naszą stronę.

Brakuje naszych ścieżek do obrazków. Wróćmy do funkcji `getMarsPictures`. Mieliśmy tu tablicę z wieloma obiektami w środku, w których mieliśmy potrzebny nam `img_src`. Przypiszmy naszą tablicę do zmiennej:

```js
function getMarsPicture() {
    fetch(urlMars)
        .then((resp) => {
            return resp.json();
        })
        .then((data) => {
            let pictureList = data.photos;
        });
}
```

Mamy tu listę, którą będziemy wykorzystywać w funkcji `createGallery`. Wywołajmy więc `createGallery` z tym argumentem wewnątrz funckji `getMarsPicture`:

```js
function getMarsPicture() {
    fetch(urlMars)
        .then((resp) => {
            return resp.json();
        })
        .then((data) => {
            let pictureList = data.photos;
            createGallery(pictureList);
        });
}
```

Ok, ale co się kryje pod naszym `pictureList`? Sprawdźmy to za pomocą`console.log`. W funkcji `createGallery` wyświetlmy w konsoli nasz argument `dataList`. Teraz wywołajmy funkcję `getMarsPicture`. W niej wywołujemy też funkcję `createGallery`:

```js
function createGallery(dataList) {
    for(let i=0; i < 9; i++) {
        let img = document.createElement('img');
        gallery.appendChild(img);
        console.log(dataList);
    }
}
```

Mamy 9 tablic, w których są nasze obiekty. A my przy każdej pętli potrzebujemy tylko 1 obiekt. Obiekt, którego indeks jest zgodny z naszym i dlatego wyświetlajmy tylko obiekty o indexie równym `i`:

```js
function createGallery(dataList) {
    for(let i=0; i < 9; i++) {
        let img = document.createElement('img');
        gallery.appendChild(img);
        console.log(dataList[i]);
    }
}
```

Jesteśmy bliżej - mamy 9 obiektów. A potrzebujemy tylko wartości, która kryje się pod `img_src`, więc wyświetlmy ją:

```js
function createGallery(dataList) {
    for(let i=0; i < 9; i++) {
        let img = document.createElement('img');
        gallery.appendChild(img);
        console.log(dataList[i].img_src);
    }
}
```

Coraz lepiej. Teraz, zamiast ją wyświetlać, przypiszmy ją do zmiennej i przesuńmy przed dodanie `img` do `gallery`:

```js
function createGallery(dataList) {
    for(let i=0; i < 9; i++) {
        let img = document.createElement('img');
        let imgPath = dataList[i].img_src;
        gallery.appendChild(img);
    }
}
```

Jak teraz dodać `imgPath` do naszego elementu `img`? Za pomocą właściwości `src`. Jest podobna do właściwości `style`. Musimy jej przypisać wartość:

```js
function createGallery(dataList) {
    for(let i=0; i < 9; i++) {
        let img = document.createElement('img');
        let imgPath = dataList[i].img_src;
        img.src = imgPath;
        gallery.appendChild(img);
    }
}
```

Wywołajmy teraz funkcję `getMarsPictures` i sprawdźmy, co słychać na Marsie! 

