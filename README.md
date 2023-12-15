Jupyter Notebook for PySpark
=================================================================================================================

## Опис
- Запуск середи розробки Jupyter Notebook з підключеним PySpark движком за 5 хвилин з використанням Docker образа.


## Інструкція з запуску середовища.

### Перед запуском слід переконатись, що на робочій машині у вас встановлено:
 - Docker https://docs.docker.com/get-docker/
  
## Крок 1. Скачуємо образ pyspark
Виконуємо в терміналі команду
```
docker pull jupyter/pyspark-notebook
```

## Крок 2. Запускаємо контейнер
Виконуємо в терміналі команду  
```
docker run -p 8888:8888 --name jupyter_pyspark jupyter/pyspark-notebook
```

## Крок 3. Запускаємо Jupyter Notebook
Переходимо в браузере за посиланням, де замінюємо <token> на секретний токен, який ви можете взяти в терміналі запуску контейнера (крок 2) чи зайти та передивитися в лог контейнера (останні рядки) це буде мати такий вигляд:   


>To access the server, open this file in a browser  
>file:///home/jovyan/.local/share/jupyter/runtime/jpserver-7-open.html  
>Or copy and paste one of these URLs:  
>http://99463b3813d8:8888/lab?token=a83453334afa95a49e1ea8054fc6a64cbfa8e9c18d51dbf2  
>http://127.0.0.1:8888/lab?token=a83453334afa95a49e1ea8054fc6a64cbfa8e9c18d51dbf2  

Посилання
```
http://127.0.0.1:8888/?token=<token>
```

При цьому повинен відкритися JupyterNotebook без додаткової авторизації по паролю чи токену

## Крок 4. Запустити тестовий код на Python
Створюємо python сесію та запускаємо такий код
```
from pyspark.sql import SparkSession
print('PySpark lib enable')
    
spark = SparkSession.builder.appName('x3').getOrCreate()
print('Spark session is created')
print('Spark version:',spark.version)
```
