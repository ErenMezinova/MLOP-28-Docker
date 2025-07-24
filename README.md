# MLOP28-Mezinova-Docker
«Docker»

Содержимое Dockerfile
```
# Используем образ
FROM continuumio/miniconda3:latest

# Создаём и делаем рабочей папкой /app
WORKDIR /app

# Создаём простой скрипт 1.sh с надписью "Hello Netology"
RUN echo '#!/bin/bash\n\necho "Hello Netology"' > 1.sh

# Делаем файл исполняемым
RUN chmod +x 1.sh

# Устанавливаем нужные Python-пакеты
RUN pip install mlflow boto3 pymysql

# Запускаем скрипт при сборке контейнера 
RUN ./1.sh

# Указываем команду по умолчанию при запуске контейнера
CMD ["./1.sh"]
```

Собираем контейнер
```
docker build -t netology-ml:netology-ml .
```
Запускаем контейнер
```
docker run --rm netology-ml:netology-ml
```

Получаем:

```
Hello Netology
```
К файлу приложены скриншоты сборки и запуска.
