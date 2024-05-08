FROM nginx:latest

# Обновляем и устанавливаем пакеты
RUN apt-get update && apt-get install -y certbot python3-certbot-nginx less nano vim

# Очищаем кэш APT
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Открываем порты 80 и 443
EXPOSE 80
EXPOSE 443
