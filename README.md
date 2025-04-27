# Практическая работа 8. Анализ метода загрузки данных

## Цель:
Определить наиболее эффективный метод загрузки данных (малых и больших объемов) из CSV-файлов в СУБД PostgreSQL, сравнивая время выполнения для методов: pandas.to_sql(), psycopg2.copy_expert() (с файлом и с io.StringIO), и пакетная вставка (psycopg2.extras.execute_values).

## Ход работы:
1. Установим необходимые библиотеки и подключимся к предоставленной базе данных `lect_08_bda_big_data` в PostgreSQL:

![image](https://github.com/user-attachments/assets/25daa6ff-7371-45c7-8b84-14ad388d36b1)
![image](https://github.com/user-attachments/assets/d751179b-ec83-40d3-a787-3d9aa6a95aea)
![image](https://github.com/user-attachments/assets/e279e3da-1f98-44e9-9ac3-2e3f29bf2e8b)
![image](https://github.com/user-attachments/assets/47a9b79c-96fa-4be0-bff7-d97b14d5a999)

2. Проанализируем структуру исходных CSV-файлов:

![image](https://github.com/user-attachments/assets/bb0cb3f4-83dc-43bd-b49b-6f470c22137f)

3. Создадим эскиз ER-диаграммы для таблицы, соответствующей структуре CSV-файлов. Для этого сначала создаем таблицу в нашей базе данных.

![image](https://github.com/user-attachments/assets/2a6338d8-0d13-49d7-8646-ec184ba18d9b)

![image](https://github.com/user-attachments/assets/6b775f08-ff0e-4e10-8d81-538a3954e5e4)

4. Реализуем три различных метода загрузки данных в PostgreSQL(pandas.to_sql(), copy_expert(), io.StringIO). Измерим время, затраченное каждым методом на загрузку данных из малого и большого файлов.

![image](https://github.com/user-attachments/assets/ecd81426-2c8e-403a-a147-1c374abf12f1)

Заметим, что самая медленная загрузка идет через `pandas`. А самая быстрая через `copy_expert()`.

5. Сделаем визуализицию результатов сравнения времени загрузки с помощью гистограммы, используя библиотеку `matplotlib`

![image](https://github.com/user-attachments/assets/6fe8aed4-3ca9-4380-b360-f69b41430d4c)

Гистограмма наглядно показывает разницу во времени загрузки данных. Таким образом, метод загрузки данных через `pandas` оказался менее эффективным из всех. Стоит также отметить, что при загрузке большого объема данных через `pandas` время загрузки совсем критичное - на целых две с небольшим минуты больше, чем через другие методы загрузки. В то время как скорости загрузки через `copy_expert()` и `io.StringIO` не сильно отличаются друг от друга.

## Индивидуальные задания. Вариант 17.

Проверяем все ли вспомогательные функции работают:

![image](https://github.com/user-attachments/assets/ac23d4e2-204e-4198-a80d-b61c789d3063)

Задание 1: Настройка таблиц. Создаем таблицы sales_small, sales_big.

![image](https://github.com/user-attachments/assets/330ef051-8f71-4525-8350-79e902aca869)
![image](https://github.com/user-attachments/assets/6fb1d626-dcda-4dbc-a7fc-6e827466f4ff)

Создаем эскизы ER-диаграмм для таблиц:

![image](https://github.com/user-attachments/assets/a3b0e054-503a-48c7-90a7-751f3c9379f6)
![image](https://github.com/user-attachments/assets/1c0b9245-d3cd-4eab-9eb8-dd23cc8c21d5)

Задание 2: Загрузка малых данных (sales_small). Метод: copy_expert (file)

![image](https://github.com/user-attachments/assets/32b2abea-9b5a-4da2-8f74-18123112e510)
![image](https://github.com/user-attachments/assets/cb767981-8cee-40a7-b849-566a0c1162f2)

Задание 3: Загрузка больших данных (sales_big). Метод: copy_expert (file)

![image](https://github.com/user-attachments/assets/9f722424-726a-41e2-925f-35e748054f6c)
![image](https://github.com/user-attachments/assets/5096289c-7923-4752-8c4c-2f11cf748b3c)

Задание 4: SQL Анализ. SQL: Подсчитать записи в sales_small, где cost = 0.50.

Задание 5: Python Анализ и Визуализация. Python: Рассчитать стандартное отклонение quantity из sales_big (LIMIT 50000).



## Выводы:
В ходе выполнения лабораторной работы были успешно освоены методы загрузки данных (малых и больших объемов) из CSV-файлов в СУБД PostgreSQL и определены наиболее эффективные из них. Кроме того, была произведена визуализация полученных результатов.
