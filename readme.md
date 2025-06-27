# ETL process

## Цель проекта:
Реализация простого ETL-процесса: извлечение погодных данных через OpenWeather API, трансформация и загрузка в PostgreSQL.
Проект построен как обучающий пример для закрепления базовых принципов Data Engineering.

OpenWeather API → (requests) → Extract → Transform → Load → [PostgreSQL (staging)]

## Запуск
1. Зарегистроваться в Openweather API
2. Получить api ключ
3. Прописать свой api key в url

## .env
В .env файл создайте (что в кавычках, то подставляете свое):
API_KEY='API_KEY'
DB_NAME='dbname'
DB_USER='user'
DB_PASSWORD='password'
HOST='host'
PORT='port'

# Структура таблицы
CREATE TABLE stagging.weather_data (
    id GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    city VARCHAR(20) NOT NULL,
    date TIMESTAMP NOT NULL,
    weather VARCHAR(30),
    temperature NUMERICAL
);

# Идеи для развития
1. Добавить схему core для нормализации данных (таблицы: cities, weather_conditions, fact_weather)
2. Расширить на другие города
3. Подключить dbt для автоматизации формирования core-слоя