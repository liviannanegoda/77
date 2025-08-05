# Урок 5. Docker Compose и Docker Swarm

Задание 1: То что делали на семинаре.
1) создать сервис, состоящий из 2 различных контейнеров: 1 - веб, 2 - БД
2) выводы зафиксировать

# Вот подробно разобранный docker-compose.yml файл:

## Указываем версию синтаксиса файла docker-compose
version: '3.1'

## Описываем сервисы, которые будут запущены
services:

  ## Первый сервис: MySQL сервер
  some-mysql:
    # Используемый Docker образ
    image: mysql:8.0.31
    # Переменные окружения для MySQL
    environment:
      MYSQL_ROOT_PASSWORD: my-secret-pw


  ## Второй сервис: phpMyAdmin
  myphp:
    # Используемый Docker образ
    image: phpmyadmin/phpmyadmin
    # Проброс портов: хост:контейнер
    ports:
      - 8081:80
    # Указываем зависимость от MySQL сервиса
    depends_on:
      - some-mysql
    # Переменные окружения для phpMyAdmin
    environment:
      PMA_HOST: some-mysql

  ## Решение:
  ![2_2](https://github.com/user-attachments/assets/6ef1d0d0-2435-4ce1-9609-5f81834b49d1)
