FROM node:18
WORKDIR /app

# Копируются файлы с перечнем зависимостей проекта: в Python такие файлы принято называть requirements.txt,
# а при разработке на JS используют package.json и package-lock.json
COPY package.json package.json
COPY package-lock.json package-lock.json

# Выполняется установка необходимых пакетов (npm — это менеджер пакетов в Node.js, вроде pip в Python)
RUN npm install

# Исходный код приложения копируется в образ
COPY . .
RUN npm run build

# Эта команда запустит встроенный сервер на Node.js, который будет раздавать
# содержимое директории /app/build на порте 8000
CMD ["npx", "-y", "http-server", "-p", "8000", "/app/build"]