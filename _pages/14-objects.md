---
title: 14. Jesteś obiektem
layout: post
---

... bo wszystko jest obiektem ;\) To kolejny typ danych. Wygląda następująco:

```js
let zmienna = {
    klucz: wartosc,
    klucz2: wartosc2,
    klucz3: wartosc3
}
```

Jak widzisz, przypomina tablicę. Z tym że w tablicy bardzo duże znaczenie ma kolejność elementów które się w niej znajdują. W przypadku obiektów kluczowe są... klucze ;\)

Gdyby przedstawić jakąś osobę jako obiekt, moglibyśmy to zrobić w następujący sposób:

```js
let person = {
    name: 'Natalia',
    age: 27,
    hobby: ['swimming', 'cycling', 'fantasy books']
}
```

By odwołać się do jakiegoś elementu obiektu trzeba odwołać się do jego klucza, np.:

```js
person.hobby;
```

Do istniejącego obiektu możemy dodawać nowe elementy:

```js
person.city = 'Poznań';
console.log(person);
```

Możemy je także usuwać:

```js
delete person.hobby;
```

Czasami w obiekcie może być inny obiekt:

```js
 let person = {   
    name: 'Natalia',
    age: 27,
    hobby: ['swimming', 'cycling', 'fantasy books'],
    city: 'Poznan',
    family: {
        mom: 'Anna',
        dad: 'Paweł',
        sister: 'Karolina'
    }
}
```

Jak wyświetlić imię siostry?

```js
person.family.sister;
```



