---
title: 10. Функції
layout: post
---

Іноді ми хочемо зробити однакові речі, але з різними властивостями. Наприклад, ми хочемо пофарбувати всю квартиру і нам потрібно порахувати площу стін для кожної кімнати. У нас є кімнати з різними розмірами, але сам підрахунок буде виглядати абсолютно однаково:

Фарбуємо кімнату розміром 6м х 5м і висотою 2,5м.

Обраховуємо периметр стін: 2\*6 + 2\*5 = 22

Вираховуємо площу стін: 22 × 2,5 = 55

Обчислюємо площу стелі: 6 × 5 = 30

Додаємо площу стін і стелі: 55 + 30 = 85

І так для 7 різних кімнат нашого будинку. Але ми можемо скоротити. Зрештою, ідея полягає в тому, щоб зробити щось подібне:

```js
let x = wall1;
let y = wall2;
let z = height;
let wallLength = 2*x + 2*y;
let wallArea = wallLength * z;
let ceilArea  = x * y;
let painting = wallArea + ceilArea;
```

Елементи, які будуть змінюватись: x, y та z.

Для здійснення такої діяльності нам знадобиться функція. Опис функції виглядає наступним чином:

```js
function functionName() {
    що має статися;
}

// Наприклад:
function greetings() {
    console.log('Hello World!');
}
```

Тепер слід викликати функцію:

```js
functionName();
greetings();
```

Кожного разу, коли функція викликається, вона буде працювати однаково.

А як же наші параметри-змінні? Що ж, вкажемо ці самі параметри в дужках поруч з назвою функції. Наприклад:

```js
function greetings(name) {
    console.log('Hello ' + name);
}
```

При виклику потрібно вставити існуючі дані замість параметра, наприклад:

```js
powitanie('Marta');
>>> Hello Marta
powitanie('Ania');
>>> Hello Ania
```

Повернімося до підрахунку площі: наші змінні параметри - це ширина однієї стіни, іншої стіни та висота, тобто:

```js
function paintingArea(wall1, wall2, height) {
    ....
}
```

Тепер всередині нашої функції:

```js
function paintingArea(wall1, wall2, height) {
    var x = wall1;
    var y = wall2;
    var z = height;
    var wallLength = 2*x + 2*y;
    var wallArea = wallLength * z;    
    var ceilArea  = x * y;
    var painting = wallArea + ceilArea;
    console.log(painting)
}
```

І її виклик:

```js
paintingArea(6, 5, 2.5);
paintingArea(3, 4, 2.5);
```

### Завдання

У JS-файлі напиши функцію під назвою `helloGirlsJS`, яка при виклику виводитиме наступний напис:

"Привіт, [тут ім'я людини]! Ласкаво просимо до girls.js!".

Або ж: "Cześć, \[ім'я людини польською\]! Witaj na girls.js!".
