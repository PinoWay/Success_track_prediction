# Модель прогнозирования успешного прохождения трека обучения
В Онлайн-Университете проходят курсы. Каждый курс является уникальным учебным блоком, который охватывает определенную тематику или набор знаний.
Обучающиеся (или студенты) регистрируются и учатся на этих курсах. Один студент может быть записан на один или несколько курсов, а один курс может иметь множество студентов.

Содержание каждого курса разделено на сущности. Сущность — это структурная единица курса, которая может представлять собой лекцию, практическое задание, тест, видео или любой другой материал или действие, помогающее студенту усвоить материал курса.
Каждая сущность имеет тип. Этот тип определяет формат или характеристику сущности. Например, типы сущностей могут включать в себя: лекции, видеоматериалы, тесты, практические работы и так далее.
После прохождения каждой сущности студенту присваивается статус "прошел" или "не прошел".

Для определенных типов сущностей, таких как тесты или практические задания, могут быть предоставлены результаты, например, в виде оценок или отзывов.

В настоящей работе была разработана модель, которая прогнозирует прохождение стундентами обучающий треков целиком.

## Структура репозитория
- data
    - main_data.csv - файл с данными о студентах, курсах, сущностях.
    - order_dict.pkl - словарь хронологического следования сущностей (см. data_analysis.ipynb).
    - relation_dict.pkl - словарь соответсвий сущностей (см. data_analysis.ipynb)ю
- data_analysis.ipynb - ноутбук с анализом и подготовкой данных и построением модели для определения пройдет ли студент трек целиком или нет.
- final_pipe.pkl - финальный пайплайн подготовки данных и предсказания целевой метрики.

## Результаты моделирования
В результате анализа данных было показано, что для хорошей степени классификации можно использовать информацию только из первых 17 сущностей (из 104 возможных). Для предсказания прохождения курса целиком протестировались различные модели. Лучшей предсказательной способностью (roc_auc=0.87) на тестовом наборе данных обладает модель XGBoost. Итоговый пайплайн подготовки данных и прогнозирования получен именно для этой модели.