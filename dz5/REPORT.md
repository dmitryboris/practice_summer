# Отчёт по 5 д/з: Аугментации и работа с изображениями

## 1. Задание 1: Стандартные аугментации torchvision

Взял по 1 изображению каждого класса, к каждому применил 1 стандартную аугментацию и сразу весь пайплайн из 5 аугментаций.

![1.1](https://github.com/dmitryboris/practice_summer/blob/main/dz5/1.1.png)

![1.2](https://github.com/dmitryboris/practice_summer/blob/main/dz5/1.2.png)

![1.3](https://github.com/dmitryboris/practice_summer/blob/main/dz5/1.3.png)

![1.4](https://github.com/dmitryboris/practice_summer/blob/main/dz5/1.4.png)

![1.5](https://github.com/dmitryboris/practice_summer/blob/main/dz5/1.5.png)

## Задание 2: Кастомные аугментации

Были созданы 3 аугментации:

 - RandomBlur
 - RandomPerspective
 - RandomBrightnessContrast

Сравнение блюра и гауссовского шума

![2.1](https://github.com/dmitryboris/practice_summer/blob/main/dz5/2.1.png)

Демонстрация RandomBrightnessContrast

![2.2](https://github.com/dmitryboris/practice_summer/blob/main/dz5/2.2.png)

## Задание 3: Анализ датасета

Задание 3: Анализ датасета

Статистика размеров изображений:

 - Всего изображений: 180
 - Минимальный размер: 210x240
 - Максимальный размер: 736x1308
 - Средний размер: 538.9x623.6
 - Медианный размер: 564x564

![3.1](https://github.com/dmitryboris/practice_summer/blob/main/dz5/3.1.png)

## Задание 4: Pipeline аугментаций

Реализован класс AugmentationPipeline со статическими методами, которые возвращают 3 конфигурации:
 - light (RandomBrightnessContrast + RandomBlur)
 - medium (light + AddGaussianNoise)
 - heavy (medium + RandomErasingCustom + CutOut + ElasticTransform)

Применил каждую конфигурацию к 5 изображениям каждого класса и сохранил

## Задание 5: Эксперимент с размерами
## Задание 6: Дообучение предобученных моделей

Взял предобученный resnet18 и дообучил на нашем датасете, к которому применил некоторые аугментации:
 - RandomHorizontalFlip
 - Гауссовский шум
 - Нормализация

![6](https://github.com/dmitryboris/practice_summer/blob/main/dz5/6.png)

