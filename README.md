# Практическая работа 8. Анализ метода загрузки данных

## Цель:
Определить наиболее эффективный метод загрузки данных (малых и больших объемов) из CSV-файлов в СУБД PostgreSQL, сравнивая время выполнения для методов: pandas.to_sql(), psycopg2.copy_expert() (с файлом и с io.StringIO), и пакетная вставка (psycopg2.extras.execute_values).

## Задачи:

1.  **Подключиться** к предоставленной базе данных PostgreSQL.
2.  **Проанализировать структуру** исходных CSV-файлов ([upload_test_data.csv](https://github.com/BosenkoTM/SQL-for-Begginer-Data-Analytics/blob/main/practice/pr-5-2-upload-data-from-pandas-to-sql-main/upload_test_data.csv) , [upload_test_data_big.csv](https://github.com/BosenkoTM/SQL-for-Begginer-Data-Analytics/blob/main/practice/pr-5-2-upload-data-from-pandas-to-sql-main/upload_test_data_big.csv)).
3.  **Создать эскизы ER-диаграмм** для таблиц, соответствующих структуре CSV-файлов.
4.  **Реализовать** три различных метода загрузки данных в PostgreSQL(**pandas.to_sql()**, **copy_expert()**, **io.StringIO**).
5.  **Измерить время**, затраченное каждым методом на загрузку данных из малого файла (`upload_test_data.csv`).
6.  **Измерить время**, затраченное каждым методом на загрузку данных из большого файла (`upload_test_data_big.csv`).
7.  **Визуализировать** результаты сравнения времени загрузки с помощью гистограммы (`matplotlib`).
8.  **Сделать выводы** об эффективности каждого метода для разных объемов данных.
