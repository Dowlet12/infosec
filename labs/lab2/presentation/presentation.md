---
## Front matter
lang: ru-RU
title: Презентация по лабораторной работе №2
subtitle: Информационная безопасность
author:
  - Байрамгельдыев Довлетмурат
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 16 сентября 2023

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
  * [1032207470@pfur.ru](mailto:1032201654@@pfur.ru)

:::
::::::::::::::

# Вводная часть

## Актуальность

- Упражнения с операциями присвоения прав и тестированием исполнения запретов помогают закрепить основы функционирующей в операционной системе Linux дискреционной модели доступа.
- Предотвращение пересечений между пользовательскими аккаунтами

## Цели и задачи

- Приобретение практических навыков работы в консоли с атрибутами файлов
- Закрепление теоретических основ дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux

## Материалы и методы

- Веб-сервис `GitHub` для работы с репозиториями
- Программа для виртуализации ОС `VirtualBox`
- Процессор `pandoc` для входного формата Markdown
- Результирующие форматы
  - `pdf`
  - `docx`
- Автоматизация процесса создания: `Makefile`

# Ход работы

## Создание пользователя

![](image/1.png){width=70%}

![](image/2.png)

## Поиск сведений об аккаунте

![](image/3.png)

## Создание папки и просмотр прав доступа

![](image/6.png){width=70%}

## Изменение прав доступа

![](image/8.png){width=70%}

## Попытка создания файла

![](image/9.png){width=70%}

## Проверка доступных операций при разных правах доступа

![](image/12.png){width=70%}

## Определение минимальных прав для выполнения операций

![](image/13.png){width=70%}

# Результаты

## Результаты работы

- Закреплены метоы работы дискреционной модели доступа в операционной системе Linux  
- Получены на практике и агрегированы в табличном виде взаимосвязи между правами доступа и доступными операциями 
- Выявлены минимальные права на директорию и на файл для разных операций 