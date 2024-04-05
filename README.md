# Упрощенный сервис для регистрации и авторизации

Приложение представляет из себя упрощенный сервис для регистрации и авторизации. Сервис предоставляет 3 API-метода (REST):
1. ```/register email password``` - регистрирует нового пользователя, если пользователь с данным email еще не зарегистрирован.
2. ```/authorize email password``` - проверяет, зарегистрирован ли пользователь с данной почтой и паролем. Возращает уникальный для пользователя токен.
3. ```/feed token``` - проверяет, валидный ли токен.

Для выхода из сервиса воспользуйтесь командой `/exit`.
## Сборка

### Docker
Проект рекомендуется собирать докер-контейнере. Для UNIX систем просто пропишите следующую команду, находясь в корне проекта:
```bash
docker build -t authorization .
```
Соберется контейнер с именем `authorization`.
Для запуска проекта воспользуйтесь следующей командой:
```bash
docker run --network="host" -it authorization
```

### CMake 
Вы можете собрать проект на своей OS без использования Docker, но будьте готовы к необходимости установки зависимостей проекта (в том числе [jwt-cpp](https://github.com/Thalhammer/jwt-cpp/blob/master/docs/install.md)). Для сборки на UNIX системах пропишите из корневой директории проекта следующие команды:
```bash
mkdir build && cd build
cmake ..
make -j4
```
Файл для запуска проекта будет лежать в `./bin/main`
## Работа с базой данных
Сервис работает с СУБД PostgreSQL, причем база данных должна называться `users_` и иметь следующий вид:
| user_id_ | email_ | password_ |
|----------|--------|-----------|
| 78654320534 | jonh@example.com | qwerty |

Для настройки тестовой СУБД воспользуйтесь инструкцией в [docs](/docs)
