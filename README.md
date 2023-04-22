### Тестовое задание:

Необходимо написать скрипт который будет ходить в википедию,
и итеративно собирать информацию о городах 
(можно использовать Selenium или Beautifulsoup на выбор)

Список городов - 
Москва, Санкт-Петербург, Омск, Тимашевск, Хельсинки, Икаалинен,  Учкудук, Янгиабад.

Поля которые необходимо забирать : 
Навазние города, Страна , Дата основание, Тип климата, 
Часовой пояс, Население, Плотность населения, Телефонный код , Почтовый индекс

После этого данные необходимо очищать мусора и приводить к общему виду, 
так же необходимо обогащать каждый забор данных датой и временем. (реализация на pandas)
На последнем этапе необходимо поднять базу данных (mysql/postgres в докере) и записать полученный датафрейм в эту базу данных.
При выключение базы данных нужно сделать так, чтобы данные не терялись.

### Решение:

1. Установить платформу [Docker Compose](https://docs.docker.com/get-docker/ "Docker Compose")
2. Установить дистрибутив языков программирования Python [Anaconda](https://www.anaconda.com/download/ "Anaconda")

Установка локального инстанса posgres, в терминале запустить следующую команду:

<code> docker -compose up d</code>

2. Установка дистрибутива Anaconda3 , далее в Anaconda Navigator запустить приложение Jupyter Notebook.</p>
Устанавливаем Python пакеты,в терминале запустить следующую команду::

COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt


3. Запись данных по городам из Википедии в DataFrame и запись в базу данных
<code> python cities_stat_from_Wikipedia.ipynb </code>

### Результат:
DataFrame со списком городов. Таблица записана на поднятую БД postgres в Docker.  
Размер (8,10)
| Column        | Type            |
|:------------- |:---------------:|
| city          | object          |
| Country       | object          |
| Founded       | object          |
| Climate       | object          |
| UTC           | int64           |
| Population    | int64           |
| Phonecode     | object          |
| Postcode      | object          |
| Date          | datetime64[ns]  |
| Timestamp     | float64         |
