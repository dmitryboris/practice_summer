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
| torch      | real              | fp16        | cuda     | (16, 3, 224, 224) | 5.970 ms       | 0.373 ms           | 418.8 MB           | 30.3x     | N/A     | 
| torch      | real              | fp16        | cuda     | (32, 3, 224, 224) | 12.822 ms      | 0.401 ms           | 418.8 MB           | 14.1x     | N/A     | 
| torch      | real              | fp16        | cuda     | (48, 3, 224, 224) | 18.195 ms      | 0.379 ms           | 418.8 MB           | 9.9x      | N/A     | 
| torch      | real              | fp16        | cuda     | (64, 3, 224, 224) | 26.317 ms      | 0.411 ms           | 418.8 MB           | 6.9x      | N/A     | 
| onnx       | real              | fp16        | cuda     | (16, 3, 256, 256) | 10.962 ms      | 0.685 ms           | 48.0 MB            | 16.5x     | N/A     |
| onnx       | real              | fp16        | cuda     | (32, 3, 256, 256) | 22.876 ms      | 0.715 ms           | 48.0 MB            | 7.9x      | N/A     | 
| onnx       | real              | fp16        | cuda     | (48, 3, 256, 256) | 34.871 ms      | 0.726 ms           | 48.0 MB            | 5.2x      | N/A     |
| onnx       | real              | fp16        | cuda     | (64, 3, 256, 256) | 47.258 ms      | 0.738 ms           | 48.0 MB            | 3.8x      | N/A     | 
| torch_trt  | real              | fp16        | cuda     | (16, 3, 256, 256) | 4.861 ms       | 0.304 ms           | 213.8 MB           | 37.2x     | N/A     | 
| torch_trt  | real              | fp16        | cuda     | (32, 3, 256, 256) | 7.614 ms       | 0.238 ms           | 213.8 MB           | 23.7x     | N/A     | 
| torch_trt  | real              | fp16        | cuda     | (48, 3, 256, 256) | 10.403 ms      | 0.217 ms           | 213.8 MB           | 17.4x     | N/A     | 
| torch_trt  | real              | fp16        | cuda     | (64, 3, 256, 256) | 13.474 ms      | 0.211 ms           | 213.8 MB           | 13.4x     | N/A     | 
| torch      | real              | fp32        | cuda     | (16, 3, 224, 224) | 10.014 ms      | 0.626 ms           | 597.0 MB           | 18.1x     | N/A     | 
| torch      | real              | fp32        | cuda     | (32, 3, 224, 224) | 21.133 ms      | 0.660 ms           | 597.0 MB           | 8.6x      | N/A     | 
| torch      | real              | fp32        | cuda     | (48, 3, 224, 224) | 31.852 ms      | 0.664 ms           | 597.0 MB           | 5.7x      | N/A     | 
| torch      | real              | fp32        | cuda     | (64, 3, 224, 224) | 43.101 ms      | 0.673 ms           | 597.0 MB           | 4.2x      | N/A     | 
| onnx       | real              | fp32        | cuda     | (16, 3, 256, 256) | 10.858 ms      | 0.679 ms           | 48.0 MB            | 16.6x     | N/A     | 
| onnx       | real              | fp32        | cuda     | (32, 3, 256, 256) | 22.679 ms      | 0.709 ms           | 48.0 MB            | 8.0x      | N/A     | 
| onnx       | real              | fp32        | cuda     | (48, 3, 256, 256) | 34.194 ms      | 0.712 ms           | 48.0 MB            | 5.3x      | N/A     | 
| onnx       | real              | fp32        | cuda     | (64, 3, 256, 256) | 46.423 ms      | 0.725 ms           | 48.0 MB            | 3.9x      | N/A     | 
| onnx       | real              | fp32        | cpu      | (16, 3, 256, 256) | 180.753 ms     | 11.297 ms          | 0.2 MB             | 1.0x      | N/A     | 
| onnx       | real              | fp32        | cpu      | (32, 3, 256, 256) | 344.099 ms     | 10.753 ms          | 0.2 MB             | 0.5x      | N/A     | 
| onnx       | real              | fp32        | cpu      | (48, 3, 256, 256) | 498.950 ms     | 10.395 ms          | 0.2 MB             | 0.4x      | N/A     | 
| onnx       | real              | fp32        | cpu      | (64, 3, 256, 256) | 655.026 ms     | 10.235 ms          | 0.2 MB             | 0.3x      | N/A     | 
| torch_trt  | real              | fp32        | cuda     | (16, 3, 256, 256) | 8.516 ms       | 0.532 ms           | 213.8 MB           | 21.2x     | N/A     |
| torch_trt  | real              | fp32        | cuda     | (32, 3, 256, 256) | 15.849 ms      | 0.495 ms           | 213.8 MB           | 11.4x     | N/A     | 
| torch_trt  | real              | fp32        | cuda     | (48, 3, 256, 256) | 24.050 ms      | 0.501 ms           | 213.8 MB           | 7.5x      | N/A     | 
| torch_trt  | real              | fp32        | cuda     | (64, 3, 256, 256) | 32.222 ms      | 0.503 ms           | 213.8 MB           | 5.6x      | N/A     | 


TensorRT с батчем 64 и точностью fp16 работает быстрее всего. Карточка rtx 4060

## 4. Обсуждение

Что-то я ничего не понимаю. Очень много времени уходит на прогон всех вариантов, поэтому тяжело отдебажить какие-то вещи и проверить гипотезы. Скрипт падает, не отработав до конца

## 5. Заключение


