# Инструкция по установке

1. Выполнить сборку контейнеров докера: `docker-compose up -d --build`
2. Зайти в консоль докера: `docker-compose run web bash` и выполнить установку зависимостей `composer install`
3. Прописать в хостах компьютера (/etc/hosts): `127.0.0.1 yii3-demo.local`
4. Сайт доступен по URL:  http://yii3-demo.local

## Доступы к БД

DB name: **yii3_demo_db**

DB user: **root**

DB password: **123456**

## Yii3

Документация (The Definitive Guide to Yii 3.0): https://github.com/yiisoft/docs/tree/master/guide/en

Приложение Yii3: https://github.com/yiisoft/app
