# DOCKER HW3

## Сборка образа 

```bash
docker build -t docker-hw3:1 .
```

## Запуск контейнера

```bash
docker run --name hw3 -e GREETING="Hello from container!" -p 127.0.0.1:8080:8000 docker-hw3:1
```

## Проверка
Получение текущего значения счетчика:
```bash
curl http://127.0.0.1:8080/
```
Увеличение счетчика:
```bash
curl -X POST http://127.0.0.1:8080/increment
```
Снова получаем значение счетчика:
```bash
curl http://127.0.0.1:8080/
```
Проверка логов:
```bash
docker logs hw3
```

## Вывод проверок

Первый запрос:
```json
{"greeting": "Hello from container!", "count": 0, "hostname": "77c732e7d199", "storage": "sqlite"}
```
Второй запрос:
```json
{"greeting": "Hello from container!", "count": 1, "hostname": "77c732e7d199", "storage": "sqlite"}
```
Третий запрос:
```json
{"greeting": "Hello from container!", "count": 1, "hostname": "77c732e7d199", "storage": "sqlite"}
```
Вывод логов:
```bash
2026-11-22 19:39:24,175 listening port=8000 storage=sqlite
2026-11-22 19:39:38,410 http 172.17.0.1 "GET / HTTP/1.1" 200 -
2026-11-22 19:40:56,593 http 172.17.0.1 "POST /increment HTTP/1.1" 200 -
2026-11-22 19:42:24,535 http 172.17.0.1 "GET / HTTP/1.1" 200 -
```
