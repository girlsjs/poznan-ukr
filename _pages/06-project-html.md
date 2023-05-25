---
title: 6. Szkielet projektu
layout: post
---

Dość zapisywania zmiennych w konsoli, czas stworzyć ramy naszego projektu i zacząć pracować z prawdziwymi plikami!

Na sam początek stwórz w wybranej lokalizacji \(np. na pulpicie\) nowy folder. To w nim będziemy zapisywać pliki z naszego projektu. Potrzeba nam trzech plików - pierwszy z kodem HTML, drugi z kodem CSS i trzeci z kodem JavaScript. Takie pliki możemy dodawać z poziomu edytora - otwórz w edytorze stworzony przez siebie folder i dodaj nowe pliki albo możesz tworzyć pliki bezpośrednio w wybranej lokalizacji. Pamiętaj tylko, by dodać im odpowiednie rozszerzenia.

### Plik HTML

Najpierw stwórz plik `index.html` i wklej do niego następujący kod:

```
<!DOCTYPE html>
<html>
   <head>
      <title>Girls.JS - Poznan</title>
   </head>
   <body>
      <h1>Hello, Girls.JS!</h1>
   </body>
</html>
```

Teraz kliknij dwukrotnie na plik `index.html`, który masz zapisany w folderze. Powinien się automatycznie otworzyć w przeglądarce. Powinnaś widzieć napis **Let's make some magic here!** i mieć możliwość przejścia do konsoli. Udało się? Świetnie! Czas na dodanie stylów.

### Plik CSS

W tym samym folderze utwórz kolejny folder o nazwie `css`, a w nim plik `style.css`. Teraz musimy powiedzieć przeglądarce, skąd ma brać style dla naszego kodu HTML. W tym celu dodamy do kodu HTML w znaczniku `<head>` następującą linijkę:

`<link rel="stylesheet" href="css/style.css">`

Do pliku `style.css` wklej poniższy kod:

```css
h1 { 
    color: red;
}
```

Zapisz plik `style.css` i odśwież Twój podgląd pliku `index.html` w przeglądarce. Napis **Let's make some magic here!** powinien być teraz czerwony. Dzięki temu wiemy, że plik ze stylami jest prawidłowo podłączony do pliku html. Teraz czas na najważniejsze, czyli plik JavaScript.

### Plik JavaScript

W swoim folderze stwórz kolejny folder, tym razem o nazwie `js`. W nim utwórz plik `app.js`. To tutaj będziemy zapisywać nasz cały kod JavaScript, dzięki któremu na naszej stronie będzie się działa magia ;\) Aby podłączyć nasz skrypt do strony w HTML, przed zamknięciem znacznika &lt;/body&gt; wklej następującą linijkę:

`<script src="js/app.js"></script>`

Ale skąd będziemy wiedzieć, że nasz plik JS naprawdę jest dobrze podłączony? 

**Musimy sprawdzić konsolę!**

W pliku `app.js` dodaj kod:

`console.log('działa!');`

Teraz zapisz plik JS, odśwież podgląd pliku `index.html` w przeglądarce i przejdź do konsoli. Powinnaś zobaczyć tam napis "działa!". To znak, że z Twoim plikiem JS wszystko jest w porządku i możesz ruszyć do wykonywania kolejnych zadań :\)

