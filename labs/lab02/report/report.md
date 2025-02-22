---
## Front matter
title: "Лабораторная работа №2"
subtitle: "Исследование протокола TCP и алгоритма управления очередью RED"
author: "Алиева Милена Арифовна"

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
## Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
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

Исследовать протокол TCP и алгоритм управления очередью RED.

# Задание

1. Выполнить пример с дисциплиной RED;
2. Изменить в модели на узле s1 тип протокола TCP с Reno на NewReno, затем на Vegas. Сравнить и пояснить результаты;
3. Внести изменения при отображении окон с графиками (изменить цвет фона, цвет траекторий, подписи к осям, подпись траектории в легенде).

# Выполнение лабораторной работы

1.  Выполним построение сети в соответствии с описанием:
- сеть состоит из 6 узлов;
- между всеми узлами установлено дуплексное соединение с различными пропускной способностью и задержкой 10 мс;
- узел r1 использует очередь с дисциплиной RED для накопления пакетов, максимальный размер которой составляет 25;
- TCP-источники на узлах s1 и s2 подключаются к TCP-приёмнику на узле s3;
генераторы трафика FTP прикреплены к TCP-агентам.
Теперь разработаем сценарий, реализующий модель согласно описанию, чтобы построить в Xgraph график изменения TCP-окна, график изменения длины очереди и средней длины очереди.. (рис. [-@fig:001]).

![Редактирование файла](image/1.jpg){#fig:001 width=70%}

2. После запуска кода получаем график изменения TCP-окна (рис. [-@fig:002]), а также график изменения длины очереди и средней длины очереди (рис. [-@fig:003]).

![График изменения TCP-окна](image/2.jpg){#fig:002 width=70%}

![График изменения длины очереди и средней длины очереди](image/3.jpg){#fig:003 width=70%}

3. Теперь изменим тип Reno на NewReno (рис. [-@fig:004]).

![Меняем тип Reno на NewReno](image/4.jpg){#fig:004 width=70%}

4. После запуска кода получаем график изменения TCP-окна (рис. [-@fig:005]), а также график изменения длины очереди и средней длины очереди (рис. [-@fig:006]). Видим, что значение средней длины очереди находится в пределах от 2 до 4, а максимальное значение длины равно 14, как и на предыдущем графике. В обоих алгоритмах размер окна увеличивается до тех пор, пока не произойдёт потеря сегмента.

![График изменения TCP-окна](image/5.jpg){#fig:005 width=70%}

![График изменения длины очереди и средней длины очереди](image/6.jpg){#fig:006 width=70%}

5. Изменим тип Reno на Vegas (рис. [-@fig:007]).

![Меняем тип Reno на Vegas](image/7.jpg){#fig:007 width=70%}

6. После запуска кода получаем график изменения TCP-окна (рис. [-@fig:008]), а также график изменения длины очереди и средней длины очереди (рис. [-@fig:009]). Видим, что средняя длина очереди опять находится также в диапазоне от 2 до 4, а максимальная длина достигает значения 14. Довольно сильные отличия можно заметить по графикам динамики размера окна, так как при Vegas максимальный размер окна составляет 20, а не 34, как в предыдущих графиках. Это происходит по той причине, что TCP Vegas обнаруживает перегрузку в сети до того, как случайно теряется пакет, и мгновенно уменьшается размер окна, получается, что TCP Vegas обрабатывает перегрузку без каких-либо потерь пакета.

![График изменения TCP-окна](image/8.jpg){#fig:008 width=70%}

![График изменения длины очереди и средней длины очереди](image/9.jpg){#fig:009 width=70%}

7. Внесем изменения при отображении окон с графиками, изменим цвет фона, цвет траекторий, подписи к осям и подпись траектории в легенде.

![Изменение цвета](image/10.jpg){#fig:010 width=70%}

![Изменение цвета](image/11.jpg){#fig:011 width=70%}

8. После запуска кода получаем график изменения TCP-окна (рис. [-@fig:012]), а также график изменения длины очереди и средней длины очереди (рис. [-@fig:013]). 

![График изменения TCP-окна](image/12.jpg){#fig:012 width=70%}

![График изменения длины очереди и средней длины очереди](image/13.jpg){#fig:013 width=70%}

# Выводы

В процессе выполнения данной лабораторной работы я исследовала протокол TCP и алгоритм управления очередью RED.

