## Инструкция

### Запуск
При запуске приложения создается БД users.

Методом https://arch.homework/api/user/api/addtestusers можно добавить тестовых пользователей в БД с идентификаторами от 1 до 10 (т.е. запустить можно только если в БД нет пользователей с такими Id)

### Postgres

Postgres создается в minikube через postgres-deployment.yaml.
Пользователь БД, пароль и строка подключения хранятся в secrets (добавление в minikube через secrets.yaml).



