# Отчёт по 6 д/з: Генератор текста на базе Transformer

## 1. Layers

Изменен класс MultiheadAttention, в нем используется torch.nn.functional.scaled_dot_product_attention

## Tokenizer

Используется от же токенизатор, что и в уроке

## Data

Взят датасет cc_news (10%). Он содержит новостные статьи с новостных сайтов по всему миру. 

Разбит на валидационную и тренировочную выборки

Размер батча 8.

## GeneratorTransformer

GeneratorTransformer написан на основе Decoder из урока

## Train

2 эпохи. Время обучения ~12 минут

![loss](https://github.com/dmitryboris/practice_summer/blob/main/dz6/loss.png)

## Result

Несмотря на низкий loss, модель выдает неточные результаты. Первые слова продолжения еще несут какую-то минимальную смысловую нагрузку, а затем бессвязный поток текста
