---
## Front matter
title: "Лабораторная работа №17"
subtitle: "Задания для самостоятельной работы"
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

Реализовать с помощью gpss модели работы вычислительного центра, аэропорта и морского порта. [@lab]

# Задание

Реализовать с помощью gpss:

- модель работы вычислительного центра
- модель работы аэропорта
- модель работы морского порта

# Выполнение лабораторной работы

1) На вычислительном центре в обработку принимаются три класса заданий А, В и С. Исходя из наличия оперативной памяти ЭВМ задания классов А и В могут решаться одновременно, а задания класса С монополизируют ЭВМ. Задачи класса С загружаются в ЭВМ, если она полностью свободна. Задачи классов А и В могут дозагружаться к решающей задаче. Задается хранилище ram на две заявки. Затем записаны три блока: первые два обрабатывают задания класса A и B, используя один элемент ram, а третий обрабатывает задания класса C, используя два элемента ram. 

Построим модель (рис. [-@fig:001]).

![Модель работы вычислительного центра](image/1.jpg){#fig:001 width=70%}

Смоделируем работу ЭВМ за 80 ч. и определим её загрузку. После запуска симуляции получаем отчёт (рис. [-@fig:002], [-@fig:003]).

![Отчёт по модели работы вычислительного центра](image/2.jpg){#fig:002 width=70%}

![Отчёт по модели работы вычислительного центра](image/3.jpg){#fig:003 width=70%}

Видим, что загруженность системы равна 0.994.

2) Самолёты прибывают для посадки в район аэропорта каждые $10 \pm 5$ мин. Если взлетно-посадочная полоса свободна, прибывший самолёт получает разрешение на посадку. Если полоса занята, самолет выполняет полет по кругу и возвращается в аэропорт каждые 5 мин. Если после пятого круга самолет не получает разрешения на посадку, он отправляется на запасной аэродром. В аэропорту через каждые $10 \pm 2$ мин к взлетно -посадочной полосе выруливают готовые к взлёту самолёты и получают разрешение на взлёт, если полоса свободна. Для взлета и посадки самолёты занимают полосу ровно на 2 мин. Если при свободной полосе одновременно один самолёт прибывает для посадки, а другой - для взлёта, то полоса предоставляется взлетающей машине.

Требуется:
- выполнить моделирование работы аэропорта в течение суток;
- подсчитать количество самолётов, которые взлетели, сели и были направлены на запасной аэродром;
- определить коэффициент загрузки взлетно-посадочной полосы.

Блок для влетающих самолетов имеет приоритет 2, для прилетающий приоритет 1, далее происходит проверка: если полоса пустая, то заявка просто отрабатывается, если нет, то происходит переход в блок ожидания. При ожидании заявка проходит в цикле 5 раз, каждый раз проверяется не освободилась ли полоса, если освободилась - переход в блок обработки, если нет - самолет обрабатывается дополнительным обработчиком отправления в запасной аэродром. Построим модель (рис. [-@fig:004]).

![Модель работы аэропорта](image/4.jpg){#fig:004 width=70%}

Время моделирования задаем в минутах - 1440. После запуска симуляции получаем отчёт (рис. [-@fig:005], [-@fig:006]).

![Отчёт по модели работы аэропорта](image/5.jpg){#fig:005 width=90%}

![Отчёт по модели работы аэропорта](image/6.jpg){#fig:006 width=90%}

Видим, что взлетело 142 самолета, село 146, а в запасной аэропорт отправилось 0. Коэффициент загрузки полосы равняется 0.4, получается, что полоса большую часть времени не используется.

3) Морские суда прибывают в порт каждые $[\alpha \pm \delta]$ часов. В порту имеется N причалов. Каждый корабль по длине занимает M причалов и находится в порту $[b \pm \varepsilon]$ часов.
Требуется построить GPSS-модель для анализа работы морского порта в течение полугода, определить оптимальное количество причалов для эффективной работы порта.

Рассмотрим два варианта исходных данных:
1) $a = 20$ ч, $\delta = 5$ ч, $b = 10$ ч, $\varepsilon = 3$ ч, $N = 10$, $M = 3$;
2) $a = 30$ ч, $\delta = 10$ ч, $b = 8$ ч, $\varepsilon = 4$ ч, $N = 6$, $M = 2$.

**Первый вариант модели**:

Построим модель (рис. [-@fig:007]).

![Модель работы морского порта](image/7.jpg){#fig:007 width=70%}

После запуска симуляции получаем отчёт (рис. [-@fig:008]).

![Отчет по модели работы морского порта](image/8.jpg){#fig:008 width=90%}

При запуске с 10 причалами видно, что судна обрабатываются быстрее, чем успевают приходить новые, так как очередь не набирается. Соответственно попробуем уменьшить число причалов. Постепенно понижая, видим, что полезность возрастает. Тогда установим наименьшее возможное число причалов - 3 (рис. [-@fig:009]), получаем оптимальный результат, что видно на отчете (рис. [-@fig:010]).

![Модель работы морского порта с оптимальным количеством причалов](image/9.jpg){#fig:009 width=90%}

![Отчет по модели работы морского порта с оптимальным количеством причалов](image/10.jpg){#fig:010 width=90%}

**Второй вариант модели**

Построим модель (рис. [-@fig:011]).

![Модель работы морского порта](image/11.jpg){#fig:011 width=70%}

После запуска симуляции получаем отчёт (рис. [-@fig:012]).

![Отчет по модели работы морского порта](image/12.jpg){#fig:012 width=90%}

При запуске с 6 причалами видно, что судна обрабатываются быстрее, чем успевают приходить новые, так как очередь не набирается. Соответственно попробуем уменьшить число причалов. Постепенно понижая, видим, что полезность возрастает. Тогда установим наименьшее возможное число причалов - 2 (рис. [-@fig:013]), получаем оптимальный результат, что видно из отчета (рис. [-@fig:014]).

![Модель работы морского порта с оптимальным количеством причалов](image/13.jpg){#fig:013 width=90%}

![Отчет по модели работы морского порта с оптимальным количеством причалов](image/14.jpg){#fig:014 width=90%}

# Выводы

В результате выполнения данной лабораторной работы я реализовала с помощью gpss модель работы вычислительного центра, модель работы аэропорта, модель работы морского порта.

# Список литературы 

