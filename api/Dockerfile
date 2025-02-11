# Usa una imagen de Node.js para construir la aplicación
FROM node:22-alpine AS builder

# Instala PNPM globalmente con npm
RUN npm install -g pnpm

# Establece el directorio de trabajo dentro del contenedor
WORKDIR /app

# Copia los archivos de dependencias y los instala
COPY package.json pnpm-lock.yaml ./
RUN pnpm install --frozen-lockfile

# Copia el resto del código
COPY . .

RUN npm run build

# Segunda etapa: imagen final ligera
FROM node:22-alpine

# Instala PNPM globalmente con npm
RUN npm install -g pnpm

# Copia solo los archivos necesarios desde la imagen de construcción
COPY --from=builder /app/dist ./dist
COPY --from=builder /app/node_modules ./node_modules
COPY --from=builder /app/package.json ./

# Expone el puerto 3000
EXPOSE 3000

# Comando para iniciar la API
CMD ["pnpm", "start:prod"]
