---
title: 15. Космічні експедиції
layout: post
---

Програмісти змінюють світ. Їхня робота має важливе значення для освоєння космосу. Спробуймо і ми :D

Оскільки нам ще не вдалося нікого відправити в космос, ми скористаємося допомогою та ресурсами NASA.

## Що відбувається на Марсі?

Спочатку нам потрібно отримати ключ доступу. Ми зробимо це тут: [https://api.nasa.gov/index.html\#apply-for-an-api-key](https://api.nasa.gov/index.html#apply-for-an-api-key).

Він допоможе нам отримати доступ до ресурсів, наданих NASA. Їх список можна знайти тут: [https://api.nasa.gov/api.html\#how-do-i-see-my-current-usage?](https://api.nasa.gov/api.html#how-do-i-see-my-current-usage?)

Почнімо з фото дня :\)

При переході за цією адресою [https://api.nasa.gov/planetary/apod?api\_key=DEMO\_KEY](https://api.nasa.gov/planetary/apod?api_key=DEMO_KEY) побачите... об'єкт.

У нас є дата, опис, адреси до фотографій у двох розмірах, тип і назва. Ми створимо сторінку з фотографією дня як фону. З'ясуймо, що сьогодні :D

Для початку завантажуй пакет файлів HTML, CSS та JS, який доступний [ТУТ](https://drive.google.com/open?id=1HEAG_bmuEWIsIX939rXJP3xV-8PFj-0F).

Ми почнемо зі зміни фону тіла на зображення. В CSS для цього використовується `background-image`. Для зміни фону за допомогою JS ми створимо функцію, аргументом якої буде шлях до зображення:

```js
function changeBackground(imageURL) {

}
```

Ми скористаємося вже знайомою нам властивістю `style`. У списку всіх стилів є також `backgroundImage`. Саме йому ми призначимо адресу для нашого зображення.

За замовчуванням вона буде виглядати так:

```js
document.body.style.backgroundImage = "url('img_unicorn.png')";
```

Але адреса нашого зображення зміниться і прийме значення, яке ми введемо як аргумент функції, тому:

```js
function changeBackground(imageURL) {
    document.body.style.backgroundImage = "url('" + imageURL + "')";
}
```

Тепер настав час під'єднатися до API NASA!

Для початку ми створимо змінну з URL-адресою за нашим об'єктом зображення. Замість `DEMO_KEY` ми введемо наш ключ.

```js
let dataURL = 'https://api.nasa.gov/planetary/apod?api_key=DEMO_KEY';
```

Тепер створимо функцію `getPicture`. Усередині неї ми напишемо код, який буде отримувати дані за адресою, вказаною в полі `dataURL`. Для цього ми використаємо `fetch API` &mdash; інструмент для динамічного отримання даних. Це досить новий інструмент, який підтримується новими браузерами.

Ми спробуємо це зробити крок за кроком:

```js
function getPicture() {
    fetch(dataURL)
    .then((resp) => {
        console.log(resp);
    })
}
```
Після виконання `fetch` повертає нам проміс (обіцянку, promise). Проміси дозволяють нам контролювати порядок виконання коду. Якщо проміс виконано, починає виконуватися наступний фрагмент коду \(then\). Якщо за адресою `dataURL` щось є, ми отримуємо доступ до відповіді з цієї сторінки і відображаємо її.

Ще один новий елемент &mdash; стрілки `=>`. Це простіший запис функцій, з якими ми вже знайомі. Наша функція має один аргумент `resp` і цей аргумент відображається в консолі. Викличемо функцію і подивимося на нашу консоль. У ній ми побачимо відповідь від сервера. Конвертуємо її в більш дружній формат, наприклад, JSON.

Найчастіше дані в форматі JSON беруться з сервера у вигляді тексту, а потім конвертуються в об'єкт. Щоб перетворити нашу відповідь від сервера, додамо до неї метод `json()`.

```js
function getPicture() {
    fetch(dataURL)
    .then((resp) => {
        return resp.json();
    })
}
```

Це теж проміс. Як тільки він буде виконаний, ми зможемо показати наш об'єкт. Перевірмо.

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
У нас є наше приміщення! Однак, нас цікавить конкретний елемент: `hdurl`. Пам'ятаєте, як ми відображаємо значення в об'єкті? Саме так: за допомогою посилання на ключ.

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

Також є наш url, який ми повинні використовувати як аргумент у функції `changeBackground`:

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
Ми вже знаємо, яке фото дня?

## До підкорення Марса!

Тепер зробімо крок далі. Дізнаймось, що відбувається на Марсі. Нам допоможе марсохід, який відважно фотографує свої денні пригоди, а дані з цих експедицій ви можете знайти за цим посиланням: [https://api.nasa.gov/mars-photos/api/v1/rovers/curiosity/photos?sol=1000&api\_key=DEMO\_\_KEY](https://api.nasa.gov/mars-photos/api/v1/rovers/curiosity/photos?sol=1000&api_key=DEMO__KEY)

Подивіться, тепер над посиланням чекає набагато більше об'єктів, ніж було хвилину тому. Скористаймось ними!

Почнемо з присвоєння нашої URL-адреси змінній:

```js
let urlMars = "https://api.nasa.gov/mars-photos/api/v1/rovers/curiosity/photos?sol=1000&apikey=DEMO_KEY";
```

Створимо нову функцію, яка буде використовувати знайомий інструмент `fetch API`:

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

Викличемо функцію і подивимося, що станеться в консолі. У нас є об'єкт з ключем `photos` \(може знадобитися деякий час, щоб щось з'явилося в консолі\). Давайте перевіримо, що знаходиться всередині, тобто під ключем `photos`:

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

Всередині ми маємо масив об'єктів. Тепер перевіримо, скільки в ньому об'єктів:

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

Дуже багато! Перевіримо, що знаходиться всередині першого об'єкта:

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

Це вже ближче до наших очікувань. З цього можна зробити щось подібне :\)

У нас є об'єкт, всередині якого знаходиться ключ `img_src` з адресою зображення. Ми його використаємо. Зробімо галерею на нашій сторінці. Вона буде знаходитися в тегу `div` з ідентифікатором `content`. Отже, створимо змінну:

```js
let gallery = document.getElementById('content');
```

Тепер створімо функцію `createGallery` з аргументом `dataList`. Це буде той самий довгий масив, який ми витягли з `data.photos` :

```js
function createGallery(dataList) {
}
```

Тепер створімо функцію `createGallery` з аргументом `dataList`. Це буде той самий довгий масив, який ми витягли з `data.photos` :

Усередині функції ми використаємо цикл, щоб створити 9 зображень і додати їх на сторінку. У HTML ми відобразимо зображення за допомогою тегу `img`:

```markdown
<img src="adres_obrazka" class="klasa/klasy" alt="co_sie_wyswietli_jesli pod danym adresem nie ma obrazka">
```

Ось так це буде виглядати в HTML. А як це зробити за допомогою JS? Почнемо з циклу, який повториться 9 разів:

```js
function createGallery(dataList) {
    for(let i = 0; i < 9; i++) {

    }
}
```

Кожного разу ми будемо створювати новий елемент. Присвоїмо його змінній `img`. Створюємо новий елемент за допомогою:

```js
document.createElement('tag_name');
```

У нашому випадку ім'я тега буде `img`, тобто:

```js
function createGallery(dataList) {
    for(let i=0; i < 9; i++) {
        let img = document.createElement('img');
    }
}
```

Наступним кроком буде вставка нового елемента в div `content`. Це робиться за допомогою методу `appendChild('inserted_element_name')`.

```js
function createGallery(dataList) {
    for(let i=0; i < 9; i++) {
        let img = document.createElement('img');
        gallery.appendChild(img);
    }
}
```

Давайте перевіримо наш сайт.

Наші шляхи до зображень відсутні. Повернемося до функції `getMarsPictures`. Тут у нас був масив з декількома об'єктами всередині, в якому був потрібний нам `img_src`. Присвоїмо наш масив змінній:

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

Тут у нас є список, який ми будемо використовувати у функції `createGallery`. Отже, викличемо `createGallery` з цим аргументом всередині функції `getMarsPicture`:

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

Гаразд, але що ховається під нашим `pictureList`? Перевіримо це за допомогою `console.log`. У функції `createGallery` виведемо в консоль наш аргумент `dataList`. Тепер викличемо функцію `getMarsPicture`. У ній ми також викликаємо функцію `createGallery`:

```js
function createGallery(dataList) {
    for(let i=0; i < 9; i++) {
        let img = document.createElement('img');
        gallery.appendChild(img);
        console.log(dataList);
    }
}
```

У нас є 9 масивів, де знаходяться наші об'єкти. І нам потрібен лише 1 об'єкт у кожному циклі. Об'єкт, індекс якого збігається з нашим, тому виводитимемо лише об'єкти з індексом, рівним `i`:

```js
function createGallery(dataList) {
    for(let i=0; i < 9; i++) {
        let img = document.createElement('img');
        gallery.appendChild(img);
        console.log(dataList[i]);
    }
}
```

Ми вже ближче &mdash; у нас є 9 об'єктів. І нам потрібне лише значення, яке ховається під `img_src`, тому виводимо його:

```js
function createGallery(dataList) {
    for(let i=0; i < 9; i++) {
        let img = document.createElement('img');
        gallery.appendChild(img);
        console.log(dataList[i].img_src);
    }
}
```

Все краще і краще. Тепер, замість того, щоб виводити його, давайте присвоїмо його змінній і перемістимо перед додаванням `img` до `gallery`:

```js
function createGallery(dataList) {
    for(let i=0; i < 9; i++) {
        let img = document.createElement('img');
        let imgPath = dataList[i].img_src;
        gallery.appendChild(img);
    }
}
```

Як тепер додати `imgPath` до нашого елемента `img`? За допомогою властивості `rc`. Вона схожа на властивість `style`. Нам потрібно присвоїти їй значення:

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

Тепер давайте викличемо функцію `getMarsPictures` і подивимося, що відбувається на Марсі!
