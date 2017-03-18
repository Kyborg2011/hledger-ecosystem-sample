# hledger-ecosystem-sample (пример работы с hledger для ведения бухгалтерии для бизнеса и/или личного бюджета)

## Установка

После [скачивания](http://hledger.org/download.html) и установки **hledger** необходимо привести файл `~/.hledger.journal` в следующий вид:

`; journal created 2016-12-20 by hledger`

`include /full/path/to/hledger-ecosystem-sample/main.journal`

Чтобы пользоваться hledger также в качестве персонального ведения счетов (бухгалтерии), переименуйте файлы:

**personal.journal ~~.example~~**

**config-personal.txt ~~.example~~**

## Некоторые термины

- **Accounting** — tracking the flow of valuable commodities, such as money or time. It clarifies activity, priorities, obligations, opportunities. It can **reduce stress** and even be enjoyable.
- **Двойна́я за́пись** — способ ведения [бухгалтерского учёта](https://ru.wikipedia.org/wiki/%D0%91%D1%83%D1%85%D0%B3%D0%B0%D0%BB%D1%82%D0%B5%D1%80%D1%81%D0%BA%D0%B8%D0%B9_%D1%83%D1%87%D1%91%D1%82), при котором каждое изменение состояния средств организации отражается по крайней мере на двух [бухгалтерских счетах](https://ru.wikipedia.org/wiki/%D0%91%D1%83%D1%85%D0%B3%D0%B0%D0%BB%D1%82%D0%B5%D1%80%D1%81%D0%BA%D0%B8%D0%B9_%D1%81%D1%87%D1%91%D1%82), обеспечивая общий баланс.
- **Де́бет** и **кре́дит** — стандартизированные методологические приёмы [бухгалтерского учёта](https://ru.wikipedia.org/wiki/%D0%91%D1%83%D1%85%D0%B3%D0%B0%D0%BB%D1%82%D0%B5%D1%80%D1%81%D0%BA%D0%B8%D0%B9_%D1%83%D1%87%D1%91%D1%82). Они раскрывают возможности хозяйственных и других процессов и их направление, и они же ставят границы этим возможностям
- **Активы = Пассивы**
- **Hledger** — an accounting program, for tracking money, time, or other commodities, on unix, mac and windows. Plain text accounting system.

## Пример построения баланса предприятия

![balance sheet example](https://habrastorage.org/files/372/e92/eb7/372e92eb757b4ec39d0aeadb90b54f12.png)

> stockholders' equity - капитал ***
>
> assets - счета ***
>
> liabilities - "мы должны" ***
>
> retained earnings - нераспределенные доходы ***

## Примеры отчетов:

- [Баланс (простая форма):](csv-examples/balance-simple.csv)
  `hledger balance -VB --format "%20(account) %12(total)" -o /full/path/to/file.csv`

- [Квартальный баланс](csv-examples/balance-quarterly.csv):
  `hledger balance -VB --quarterly income expenses -E --cumulative -o /full/path/to/file.csv`

- [Счета (текущее состояние)](csv-examples/balance-changes.csv):
  `hledger balance --format "%20(account) %12(total)" -o /full/path/to/file.csv`

- [Вывод полного списка операций](csv-examples/whole-journal.csv): ``hledger print -B -o /full/path/to/file.csv``

  *<p align="right">и многое другое можно делать с этой штукой...</div>*

## Примечания:

1. `-VB` используется для отображения баланса в одной валюте (**UAH - Украинская гривня**). Для валютных операций используются гибкие курсы обмена различных *commodities* - с возможностью задавать различные курсы даже, при необходимости, на любую конкретную дату. **Пример:** `P 2016/1/1 $ UAH26.70`

## RTFM

- **[Документация *hledger*](http://hledger.org/manual.html):**
- **[Plain Text Accounting](http://plaintextaccounting.org/)**
- https://en.wikipedia.org/wiki/Partnership_accounting
- https://en.wikipedia.org/wiki/Balance_sheet
