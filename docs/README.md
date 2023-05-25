# Wyprawy kosmiczne repozytorium girls.js Poznań 


### Konfiguracja
Konfiguracja strony korzysta z Github Pages oraz generatora stron Jekyll (dostępny domyślnie z Github Pages).

Github Actions wykonują build & deploy w pliku `.github/jekyll-gh-pages.yml`. Dodatkowo ustawienia szablonu znajdują się w `_config.yml`. 

Szablony jekyll: https://jekyllrb.com/docs/pages/

Wszystkie dodatkowe informacje jak korzystać z szablonu znajdują się w pliku `THEME.md` w folderze docs.


### Dodawanie podstron

W skrócie:

Podręcznik dzieli się na podstrony `_pages` - kolejne rozdziały warsztatów. 

Wszystkie chaptery warsztatów muszą być w formacie **markdown** i być umieszczone w folderze `_posts`. Dodatkowo pliki muszą posiadać odpowiednią sformatowany nagłówek.

```md

---
title: Why JS?
author: Rita Lyczywek
date: 2023-04-27 
category: programming
layout: post
cover: ../assets/cover.png
---

```

- obowiązkowo: title, layout
- opcjonalnie: author, date, category, cover


Posty są sortowane automatycznie wg numerów chapterów - zachowaj konwencję
