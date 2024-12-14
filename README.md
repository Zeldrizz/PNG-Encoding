# Проект "PNG Encoder"

## Задача

На вход приложения подается изображение в сыром виде (RAW): трехмерный массив размера HxWx3, где для каждого пикселя определены компоненты RGB. Требуется сжать изображение в формат PNG и сохранить его. Проект включает в себя следующие этапы:

- Анализ и понимание структуры формата PNG.
- Реализация фильтра PAETH первичной обработки RAW файла.
- Реализация цветовых фильтров.
- Использование алгоритма сжатия данных DEFLATE, используемых в PNG.
- Обработка и оптимизация цветовой информации.
- Формирование корректного файла PNG.
- Тестирование с различными изображениями для проверки корректности и эффективности сжатия.

## Сколько человек

Проект рассчитан на 1 человека.

## Функционал

1. **Чтение исходного изображения:**
   - Прием входных данных в виде массива HxWx3 с RGB-компонентами (.raw файл)
   
2. **Предварительная обработка:**
   - Применение фильтра PAETH для улучшения сжатия.
   
3. **Сжатие данных:**
   - Использование алгоритма DEFLATE из ZLIB для сжатия пиксельных данных.
   
4. **Формирование PNG-файла:**
   - Создание необходимых блоков PNG (IHDR, IDAT, IEND и т.д.)
   - Корректное объединение и структурирование блоков согласно спецификации PNG.
   
5. **Сохранение файла:**
   - Запись сжатых данных в файл с расширением .png.
   
6. **Тестирование:**
   - Проверка корректности созданных PNG-файлов.
   - Оптимизация производительности и качества сжатия.

7. **Применение цветовых фильтров:**
   - Применение цветовых фильтров (по типу Grayscale, Negative) к изображению.

## Цели проекта

- Изучить структуру формата PNG и понять принципы его работы.
- Реализовать алгоритм PAETH для первичной фильтрации изображения.
- Реализовать несколько цветовых фильтров для изменения изображений.
- Использовать алгоритм сжатия DEFLATE на языке C/C++ из ZLIB.
- Создать полноценное приложение, способное конвертировать сырые изображения в формат PNG.
- Обеспечить корректную работу приложения на различных тестовых изображениях.
- Получить практический опыт разработки программного обеспечения, взаимодействующего с системными ресурсами и файловой системой.

## Сборка
```bash
mkdir build
cd build
cmake ..
make
ctest
```

## Использование
```bash
cd build
./png_encoder input.raw output.png width height [optional] filter
```

## Частный пример использования
```bash
python3 generate_raw_from_png.py examples/png/test5-1280x720.png examples/raw/test5-1280x720.raw 
// можно свой png преобразовать в несжатый HxWx3 raw формат
cd build
./png_encoder ../examples/raw/test5-1280x720.raw ../result.png 1280 720 
// получаем result.png, который точь в точь как исходный png
```

## Источники

- [PNG: Filtering](https://en.wikipedia.org/wiki/PNG#Filtering)
- [Глубокое погружение в PNG (Habr)](https://habr.com/ru/articles/130472/)
- [Подробности о PNG: фильтрация и компрессия (Habr)](https://habr.com/ru/companies/ruvds/articles/787302/)
- [ZLIB: Документация](https://www.zlib.net/manual.html)
- [DEFLATE: Алгоритм сжатия](https://en.wikipedia.org/wiki/Deflate)
- [GoogleTest: Библиотека тестирования](https://github.com/google/googletest.git)