# docker-xdebug-phpstorm
Тренировочный репозиторий для создания окружения при обучении Laravel ( https://www.youtube.com/watch?v=qxGlQZIbpHM )

## Dockerfile

Ищем докер-образ тут https://hub.docker.com/_/php?tab=tags
В данном конкретном случае использован php:8.1.19-fpm-alpine .

Список дополнительных пакетов:

* bash - привычная командная оболочка
* curl - загрузка из сети
* wget - загрузка из сети
* rsync - в видео есть, но на данный момент внятного объяснения нет
* ca-sertificates - для работы https
* openssl - для работы https
* openssh - для работы git
* git - версионный контроль
* tzdata - часовые пояса
* openntpd - мировое время
* libxrender -
* fontconfig -
* libc6-compat - часть инструментария для сборки расширений
* mysql-client -
* gnupg - часть инструментария для сборки расширений
* binutils-gold - часть инструментария для сборки расширений
* autoconf - часть инструментария для сборки расширений
* g++ - часть инструментария для сборки расширений
* gcc - часть инструментария для сборки расширений
* libgcc - часть инструментария для сборки расширений
* linux-headers - часть инструментария для сборки расширений
* make - часть инструментария для сборки расширений
* pyton - часть инструментария для сборки расширений
* freetype - часть инструментария для работы gd
* libpng - часть инструментария для работы gd
* libjpeg-turbo - часть инструментария для работы gd
* freetype-dev - часть инструментария для работы gd
* libpng-dev - часть инструментария для работы gd
* libjpeg-turbo-dev - часть инструментария для работы gd
* zlib-dev - часть инструментария для поддержки ZIP-архивов
* libzip-dev -  часть инструментария для поддержки ZIP-архивов

Расширения php:

* bcmath - математика
* mysqli - MySQL
* pdo_mysql - драйвер PDO MySQL
* pdo_pgsql - драйвер PDO PostgreSQL
* gd - работа с графикой
* zip - работа с архивами
* xdebug - дебаггер

## Настройка xdebug

Содержимое xdebug.ini

```
zend_extension=xdebug.so
[xdebug]
xdebug.remote_enable=true
xdebug.remote_autostart=0
xdebug.idekey=PHPSTORM
xdebug.profiler_enable=0
xdebug.max_nesting_level=700
xdebug.remote_host=172.17.0.1
```

Особо обратить внимание на строчку:
```
xdebug.remote_host=172.17.0.1
```

IP - это ip интерфейса докера. Можно узнать командой:

```
sudo ifconfig docker0
```
