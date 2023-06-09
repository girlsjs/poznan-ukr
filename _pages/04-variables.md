---
title: 4. Змінні
layout: post
---

У попередньому розділі ми вводили просту математичну операцію 33 + 5 в консолі браузера. Однак, якби ми захотіли використовувати одне і те ж рівняння кілька разів в різних місцях коду, це було б дуже незручно. Саме тому ми використовуємо змінні. Змінна &mdash; це ім'я, якому ми присвоюємо певне значення. Змінні дозволяють нам зберігати фрагменти коду, які ми можемо використовувати пізніше. У змінній можна зберігати, наприклад, результат рівняння, яке ми щойно згадали.

Як створити таку змінну?

```js
var sum = 33 + 5;
```

`var` &mdash; це інструкція, яка визначає змінну. `sum` &mdash; ім'я нашої змінної. `33 + 5` &mdash; це дія, результатом якої буде значення нашої змінної. Коли ми наберемо `var sum = 33 + 5;`, а потім впишемо `sum`, консоль поверне &mdash; `38`. Відтепер, для JavaScript, `sum` &mdash; це те ж саме, що і `38`.

## var

`var` походить від англійського "variable" і означає "змінна". Кожне визначення змінної складається зі слова var, за яким слідує ім'я змінної. Імена змінних можуть складатися з літер, цифр і деяких спеціальних символів, і зазвичай починаються з малої літери. Назви змінних повинні нам про щось говорити. Тобто давайте не будемо називати змінні `xyz`, а краще &mdash; `sum`, `result` тощо. Так нам буде легше орієнтуватися в нашому коді.

Якщо ми присвоїли змінній значення, це не означає, що воно повинно дорівнювати йому назавжди. У нас є можливість перезаписати цю змінну, тобто присвоїти їй нове значення. Просто введіть, наприклад, `sum = 99`. Відтепер для JavaScript `sum` буде означати те ж саме, що і `99`. Коли ми перезаписуємо значення змінної, ми не пишемо `var` поруч з її ім'ям. Ми використовуємо `var` тільки тоді, коли визначаємо змінну, тобто коли записуємо її вперше. Після цього ми просто використовуємо саме ім'я змінної.

## let i const

Сьогодні ми також використовуємо стандарт ES6, який є більш новим стандартом для JavaScript. Згідно з цим стандартом, змінні можна створювати за допомогою `let` або `const`.

Якщо ми створюємо змінну за допомогою `let`, ми можемо присвоювати їй значення будь-яку кількість разів, тобто перезаписувати її \(так само, як `var`, про яку ми говорили вище\). Тоді ми можемо написати такий код:

```js
let sum;
sum = 15;
sum = 20;
```

З іншого боку, коли ми створюємо змінну за допомогою `const`, вона є константою, і ми не можемо присвоїти їй значення, відмінне від того, яке ми присвоїли на самому початку. Спроба присвоїти `const` нове значення призведе до появи помилки в консолі.

```js
const sum = 15;
sum = 20; // виведе помилку в консолі з повідомленням TypeError: Assignment to constant variable.
```

Використання `let` і `const` в коді дуже корисно, тому що ми можемо розрізняти значення, які можна перевизначати, і ті, які повинні залишатися незмінними в усьому коді. Припустимо, наприклад, що у нас є елемент, який завжди однаковий. Для його визначення ми використаємо `const` і таким чином будемо впевнені, що його значення не буде перезаписано.

Через переваги, які дає нам різниця між `let` і `const`, варто використовувати їх у своєму коді замість того, щоб створювати всі змінні за допомогою `var`.

### Завдання

Створи у консолі дві змінні з довільними числами. Одну за допомогою `let`, іншу за допомогою `const`. Спробуй перезаписати обидва значення і подивись, що відобразиться в консолі.
