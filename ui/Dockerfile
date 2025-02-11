# Usa una imagen de Node.js para construir la aplicación
FROM node:22-alpine AS builder

# Instala PNPM globalmente con npm
RUN npm install -g pnpm

# Establece el directorio de trabajo dentro del contenedor
WORKDIR /app

# Copia los archivos de dependencias y los instala
COPY package.json pnpm-lock.yaml ./
RUN pnpm install --frozen-lockfile
COPY . .
RUN pnpm build

# Usa una imagen de Nginx para servir el frontend
FROM nginx:alpine

# Copia los archivos de la build de React a la carpeta de Nginx
COPY --from=builder /app/dist /usr/share/nginx/html

# Expone el puerto 80
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
