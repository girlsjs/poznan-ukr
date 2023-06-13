---
title: 14. Ти об'єкт
layout: post
---
...тому що все є об'єктом ;\) Це ще один тип даних. Виглядає він наступним чином:

```js
let variable = {
    key: value,
    key2: value2,
    key3: value3
}
```

Як бачите, нагадує масив. За винятком того, що в масиві дуже важливий порядок елементів, які в ньому знаходяться. У випадку з об'єктами ключовими елементами є... ключі ;\)

Якби ми хотіли представити людину як об'єкт, ми могли б зробити це наступним чином:

```js
let person = {
    name: 'Natalia',
    age: 27,
    hobby: ['swimming', 'cycling', 'fantasy books']
}
```

Щоб звернутися до елемента об'єкта, потрібно звернутися до його ключа, наприклад:

```js
person.hobby;
```

Ми можемо додавати нові елементи до вже наявного об'єкта:

```js
person.city = 'Poznań';
console.log(person);
```

Ми також можемо їх видаляти:

```js
delete person.hobby;
```

Іноді в об'єкті може бути ще один об'єкт:

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

Як вивести ім'я сестри?

```js
person.family.sister;
```
