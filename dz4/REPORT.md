# Отчёт по 4 д/з

## 1. Задание 1: Сравнение CNN и полносвязных сетей

### 1.1 Сравнение на MNIST

Создадим три модели и обучим на MNIST

| Модель          | Параметры | Время обучения (сек, 5 эпох) | Точность train (%) | Точность test (%) | Потеря train | Потеря test |
|-----------------|-----------|------------------------------|--------------------|-------------------|--------------|-------------|
| Fully Connected | 235,146   | ~80                          | 98.71              | 97.93             | 0.0398       | 0.0743      |
| Simple CNN      | 421,642   | ~75                          | 99.21              | 99.15             | 0.0244       | 0.0242      |
| Residual CNN    | 160,906   | ~100                         | 99.30              | 99.19             | 0.0226       | 0.0247      |

![Simple CNN vs Residual CNN](https://github.com/dmitryboris/practice_summer/blob/main/dz4/simple_residual.png)

![Fully Connected vs Residual CNN](https://github.com/dmitryboris/practice_summer/blob/main/dz4/residual_connected.png)

![Simple CNN vs Fully Connected](https://github.com/dmitryboris/practice_summer/blob/main/dz4/simple_connected.png)

### 1.2 Сравнение на CIFAR-10

Создадим три модели и обучим на CIFAR-10

| Модель                 | Параметры | Время обучения sec | Точность train (%) | Точность test (%) | Потеря train | Потеря test |
|------------------------|-----------|--------------------|--------------------|-------------------|--------------|-------------|
| Fully Connected        | 3,805,450 | 65                 | 56.72              | 51.72             | 1.2222       | 1.3997      |
| CNN WithRegularization |   283,722 | 110                | 67.27              | 73.54             | 0.9337       | 0.7552      |
| Residual CNN           |   161,482 | 120                | 82.94              | 78.23             | 0.4922       | 0.6459      |

![Fully Connected](https://github.com/dmitryboris/practice_summer/blob/main/dz4/conn_plot.png)

![CNN With Regularization](https://github.com/dmitryboris/practice_summer/blob/main/dz4/reg_plot.png)

![Residual CNN](https://github.com/dmitryboris/practice_summer/blob/main/dz4/res_plot.png)

![Simple CNN vs Residual CNN](https://github.com/dmitryboris/practice_summer/blob/main/dz4/1.png)

![Fully Connected vs Residual CNN](https://github.com/dmitryboris/practice_summer/blob/main/dz4/2.png)

![Simple CNN vs Fully Connected](https://github.com/dmitryboris/practice_summer/blob/main/dz4/3.png)

## 2. Задание 2: Анализ архитектур CNN

### 2.1 Влияние размера ядра свертки

Обучаем и тестируем на CIFAR-10

| Модель       | Точность (Accuracy) | Время обучения (сек) |
|--------------|---------------------|----------------------|
| 3x3          | 54.22%              | 62.20                |
| 5x5          | 54.36%              | 60.54                |
| 7x7          | 52.96%              | 60.95                |
| 1x1 + 3x3    | 55.42%              | 61.87                |

Визуализация активаций первого слоя в ноутбуке

### Влияние на обучение и качество

- **3×3 ядра:** гибкое и устойчивое обучение, признаки учатся постепенно.
- **5×5 и 7×7 ядра:** охватывают больше информации сразу, но хуже обобщают на небольших данных.
- **1×1 + 3×3:** компромисс — меньше параметров и высокая выразительность.
