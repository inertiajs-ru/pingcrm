# Ping CRM

Демо-приложение, демонстрирующее, как работает Inertia.js.

![](https://raw.githubusercontent.com/inertiajs/pingcrm/master/screenshot.png)

## Установка

Клонировать репозиторий локально:

[RU]
```sh
git clone https://github.com/inertiajs-ru/pingcrm.git pingcrm
cd pingcrm
```

[EN]
```sh
git clone https://github.com/inertiajs/pingcrm.git pingcrm
cd pingcrm
```

Установить зависимости PHP:

```sh
composer install
```

Установить зависимости NPM:

```sh
npm ci
```

Сборка асетов:

```sh
npm run dev
```

Установка конфигурации:

```sh
cp .env.example .env
```

Сгенерировать ключ приложения:

```sh
php artisan key:generate
```

Создайте базу данных SQLite. Вы также можете использовать другую базу данных (MySQL, Postgres), просто обновите свою конфигурацию соответствующим образом.

```sh
touch database/database.sqlite
```

Запустить миграцию базы данных:

```sh
php artisan migrate
```

Запустить заполнение данными (сиды) базы данных:

```sh
php artisan db:seed
```

Запустите сервер разработки (в выводе будет указан адрес):

```sh
php artisan serve
```

Вы готовы к работе! Посетите Ping CRM в своем браузере и войдите с помощью:

- **Username:** johndoe@example.com
- **Password:** secret

## Запуск тестов

Чтобы запустить тесты Ping CRM, запустите:

```
phpunit
```
