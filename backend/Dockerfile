# Stage 1: Build (Instalación de dependencias)
FROM node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install

# Stage 2: Producción (Imagen final ligera)
FROM node:18-alpine
WORKDIR /app

# Crear usuario non-root
RUN addgroup -S nodeuser && adduser -S nodeuser -G nodeuser

# Copiar solo los archivos necesarios desde el stage de build
COPY --from=builder /app/node_modules ./node_modules
COPY . .

# Ajustar permisos para el usuario
RUN chown -R nodeuser:nodeuser /app

# Cambiar al usuario non-root
USER nodeuser

EXPOSE 3001
CMD ["npm", "start"]