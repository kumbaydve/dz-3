6 баллов


Запуск:

cp .env.example .env
docker compose up -d --build


Запросы для проверки увеличения счётчика:

curl -s http://localhost:8080/
curl -s -X POST http://localhost:8080/increment
curl -s http://localhost:8080/


Проверка сохранения данных:

docker compose down
docker compose up -d
curl -s http://localhost:8080/


Логи до перезапуска (до compose down):

2026-11-22 17:30:54,334 listening port=8000 storage=sqlite
2026-11-22 17:31:01,402 http 172.18.0.1 "GET / HTTP/1.1" 200 -
2026-11-22 17:31:05,433 http 172.18.0.1 "POST /increment HTTP/1.1" 200 -
2026-11-22 17:31:13,820 http 172.18.0.1 "GET / HTTP/1.1" 200 -


Логи после перезапуска и проверки:

2026-11-22 17:32:21,790 listening port=8000 storage=sqlite
2026-11-22 17:32:27,967 http 172.18.0.1 "GET / HTTP/1.1" 200 -
