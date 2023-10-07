---
## Front matter
title: "Отчет по лабораторной работе №5"
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

- Изучение механизмов изменения идентификаторов, применения SetUID- и Sticky-битов
- Получение практических навыков работы в консоли с дополнительными атрибутами


# Задание

- Написание программ
- Изменение владельца файлов и прав доступа на файлы
- Установка и снятие Sticky-бита и проверка доступных действий

# Теоретическое введение

Setuid –-- это бит разрешения, который позволяет пользователю запускать исполняемый файл с правами владельца этого файла. Другими словами, использование этого бита позволяет нам поднять привилегии пользователя в случае, если это необходимо. Классический пример использования этого бита в операционной системе это команда sudo.

На месте, где обычно установлен классический бит x (на исполнение), выставлен специальный бит s. Это позволяет обычному пользователю системы выполнять команды с повышенными привилегиями без необходимости входа в систему как root, зная пароль пользователя root.

Принцип работы Setgid очень похож на setuid с отличием, что файл будет запускаться пользователем от имени группы, которая владеет файлом.

Последний специальный бит разрешения – это Sticky Bit . В случае, если этот бит установлен для папки, то файлы в этой папке могут быть удалены только их владельцем. Пример использования этого бита в операционной системе это системная папка /tmp . Эта папка разрешена на запись любому пользователю, но удалять файлы в ней могут только пользователи, являющиеся владельцами этих файлов.

Более подробно о см. в [@lab-theory;@ruvds].

# Выполнение лабораторной работы

В качестве первого шага лабораторной работы осуществил вход от лица пользователя guest и создал файл simpleid.c (рис. @fig:001).

![Создание файла](image/1.png){#fig:001 width=70%}

Далее написал программу, которая выводит информацию об идентификаторах пользователя и группы (рис. @fig:002). Скомпилировал эту программу (рис. @fig:003).

![Программа 1](image/2.png){#fig:002 width=70%}

![Компиляция программы 1](image/3.png){#fig:003 width=70%}

Выполнил эту программу и сравнил ее вывод с результатом работы системной команды id (рис. @fig:004)(рис. @fig:005). 

![Запуск программы 1](image/4.png){#fig:004 width=70%}
![Запуск программы 1](image/5.png){#fig:005 width=70%}

Модифицировал программу, чтобы она выводила также действительные идентификаторы (рис. @fig:006).

![Программа 2](image/6.png){#fig:006 width=70%}

Скомпилировал и запустил модифицированную программу (рис. @fig:007).

![Запуск модифицированной программы](image/7.png){#fig:007 width=70%}

Передал право владения программой суперпользователю и наделил его правом на исполнение программы. Запустили программу и сверили результат с выводом команды id (рис. @fig:008) (рис. @fig:009). Запустил simpleid2 и id. Ничего не изменилось (рис. @fig:010)
![Передача прав и перезапуск программы](image/8.png){#fig:008 width=70%}
![Передача прав и перезапуск программы](image/9.png){#fig:009 width=70%}
![Запустил simpleid2 и id. Ничего не изменилось](image/10.png){#fig:010 width=70%}


Создал новую программу readfile, позволяющую прочесть содержимое файла (рис. @fig:011).

![Программа 3](image/11.png){#fig:011 width=70%}

Скомпилировал ее, а затем поменял владельца файла readfile.c (рис. @fig:012) и изменил права так, чтобы читать файл мог только суперпользователь. Проверил, может ли пользователь guest прочитать файл (рис. @fig:013). Ему было отказано в доступе.

![Смена владельца файла](image/12.png){#fig:012 width=70%}
![Смена прав и проверка](image/13.png){#fig:013 width=70%}

Передал право владения программой суперпользователю и проверили, может ли программа прочитать readfile.c (рис. @fig:014) (рис. @fig:015) и etc/shadow (рис. @fig:016). Действия были выполнены успешно.

![Смена владельца программой и чтение readfile.c](image/14.png){#fig:014 width=70%}
![Смена владельца программой и чтение readfile.c](image/15.png){#fig:015 width=70%}
![Чтение etc/shadow](image/16.png){#fig:016 width=70%}

Проверил, установлен ли Sticky-бит на директории tmp, создал file01.txt и передал категории пользователей "все остальные" право на чтение и запись (рис. @fig:017) (рис. @fig:018).
![Проверка наличия Sticky-бита и создание файла](image/80.png){#fig:017 width=70%}
![Проверка наличия Sticky-бита и создание файла](image/18.png){#fig:018 width=70%}

От лица пользователя guest2 (не являющегося владельцем файла) попробовал прочесть файл и записать туда новые данные (рис. @fig:019) (рис. @fig:020), а также удалить файл (рис. @fig:021).

![Попытка чтения и изменения](image/20.png){#fig:019 width=70%}
![Попытка чтения и изменения](image/22.png){#fig:020 width=70%}
![Попытка удаления](image/24.png){#fig:021 width=70%}

Снял с папки tmp атрибут Sticky (рис. @fig:022) (рис. @fig:023).

![Снятие атрибута Sticky](image/25.png){#fig:022 width=70%}
![Снятие атрибута Sticky](image/26.png){#fig:023 width=70%}

От лица пользователя guest2 попробовал прочесть файл, произвести в него запись и удалить (рис. @fig:024). Удаление файла прошло успешно.

![Чтение, запись и удаление](image/27.png){#fig:024 width=70%}

Установил атрибут Sticky обратно на папку tmp (рис. @fig:025) (рис. @fig:026).

![Установка атрибута Sticky](image/28.png){#fig:025 width=70%}
![Установка атрибута Sticky](image/29.png){#fig:026 width=70%}

# Выводы

В результате лабораторной работы усовершенствовал навыки использования командой строки и изучил SetUID-, SetGID- и Sticky-биты. 

# Список литературы{.unnumbered}

1. Дискреционное разграничение прав в Linux. Исследование влияния дополнитель
ных атрибутов [Электронный ресурс]. URL: https://esystem.rudn.ru/mod/resource/v
iew.php?id=1031377.
2. Использование SETUID, SETGID и Sticky Bit для расширенной настройки прав
доступа в операционных системах Linux [Электронный ресурс]. URL: https://ruvd
s.com/ru/helpcenter/suid-sgid-sticky-bit-linux/.