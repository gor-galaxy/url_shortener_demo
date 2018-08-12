# Вступление

Демонстрационный сервис коротких ссылок. 
Для упрощения демонстрации (установки и запуска) используется встроенный в PHP веб-сервер и SQLite база данных.

Сервис: 
- создает короткие ссылки с кодом длинной в 12 символов
- не проверяет реальное существование ссылок, переданных на сокращение
- разрешает создавать короткие ссылки, задав собственный код
- не дает создать короткую ссылку, если уже существует не истекшая ссылка с таким же кодом
- разрешает создавать короткие ссылки со сроком жизни от 1 до 30 дней
- считает валидной переданную ссылку, если в ней есть указание протокола (http://, https://...)
- считает переход по короткой ссылке уникальным по сочетанию: user-agent / ip / session_id
- устанавливает длину сессию равной 14 дней, для улучшения определеня уникальных переходов в рамках этого периода
- сокращает только URLы, содержащие латиницу (сокращение "http://привет.рф" - не поддерживается)

# Требования к вашей машине

- PHP 7.1
- Composer

# Установка и запуск

Установить зависимости
```
composer install
```

Создать файл конфигурации путем копирования из .env.example
```
cp .env.example .env
```

Создать файл БД
```
touch database/database.sqlite
```

Выполнить миграции
```
php artisan migrate
```

Поднять тестовый веб-сервер 
```
php artisan serve
```

Готово. Сервис будет доступен по ссылке: [http://127.0.0.1:8000](http://127.0.0.1:8000)

# Запуск тестов

Создать тестовую БД

```
touch database/testing.sqlite
```

Запустить PHPUnit
```
vendor/bin/phpunit
```