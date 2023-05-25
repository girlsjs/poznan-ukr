# Warsztaty girls.js Poznań / Експедиції у космос, репозиторій girls.js у Познані.

The configuration of book is the same as in the poznan-pl and poznan-eng repositories.

### Конфігурація
Конфігурація сторінки використовує Github Pages та генератор сторінок Jekyll (за замовчуванням доступний на Github Pages).

Github Actions виконують збірку та розгортання за допомогою файлу `.github/jekyll-gh-pages.yml`. Додаткові налаштування шаблону знаходяться в файлі `_config.yml`.

Шаблони Jekyll: [https://jekyllrb.com/docs/pages/](https://jekyllrb.com/docs/pages/)

Усю додаткову інформацію щодо використання шаблону можна знайти у файлі `THEME.md` у папці `docs`.


### Додавання підсторінок

Укорочено:

Посібник розділений на підсторінки у папці `_pages` - це окремі розділи майстерень.

Усі розділи майстерень повинні бути у форматі **markdown** та бути розміщені у папці `_posts`. Крім того, файли повинні мати відповідно оформлену шапку.

```markdown
---
title: Why JS? (Чому JS?)
author: Rita Lyczywek 
date: 2023-04-27
category: programming
layout: post
cover: ../assets/cover.png
---
```

- обов'язково: title (назва), layout (розмітка)
- опціонально: author (автор), date (дата), category (категорія), cover (обкладинка)
Пости автоматично сортуються за номерами розділів - будь ласка, дотримуйтесь цієї конвенції.

