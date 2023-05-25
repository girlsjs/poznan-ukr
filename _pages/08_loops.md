---
title: 8. Pętle
layout: post
---

Załóżmy, że chcemy coś zrobić kilka razy, np. wysłać 5 takich samych wiadomości, albo nadać identyfikator 30 kolejnym książkom w naszym księgozbiorze. Robienie kilkukrotnie tej samej rzeczy jest mało optymalne. Dlatego możemy wykorzystać pętle. Żeby powtórzyć coś kilkukrotnie potrzebujemy licznika - by wiedzieć, w którym momencie jesteśmy i czy powinniśmy już skończyć, czy nadal powtarzać dany skrypt.

Załóżmy, że chcemy w konsoli napisać pięć razy wiadomość "Cześć! Miło nam Cię powitać na girls.js!". Możemy to zrobić w ten sposób:

```js
console.log("Cześć! Miło nam Cię powitać na girls.js!");
console.log("Cześć! Miło nam Cię powitać na girls.js!");
console.log("Cześć! Miło nam Cię powitać na girls.js!");
console.log("Cześć! Miło nam Cię powitać na girls.js!");
console.log("Cześć! Miło nam Cię powitać na girls.js!");
```

Trochę dużo pisania, prawda? Możemy ten kod uprościć!

### Pętla for

Pętla for wygląda w następujące sposób:

```js
for (start licznika; wyrażenie określające czy należy zakończyć pętlę czy jeszcze nie; zwiększanie/pomniejszanie licznika ) {
    kod który chcemy powtórzyć określoną liczbę razy
}
```

Przeróbmy nasz kod z wiadomością!

start licznika - zaczynamy od 0, czyli tworzymy zmienną \(która istnieje tylko na potrzeby pętli\),

`let i = 0;`

koniec pętli - powtarzamy działanie dopóki licznik nie osiągnie 5, czyli

`i <= 5;`

zwiększanie/pomniejszanie licznika - po każdym przejściu pętli nasz licznik zwiększa się o jeden, czyli

`i += 1`

Pętla będzie więc wyglądać w następujący sposób:

```js
for (let i = 0; i <= 5; i += 1) { 
     console.log("Cześć! Miło nam Cię powitać na girls.js!");
}
```

Licznik możemy też zmniejszać. Wiemy, że wiadomości ma być 5, więc możemy to również zapisać tak:

start licznika - zaczynamy od 5 czyli `let i = 5;`

koniec pętli - powtarzamy dopóki nie osiągniemy 0, czyli dopóki `i` jest większe od zera,`i > 0;`

zwiększanie/pomniejszanie licznika - każda pętla odlicza od pięciu w dół, czyli `i -= 1;`

```js
for (let i = 5; i > 0; i -= 1) {
  console.log("Cześć! Miło nam Cię powitać na girls.js!");  
}
```

Spróbuj w swoim pliku JS zapisać powyższą pętlę. Spraw, by kod powtórzył się 10 razy.

Czas na nasze książki! Przypomnijmy - chcemy dodać identyfikator (id) kolejnym 30 książkom.

Możemy to zrobić tak:

```js
console.log("id-1");
console.log("id-2");
console.log("id-3");
console.log("id-4");
console.log("id-5");
console.log("id-6");
....
console.log("id-30");
```

Ale taki kod zająłby bardzo wiele miejsca. Wykorzystajmy więc pętle! Zauważmy, że tym razem powtarzamy tę samą czynność, jednak string który chcemy wyświetlić, zmienia się. Zwiększa się dokładnie o 1. Podobnie zachowuje się nasz licznik!

Sprawdź co się wydarzy, gdy spróbujesz wyświetlić w konsoli wartość naszego licznika \(to jest zmienna więc wystarczy wpisać jej nazwę\).

```js
for (let i = 0; i < 30; i += 1){
  console.log(i);
}
```

Konsola wyświetliła nam liczby od 0 do 29. W końcu zaczynamy liczyć od 0 i powtarzamy kod dopóki jest mniejsze od 30. Gdy osiąga 30 zatrzymujemy pętlę. Musimy więc lekko przerobić naszą pętlę. Nasze id zaczyna się od 1, a powtarzamy pętlę, dopóki elementy są mniejsze **bądź równe** 30.

```js
for (let i = 1; i <= 30; i += 1) {
  console.log(i);
}
```

Super! Teraz dodajmy brakujący element id, czyli string "id-". Możemy do tego wykorzystać dodawanie. Kiedy dodajemy string do liczby JS zamienia całość na string!

```js
for (let i = 1; i <= 30; i += 1) { 
     console.log("id-" + i);
}
```

### Zadanie:

Wykorzystaj powyższą pętlę, by nadać id 50 książkom. Zapisz kod w swoim pliku JS.


### Pętla while

Oprócz pętli `for` w języku JavaScript występuje pętla `while`, której struktura wygląda tak:

```js
while (wyrażenie sprawdzające czy pętle należy wykonywać dalej) {
    kod który chcemy powtórzyć dopóki jest spełniany warunek w nawiasie
}
```

Pętla `for` jest wykonywana określoną ilość. Pętla `while` działa, dopóki wyrażenie w nawiasach jest prawdziwe.

Zauważ jednak, że w tej pętli nie ma licznika. Dlatego często dodaje się go ręcznie. Wracając do naszej wiadomości do 5 osób:

```js
let counter = 0;
while(counter < 5) {
    console.log("Cześć! Miło nam Cię powitać na girls.js!");  
    counter += 1;

}
```

Zmienną, która jest naszym licznikiem definiujemy poza pętlą. Przy każdej pętli zwiększamy licznik o 1.

### Zadanie:

W swoim pliku JS napisz taką pętlę `while`, która 10 razy napisze w konsoli "JavaScript jest super!".

