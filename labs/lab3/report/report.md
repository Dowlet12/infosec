---
## Front matter
title: "Отчет по лабораторной работе №3"
subtitle: "Информационная безопасность"
author: "Байрамгельдыев Довлетмурат"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
  - spelling=modern
  - babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: Times New Roman
romanfont: Times New Roman
sansfont: DejaVu Sans
monofont: DejaVu Sans Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

- Получение практических навыков работы в консоли с атрибутами файлов для
групп пользователей.

# Задание

- Создание двух учетных записей
- Объединение пользователей в одну группу
- Изменение прав доступа одним пользователем и проверка возможных в рамках заданных прав доступа действий другим пользователем
- Заполнение таблиц

# Теоретическое введение

Каждый файл или каталог имеет права доступа, обозначаемые комбинацией
букв латинского (обозначает разрешение) алфавита и знаков –(обозначает отсут
ствие разрешения). Для файла: r — разрешено чтение, w — разрешена запись, x —
разрешено выполнение,для каталога: r — разрешён просмотр списка входящих
файлов, w — разрешены создание и удаление файлов, x — разрешён доступ в
каталоги естьвозможностьсделатьеготекущим,-—праводоступа отсутствует.В
сведениях о файле или каталоге указываются:–тип файла (символ (-) обозначает
файл, а символ (d) — каталог);
– права для владельца файла;
– права для членов группы;
– права для всех остальных [1] [2].

# Выполнение лабораторной работы

В первом шаге лабораторной работы перешел в режим sudo, дающий больше прав, создал учетную запись guest2 с помощью команды useradd и добавил пользователя guest2 в группу guest (рис. @fig:001).

![Создание учетных записей](image/1.png){#fig:001 width=70%}

Далее осуществили вход в систему от двух пользователей на разных терминалах, определил в какой директории нахожусь, командой pwd и получил информацию о группах, в которые входит каждый пользователь, с помощью команд id и groups (рис. @fig:002) {#fig:003 width=70%}.

![Вход и информация о группах](image/2.png){#fig:002 width=70%}
![Вход и информация о группах](image/3.png){#fig:003 width=70%}

Посмотрел содержимое файла etc/group и увидел, что данные о группах пользователей совпадают с полученными ранее (рис. @fig:004).

![Содержимое файла etc/group](image/4.png){#fig:004 width=70%}

Зарегистрировал второго пользователя в группе guest командой newgrp (рис. @fig:005).

![Регистрация guest2 в группе guest](image/5.png){#fig:005 width=70%}

Дал всем пользователям группы все права доступа к директории /home/guest (рис. @fig:006).

![Изменение прав доступа к /home/guest](image/6.png){#fig:006 width=70%}

Создал папку dir1 и сняли с нее все атрибуты командой chmod 000. Проверил успешность действий командой ls -l (рис. @fig:007).

![Изменение и просмотр прав доступа папки dir1](image/7.png){#fig:007 width=70%}

Снял с ранее созданного файла file1 все атрибуты (рис. @fig:008).

![Снятие атрибутов с file1](image/8.png){#fig:008 width=70%}

Комбинируя разные права доступа к директории и к файлу от имени guest, проверил какие действия доступны для разных прав доступа от имени guest2 (рис. @fig:009).

![Проверка доступных действий](image/9.png){#fig:009 width=70%}

Заполнил таблицу полученной информацией (рис. @fig:010).

![Установленные права и разрешенные действия, 2](image/10.png){#fig:010 width=70%}

Проанализировал полученную таблицу и определил, какие минимальные права доступа на директорию и на файл необходимы для различных операций (рис. @fig:012). 

![Минимальные права для совершения операций](image/11.png){#fig:012 width=70%}

# Выводы

В результате лабораторной работы мной были получены навыки работы с атрибутами файлов, закреплены знания о правах доступа в системах на базе ОС Linux, а также были выявлены минимальные необходимые права доступа для выполнения операций над файлами и директориями.

# Список литературы{.unnumbered}

1. Робачевский А., Немнюгин С., Стесик О. Операционная система UNIX. 2-е
изд. БХВ-Петербург, 2010. 656 с.
2. Таненбаум Э., Бос Х. Современные операционные системы. 4-е изд. СПб.:
Питер, 2015. 1120 с.3. 