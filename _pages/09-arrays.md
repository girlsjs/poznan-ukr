---
title: 9. Tablice
layout: post
---

Zmienne, które dotychczas poznałaś, zawierały tylko jeden element - string, liczbę, czy wartość logiczną. Czasami jednak musimy skorzystać z całej listy danych. Do ich przechowywania służą nam tablice.

```js
let tablica = ["pomarancza", 34, true, "mandolina", 45 [67, 56, "czerwony"]];
```

Tablicę tworzymy zapisując dane pomiędzy kwadratowymi nawiasami i oddzielając te elementy od siebie przecinkami. W tablicy możemy przechowywać różne typy danych: stringi, liczby, zmienne typu logicznego, a nawet inne listy.

Stwórzmy np. listę znajomych:

```js
let friends = ["Michał", "Marta", "Mikolaj", "John", "Natalia", "Ania"];
```

Aby wyświetlić element listy odwołujemy się do listy i pozycji danego elementu.

UWAGA!

Kolejność elementów liczymy od 0. Tak więc:

```js
console.log(friends[0]);
>>> Michał

console.log(friends[3]);
>>> John
```

W swoim pliku JS stwórz teraz tablicę o nazwie "group", która zawiera imiona wszystkich osób z grupą, z którą pracujesz na warsztacie. Następnie wypisz w konsoli imię pierwszej zapisanej osoby.

Podobnie jak stringi, długość tablicy możemy ustalić dzięki właściwości **length**

```js
console.log(friends.length); 
>>> 6
```

Teraz wypisz w konsoli długość tablicy z imionami osób z Twojej grupy, a następnie wyloguj imię osoby, która jest zapisana jako ostatnia.

Do dodawania nowego elementu służy metoda **push**:

```js
friends.push('Kasia');

console.log(friends);
>>> ["Michał", "Marta", "Mikolaj", "John", "Natalia", "Ania","Kasia"]
```

Za jej pomocą dodajemy nowy element na końcu tablicy.

Dodaj do swojej tablicy "group" jeszcze jedno dowolne imię używając do tego metody `push`, a następnie wypisz je w konsoli.

Możemy również nadpisać istniejący element tablicy o określonej pozycji:

```js
friends[2] = "Tomek";

console.log(friends);
>>> ["Michał", "Marta", "Tomek", "John", "Natalia", "Ania","Kasia"]
```

Nadpisz ostatnio dodane do swojej tablicy imię innym. Raz jeszcze wypisz ostatnie imię w konsoli.

Różne tablice możemy dodać do siebie. Stwórz tablicę z imionami przyjaciół z pracy i drugą z imionami przyjaciół z imprez.

Aby stworzyć tablicę w której znajdą się imiona wszystkich Twoich przyjaciół użyjemy metody `concat`

```js
let work_friends = ["Michał", "Marta", "Tomek", "John", "Natalia", "Ania","Kasia"];
let party_friends = ["Asia", "Kamil", "Bartek", "Ola", "Weronika", "Czarek"];

let all_friends = work_friends.concat(party_friends);

console.log(all_friends);
>>> ["Michał", "Marta", "Tomek", "John", "Natalia", "Ania","Kasia", "Asia", "Kamil", "Bartek", "Ola", "Weronika", "Czarek"]
```

Sprawdź w konsoli, jak wygląda nowa tablica powstała za pomocą `concat`.

By "pobrać" kawałek tablicy używamy metody `slice`. Wymaga ona określenia od którego elementu chcemy ciąć i na którym chcemy skończyć

```js
let friends = ["Michał", "Marta", "Tomek", "John", "Natalia", "Ania","Kasia"];

let part = friends.slice(1, 4);
console.log(part);
>>> Marta, Tomek, John
```

Stwórz teraz jeszcze jedną tablicę, której elementami będą pierwsze i drugie imię z tablicy "group". Użyj do tego metody `slice`.

Do usuwania, lub zamieniania kawałka tablicy służy metoda `splice`

```js
tablica.splice(od którego elementu, ile elementów usunąć, co tam wstawić w zmian)

let friends = ["Michał", "Marta", "Tomek", "John", "Natalia", "Ania","Kasia"];

friends.splice(2,1);
console.log(friends);
>>> Michał, Marta, John, Natalia, Ania, Kasia,
```

