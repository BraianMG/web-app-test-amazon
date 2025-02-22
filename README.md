# Web App (Test despliegues en Amazon)

Pequeña web app que consta de una [UI](/ui/) en React y una [API](/api/) en Nest para hacer pruebas de despliegues en AWS.

## Comandos

```sh
# Construir y levantar contenedores
$ docker-compose up --build

# Levantar API para desarrollo
$ pnpm start:dev

# Levantar UI para desarrollo
$ pnpm dev

# API en http://127.0.0.1:3000
# UI en http://127.0.0.1:8080
```

## Tecnologías

- React
- Nest
- Docker
- Docker Compose
- Git
- GitHub
- GitHub Action
- Amazon EC2
