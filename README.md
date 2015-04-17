# Парсер

Парсер данных с [МосЭкоМониторинга](http://www.mosecom.ru/air/air-today/). Парсит показатели загрязнения воздуха газамивредными по станциям. На данный момент скачивается статистика только по годам. Данные по одному показателю выгружаются в CSV где по горизонати - названия газов, а по вертикали - названия станций.

Данные скачиваются от [сюда](http://www.mosecom.ru/air/air-today/). Здесьже есть геометрия для метеостанций.

## Парсинг

На данный момент парсинг осуществляется в ручную, достаточно запустить html страницу `parse.html`.

## Импорт в базу

Импорт осуществляется следующими командами. Подразумевается, что станции уже загружены.

```sh
thor data:csv:import ../parse-mos-eco-monitoring/results_2014/avg_pdk_ss.csv Place moseco_id
thor data:csv:import ../parse-mos-eco-monitoring/results_2014/max_pdk_ss.csv Place moseco_id
thor data:csv:import ../parse-mos-eco-monitoring/results_2014/raise_pdk_ss.csv Place moseco_id
```

## Коды показателей
Показатель | Код
-----------|-----
Среднее значение (в мг / куб. м)                      | avg_mg
Среднее значение (в ПДК с.с.)                         | avg_pdk_ss
Максимальное разовое значение (в мг / куб. м)         | max_mg
Максимальное разовое значение (в ПДК м.р.)            | max_pdk
Максимальное разовое значение — дата и время          | 
Максимальное среднесуточное значение (в мг / куб. м)  | max_mg_ss
Максимальное среднесуточное значение (в ПДК с.с.)     | max_pdk_ss
Максимальное среднесуточное значение — дата           | 
Превышение ПДК м.р. (часы)                            | raise_pdk_mr
Наибольшая длительность непрерывного превышения ПДК м.р. (часы)  | raise_time_pdk
Превышение ПДК с.с. (сутки)                           | raise_pdk_ss
Наибольшая длительность непрерывного превышения ПДК с.с. (сутки) | raise_time_pdk_ss

На данный момент нам актуальны три: `avg_pdk_ss`, `max_pdk_ss` и `raise_pdk_ss`.

## Коды веществ

Вещество | Код
---------|-----
Аммиак                            | amiak
Азотистая кислота                 | azotistaya-kislota
Бензол                            | benzol
Взвешенные частицы менее 10 мкм   | chastitsi-10
Взвешенные частицы менее 2.5 мкм  | chastitsi-2
Диоксид азота                     | dioxid-seri
Диоксид серы                      | dioxid-seri
Метаксилол                        | metaksilol
Метан                             | metan
Нафталин                          | naftalin
Неметановые углеводороды          | non-metan-ugevodorodi
Оксид азота                       | oxid-azota
Оксид углерода                    | oxid-ugleroda
Озон                              | ozon
Параксилол                        | paraxilol
Стирол                            | stirol
Сероводород                       | serovodorod
Толуол                            | toluol
Углеводороды суммарные            | uglevodorodi
Формальдегид                      | formaldegid
Фенол                             | fenol
Этилбензол                        | etilbenzol
SO2_OPSIS                         | SO2_OPSIS
H2S                               | H2S

