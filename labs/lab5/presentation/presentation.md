---
## Front matter
lang: ru-RU
title: Презентация по лабораторной работе №5
subtitle: Информационная безопасность
author:
  - Байрамгельдыев Довлетмурат
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 5 октября 2023

## i18n babel
babel-lang: russian
babel-otherlangs: english

## Formatting pdf
toc: false
toc-title: Содержание
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'
---

# Информация

## Докладчик

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

  * Байрамгельдыев Довлетмурат
  * студент 4 курса группы НФИбд-01-20
  * ст. б. 1032207470
  * Российский университет дружбы народов
  * [1032207470@pfur.ru](mailto:1032207470@@pfur.ru)

:::
::::::::::::::

# Вводная часть

## Актуальность

- Обеспечение безопасности

## Цели и задачи

- Приобретение практических навыков работы в консоли с дополнительными атрибутами файлов
- Изучение механизмов смены идентификатора процессов пользователей
- Изучение SetUID-, SetGID- и Sticky-битов

## Материалы и методы

- Веб-сервис `GitHub` для работы с репозиториями
- Программа для виртуализации ОС `VirtualBox`
- Процессор `pandoc` для входного формата Markdown
- Результирующие форматы
  - `pdf`
  - `docx`
- Автоматизация процесса создания: `Makefile`

# Ход работы

## Написание программы 1

![](image/2.png){width=70%}

## Запуск программы 1

![](image/4.png)

![](image/5.png)

## Модификация программы

![](image/6.png){width=70%}

## Запуск модифицированной программы

![](image/7.png){width=70%}

## Изменение владельца файла

![](image/8.png){width=70%}
![](image/9.png){width=70%}
![](image/10.png){width=70%}

## Написание программы 3

![](image/11.png){width=70%}

## Изменение прав доступа

![](image/12.png){width=70%}

![](image/13.png){width=70%}

## Попытка чтения, изменения и удаления файла

![](image/18.png){width=70%}
![](image/22.png){width=70%}

![](image/24.png){width=70%}

## Снятие Sticky-бита

![](image/25.png){width=70%}
![](image/26.png){width=70%}

## Повторная попытка чтения, записи и удаления файла

![](image/27.png){width=70%}

# Результаты

## Результаты работы

- Получены навыки работы с дополнительными атрибутами файлов
- Усовершенствованы навыки работы с механизмами смены владельца
- Рассмотрены принципы работы SetUID-, SetGID- и Sticky-битов- 