Zaczynam od pozycji 2, usuwam jeden element, żadnego nie dodaję.

```js
let friends = ["Michał", "Marta", "Tomek", "John", "Natalia", "Ania","Kasia"];

friends.splice(2, 0, "Patrycja");
console.log(friends);
>>> Michał, Marta, Patrycja, John, Natalia, Ania, Kasia,
```

Zaczynam od elementu na 2 pozycji, usuwam jeden element, dodaje element "Patrycja".

Usuń teraz za pomocą `splice` pierwsze imię z tablicy "group" i w jego miejsce wstaw inne, dowolne imię.

**UWAGA:** `friends.slice` nie modyfikuje tablicy `friends`, zwraca tylko jej określone elementy. `friends.splice` modyfikuje tablicę `friends`. Jest to ważna różnica. 

### Wyszukiwanie elementu

do wyszukiwania pozycji elementu służy metoda indexOf. Zwraca ona indeks danego elementu lub -1 jeśli go nie znajdzie

```js
let friends = ["Michał", "Marta", "Tomek", "John", "Natalia", "Ania","Kasia"];

if (friends.indexOf('Marta') !== -1) {
    console.log('Marta znajduje się w tej tablicy!');
} else {
    console.log('Marty nie ma w tej tablicy');
}
```

Korzystając z `indexOf()` sprawdź jaką pozycję ma Twoje imię w tablicy "group".

### Pętla po tablicy

Pętla to doskonały sposób przechodzenia (iterowania) po elementach tablicy. Wykorzystajmy ją do wypisania naszych znajomych. Aby wypisać jakiś element tablicy określamy jego indeks:

```js
let friends = ["Michał", "Marta", "Tomek", "John", "Natalia", "Ania","Kasia"];

console.log(friends[0]);
console.log(friends[1]);
console.log(friends[2]);
console.log(friends[3]);
....
```

Ale pojawiają się dwa problemy. Po pierwsze, będzie to mało optymalne. Po drugie, co jeśli nie wiem ile jest elementów na liście i jak długo mam powtarzać ten sam kod?

Spróbujmy więc pętli `for`:

inicjacja licznika - pierwsza pozycja na liście ma index 0, więc zaczynamy liczyć o 0, `let i = 0;`

koniec licznika - pętlę powtarzamy aż przejdzie po wszystkich elementach listy. Liczbę elementów określamy za pomocą właściwości `length`. Czyli powtarzamy pętlę, dopóki licznik jest mniejszy od liczby moich przyjaciół: `i < friends.length`

powiększanie/zmniejszanie licznika - po każdej pętli idziemy do kolejnej osoby czyli zwiększamy licznika o 1,`i += 1;`

```js
let friends = ["Michał", "Marta", "Tomek", "John", "Natalia", "Ania","Kasia"];
for (let i = 0; i < friends.length; i += 1) {
    console.log(friends[i]);
}
```

Przećwiczmy to jeszcze wracając do naszej wiadomości. Powiedzmy, że chcemy ją spersonalizować i wyświetlić, np.

"Cześć Michał! Miło nam Cię powitać na girls.js!"

Wystarczy do naszej wcześniejszej pętli dodać brakujący tekst powitania:

```js
let friends = ["Michał", "Marta", "Tomek", "John", "Natalia", "Ania","Kasia"];
for(let i = 0; i < friends.length; i+=1) {
    console.log("Cześć " + friends[i] +"! Miło nam Cię powitać na girls.js!");
}
```

### Zadanie:

Używając pętli `for` spraw, aby w konsoli pojawił się napis witający na girls.js wszystkie osoby zapisane w Twojej tablicy "group". Tekst ma być następujący: "Cześć \[tu imię osoby\]! Miło nam Cię powitać na girls.js!".



### Zadanie:

Wykorzystując pętlę znajdź wypisz wszystkie samogłoski ze zdania: 

"Nad rzeczką opodal krzaczka, mieszkała kaczka-dziwaczka, lecz zamiast trzymać się rzeczki, robiła piesze wycieczki."

Podpowiedź: string można traktować jak tablicę znaków ;\)
