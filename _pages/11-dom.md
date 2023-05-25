---
title: 11. DOM
layout: post
---

DOM, czyli **Document Object Model** pozwala językowi JS odzwierciedlić układ strony HTML.

W narzędziach developerskich wróćmy do zakładki "Elements". Tam widać całą naszą stronę. Ale jak się odwołać do jakiegoś elementu za pomocą JSa?

Wróćmy do zakładki "Console". Do elementów HTML możemy się dowoływać poprzez ich:

- **id** - `getElementById`

- **tag** \(np. div, p, ul\) - `getElementsByTagName`

- **klasę** - `getElementsByClassName`

- **selektor** - `querySelector` i `querySelectorAll` \(pierwsza zwraca pierwszy element z pasujących, druga zwraca wszystkie pasujące elementy\)

Spróbujmy teraz pobrać do zmiennej nagłówek ze strony, z którą pracujesz. Zobacz, że w pliku `index.html` masz tag `<h1>`, a w nim jakąś treść. Pobierz ten element do zmiennej korzystając z metody `querySelector`. Aby ta metoda zadziałała, musisz ją wywołać na dokumencie HTML, czyli `document` , a potem podać wybrany selektor w nawiasie okrągłym. Twój kod powinien wyglądać tak:

`let header = document.querySelector("h1");`

Wypisz teraz tę zmienną w konsoli i sprawdź, czy zapisał się do niej element HTML. Co widzisz?

Jak umiemy już pobierać elementy do zmiennych, możemy działać dalej! 

🪄 Pora na trochę magii!

