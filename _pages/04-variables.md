---
title: 4. Zmienne
layout: post
---

W poprzednim rozdziale w konsoli przeglądarki wpisałyśmy proste działanie matematyczne 33 + 5. Jednak gdybyśmy tego samego równania chciały używać kilkakrotnie w różnych miejscach kodu, byłoby to bardzo niewygodne. Dlatego korzystamy ze zmiennych. Zmienna jest to nazwa zdefiniowana przez nas z określoną wartością. Zmienne pozwalają nam przechowywać fragmenty kodu, których potem możemy używać. W zmiennej można zapisać np. wynik równania, które przed chwilą przypomniałyśmy.

Jak zdefiniować taką zmienną?

```js
var sum = 33 + 5;
```

`var` to instrukcja, która definiuje zmienną. `sum` to nazwa naszej zmiennej. `33 + 5` to działanie, którego wynik będzi wartością naszej zmiennej. Kiedy w konsoli wpiszemy `var sum = 33 + 5;` a następnie wpiszemy `sum`, konsola zwróci nam 38. Od tej chwili dla języka JavaScript `sum` to to samo co `38`.

### var

`var` pochodzi od angielskiego "variable" i oznacza zmienną. Każda definicja zmiennej składa się ze słówka `var`, za którym stoi nazwa danej zmiennej. Nazwy zmiennych mogą składać się z liter, cyfr i niektórych znaków specjalnych, zazwyczaj zaczynają się małą literą. Nazwy zmiennych powinny nam coś mówić. Tzn. nie nazywajmy zmiennych `xyz`, ale właśnie `sum`, `wynik` itp. Dzięki temu łatwiej będzie nam się odnaleźć w naszym kodzie.

To, że do zmiennej przypisałyśmy daną wartość, nie znaczy, że musi ona na zawsze już być jej równa. Mamy możliwość nadpisania tej zmiennej, czyli przypisania jej nowej wartości. Wystarczy wpisać np. `sum = 99`. Od tej chwili dla języka JavaScript `sum` będzie oznaczało to samo co 99. Kiedy nadpisujemy wartość zmiennej, nie zapisujemy`var` przy jej nazwie. `var` używamy tylko przy definiowaniu zmiennej, czyli przy zapisaniu jej po raz pierwszy. Później już posługujemy się samą nazwą zmiennej.

### let i const®

Obecnie używa się również standardu ES6, który jest nowszym standardem języka JavaScript. Zgodnie z nim, zmienne możemy tworzyć przez użycie słowa `let` albo `const`.

Jeśli stworzymy zmienną przez `let`, możemy jej przypisywać wartość dowolną ilość razy, tzn. ją nadpisywać \(tak jak `var` omówione wyżej\). Wtedy możemy mieć taki kod:

```js
let sum;
sum = 15;
sum = 20;
```

Z kolei, gdy stworzymy zmienną przez `const`, jest ona stała i nie możemy przypisać jej innej wartości, niż ta, którą przypisałyśmy na samym początku. Próba przypisania `const` nowej wartości sprawi, że zobaczymy błąd w konsoli.

```js
const sum = 15;
sum = 20; // wyświetli błąd w konsoli z informacją TypeError: Assignment to constant variable.
```

Używanie `let` i `const` w kodzie jest bardzo przydatne, ponieważ możemy rozróżnić wartości, które mogą być nadpisane od tych, które muszą pozostać takie same przez cały kod. Załóżmy na przykład, że mamy jakiś przelicznik, który zawsze jest taki sam. Użyjemy do jego zdefiniowana `const` i dzięki temu jesteśmy pewne, że jego wartość nie zostanie nadpisana.

W związku z benefitami jakie dają nam różnice między `let` i `const`, dobrze jest je stosować w kodzie zamiast tworzenia wszystkich zmiennych z użyciem `var`.

### Zadanie

Stwórz teraz w konsoli dwie zmienne z dowolnymi liczbami. Jedną przy użyciu `let`, drugą przy użyciu `const`. Spróbuj nadpisać obie wartości i zobacz, co wyświetli się w konsoli.

