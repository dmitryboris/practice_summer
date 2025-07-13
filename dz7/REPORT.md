# Отчёт по 7 д/з: Сравнение производительности различных подходов оптимизации

## 1. Введение

КОД: https://github.com/dmitryboris/onnx

Протестировать ONNX и TensorRT на моделях Resnet18 для различных размеров изображений с разными размерами батча

## 2. Методология

Инференс ONNX моделей на CPU и GPU
Компиляция с помощью Torch-TensorRT

## 3. Результаты

| function   | dataloader_type   | precision   | device   | shape             | time (batch)   | time (per image)   | allocated_memory   | speedup   | FLOPs   | 
|------------|-------------------|-------------|----------|-------------------|----------------|--------------------|--------------------|-----------|---------|
| torch      | real              | fp16        | cuda     | (16, 3, 224, 224) | 5.900 ms       | 0.369 ms           | 418.0 MB           | 0.0x      | N/A     | 
| torch      | real              | fp16        | cuda     | (32, 3, 224, 224) | 12.348 ms      | 0.386 ms           | 418.0 MB           | 0.0x      | N/A     | 
| torch      | real              | fp16        | cuda     | (48, 3, 224, 224) | 18.088 ms      | 0.377 ms           | 418.0 MB           | 0.0x      | N/A     | 
| torch      | real              | fp16        | cuda     | (64, 3, 224, 224) | 25.297 ms      | 0.395 ms           | 418.0 MB           | 0.0x      | N/A     | 
| onnx       | real              | fp16        | cuda     | (16, 3, 256, 256) | 10.900 ms      | 0.681 ms           | 48.0 MB            | 0.0x      | N/A     | 
| onnx       | real              | fp16        | cuda     | (32, 3, 256, 256) | 22.665 ms      | 0.708 ms           | 48.0 MB            | 0.0x      | N/A     | 
| onnx       | real              | fp16        | cuda     | (48, 3, 256, 256) | 34.509 ms      | 0.719 ms           | 48.0 MB            | 0.0x      | N/A     | 
| onnx       | real              | fp16        | cuda     | (64, 3, 256, 256) | 46.496 ms      | 0.727 ms           | 48.0 MB            | 0.0x      | N/A     | 
| torch_trt  | real              | fp16        | cuda     | (16, 3, 256, 256) | 5.554 ms       | 0.347 ms           | 213.4 MB           | 0.0x      | N/A     | 
| torch_trt  | real              | fp16        | cuda     | (32, 3, 256, 256) | 9.312 ms       | 0.291 ms           | 213.4 MB           | 0.0x      | N/A     | 
| torch_trt  | real              | fp16        | cuda     | (48, 3, 256, 256) | 13.028 ms      | 0.271 ms           | 213.4 MB           | 0.0x      | N/A     | 
| torch_trt  | real              | fp16        | cuda     | (64, 3, 256, 256) | 17.026 ms      | 0.266 ms           | 213.4 MB           | 0.0x      | N/A     | 
| torch      | real              | fp32        | cuda     | (16, 3, 224, 224) | 9.939 ms       | 0.621 ms           | 597.0 MB           | 0.0x      | N/A     | 
| torch      | real              | fp32        | cuda     | (32, 3, 224, 224) | 21.097 ms      | 0.659 ms           | 597.0 MB           | 0.0x      | N/A     | 
| torch      | real              | fp32        | cuda     | (48, 3, 224, 224) | 31.815 ms      | 0.663 ms           | 597.0 MB           | 0.0x      | N/A     | 
| torch      | real              | fp32        | cuda     | (64, 3, 224, 224) | 43.084 ms      | 0.673 ms           | 597.0 MB           | 0.0x      | N/A     | 
| onnx       | real              | fp32        | cuda     | (16, 3, 256, 256) | 10.890 ms      | 0.681 ms           | 48.0 MB            | 0.0x      | N/A     | 
| onnx       | real              | fp32        | cuda     | (32, 3, 256, 256) | 22.725 ms      | 0.710 ms           | 48.0 MB            | 0.0x      | N/A     | 
| onnx       | real              | fp32        | cuda     | (48, 3, 256, 256) | 34.468 ms      | 0.718 ms           | 48.0 MB            | 0.0x      | N/A     | 
| onnx       | real              | fp32        | cuda     | (64, 3, 256, 256) | 46.474 ms      | 0.726 ms           | 48.0 MB            | 0.0x      | N/A     | 
| torch_trt  | real              | fp32        | cuda     | (16, 3, 256, 256) | 8.574 ms       | 0.536 ms           | 212.9 MB           | 0.0x      | N/A     |
| torch_trt  | real              | fp32        | cuda     | (32, 3, 256, 256) | 15.814 ms      | 0.494 ms           | 212.9 MB           | 0.0x      | N/A     | 
| torch_trt  | real              | fp32        | cuda     | (48, 3, 256, 256) | 23.519 ms      | 0.490 ms           | 212.9 MB           | 0.0x      | N/A     | 
| torch_trt  | real              | fp32        | cuda     | (64, 3, 256, 256) | 31.611 ms      | 0.494 ms           | 212.9 MB           | 0.0x      | N/A     | 


TensorRT с батчем 64 и точностью fp16 работает быстрее всего. Карточка rtx 4060

## 4. Обсуждение

Что-то я ничего не понимаю. Очень много времени уходит на прогон всех вариантов, поэтому тяжело отдебажить какие-то вещи и проверить гипотезы

## 5. Заключение


