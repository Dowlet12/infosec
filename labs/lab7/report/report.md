---
## Front matter
title: "Отчет по лабораторной работе №7"
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

- Освоить на практике применение режима однократного гаммирования.

# Задание

- Написание программы
- Зашифровка текста по открытому тексту и известному ключу
- Определение ключа по открытому и зашифрованному тексту

# Теоретическое введение

Гаммирование представляет собой наложение (снятие) на открытые (зашифрованные) данные последовательности элементов других данных, полученной с помощью некоторого криптографического алгоритма, для получения зашифрованных (открытых) данных. Иными словами, наложение гаммы — это сложение её элементов с элементами открытого (закрытого) текста по некоторому фиксированному модулю, значение которого представляет собой известную часть алгоритма шифрования.

Наложение гаммы по сути представляет собой выполнение операции сложения по модулю 2 (XOR) между элементами гаммы и элементами подлежащего сокрытию текста. Такой метод шифрования является симметричным, так как двойное прибавление одной и той же величины по модулю 2 восстанавливает исходное значение, а шифрование и расшифрование выполняется одной и той же программой.

Более подробно о см. в [@lab-theory].

# Выполнение лабораторной работы

Для выполнения лабораторной работы я написал функции для перевода в 16-ричный вид, шифрования и дешифрования, а также импортировал нужные библиотеки (рис. @fig:001).

![Программа, 1](image/1.png){#fig:001 width=70%}

Далее я задал изначальное открытое сообщение, сгенерировал ключ, закодировал сообщение с помощью этого ключа, а также перевел все в 16-ричную систему. После этого раскодировал закодированное сообщение, чтобы проверить правильность работы программы, и определил используемый ключ по открытому сообщению и закодированному сообщению (рис. @fig:002).

![Программа, 2](image/3.png){#fig:002 width=70%}

Полученные сообщения и ключи вывел на экран (рис. @fig:003). Сообщение было успешно закодировано и раскодировано, а найденный ключ совпадает с тем, который был сгенерирован для кодирования.

![Результат запуска программы](image/4.png){#fig:003 width=70%}

# Выводы

В результате лабораторной работы я получил представление о базовых элементах криптографии и освоил на практике применение режима однократного гаммирования, написав программу, позволяющую зашифровывать и расшифровывать тексты и определять использованные для этого ключи.

# Список литературы{.unnumbered}

1. Элементыкриптографии.Однократноегаммирование[Электронныйресурс].URL:
https://esystem.rudn.ru/pluginfile.php/2090284/mod_resource/content/2/007
lab_crypto-gamma.pdf.