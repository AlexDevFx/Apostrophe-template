# Шаблон проекта Apostrophe
## О проекте
Начальный шаблон для разработки под CMS Apostrophe. 
Проект построен с использованием docker контейнеров. 
Предусмотрено три ветки. Код расположен в соответствующих каталогах:
* dev - разработка
* test - тестирование
* release - окончательная версия для публикации
Внутри каждого каталога есть docker-файл Docketfile.<имя ветки>.
Для хранения файлов базы данных используется каталог /data/db.
Каждая ветка запускается в собственном контейнере.

## Использование
Перед первым запуском контейнера в каждом каталоге ветки: dev, test, release
необходимо выполнить:
`npm install`
Для запуска контейнера необходимо использовать docker-compose:
`docker-compose up -d`. 
Данная команда запустит контейнеры для всех 3х веток.
Остановка контейнера:
`docker-compose down`
Каждая ветка запускает собственный сервис приложения и сервис MongoDb.
Сервисы:
* Разработка(dev) -  dev-app
* Тестирование(test) - test-app
* Релиз(release) - release-app

Запуск сервиса для определенной ветки
`docker-compose up -d <service>`.
Например, ветка dev запускается командой: 
`docker-compose up -d dev-app`

Порты доступа к приложению:
* dev - 3000
* test - 3001
* release - 3002
Например, в ветке dev: http://localhost:3000

Для того чтобы добавить пользователя для входа в Apostrophe
необходимо выполнить:
`docker-compose exec <app-service> node app.js apostrophe-users:add <user> <user>`
Например, `docker-compose exec dev-app node app.js apostrophe-users:add admin admin`

