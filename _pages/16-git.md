---
title: 16. GIT
layout: post
---


GIT to narzędzie do kontrolowania zmian w projekcie.  Tworzy on historię i umożliwia sprawną współpracę między wieloma programistami. By korzystać z GITa warto poznań kilka pojęć:

**terminal** - aplikacja tekstowa służąca do przeglądania, obsługi i operowania plikami na Twoim komputerze. Jak go uruchomić?

Windows: Start → Wszystkie programy → Akcesoria → Wiersz poleceń

Mac OS: Aplikacje → Narzędzia → Terminal

Linux: Aplikacje → Akcesoria → Terminal

**repozytorium** - miejsce, gdzie znajduje się nasza aplikacja. To historię tego folderu obserwuje GIT. Na komputerze można mieć kilka takich folderów.

**commit** - paczka zmian, która jest częścią historii danego repozytorium. W trakcie pracy nad projektem tworzysz kolejne commity i zarządzasz nimi

**branch** - gałąź Twojego projektu. Programiści pracują na osobnych branchach, np. nad różnymi funkcjonalnościami strony, po czym łączą je w jedną całość.

### Instalacja GITa:

[https://git-scm.com/downloads](https://git-scm.com/downloads)

### Podstawowe komendy:

* **git init** - inicjalizuje repozytorium GIT w danym katalogu

* **git add nazwa\_pliku** - dodaje zmiany we wskazanym pliku do commita

* **git commit -m "treść\_commita"** - dodaje opis do commita

* **git add origin adres\_repozytorium**, np. [https://github.com/username/moje-repozytorium.git](https://github.com/username/moje-repozytorium.git) - ustawia konkretny adres zdalnego repozytorium jako główne repozytorium

* **git push origin master** - wysłanie zmian do branacha zdalnego

* **git checkout nazwa\_brancha** - zmienia aktywny branch na wybrany przez użytkownika

* **git pull** - pobranie zmian ze zdalnego repozytorium

### Zadanie:

1. Zainstaluj na swoim komputerze GITa zgodnie z instrukcją na stronie:[ https://git-scm.com/book/pl/v1/Pierwsze-kroki-Instalacja-Git](https://git-scm.com/book/pl/v1/Pierwsze-kroki-Instalacja-Git).
2. Załóż konto na [github.com](https://github.com/).
3. Na GitHubie stwórz nowe repozytorium.
4. W katalogu ze stroną "A jednak się kręci" zainicjuj repozytorium GITa.
5. Wyślij pliki z tego folderu do zdalnego repozytorium na GitHubie.

## GitHub Pages

GitHub oferuje także hosting Twoich stron.

### Zadanie:

1. Stwórz na GitHub nową organizację lub repozytorium.
2. Na podstawie instrukcji zamieszczonej na stronie: [https://pages.github.com/](https://pages.github.com/) zamieść stronę "Wyprawy Kosmiczne" na GitHub Pages. 
3. Wyświetl nową stronę w przeglądarce.

**Podpowiedź:**

[O Github Pages krok po kroku](https://www.flynerd.pl/2018/02/opublikowac-strone-internetowa-github-pages-krok-kroku.html)