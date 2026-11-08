# Aegis

## Sobre el Proyecto

Aegis es el servidor backend centralizado para [Zenith](https://zenith-delta-dusky.vercel.app) y [Nova](https://nova-one-black.vercel.app/), diseñado para gestionar la lógica de negocio y los servicios compartidos de ambos sistemas.

Desarrollado con Bun, Express.js y TypeScript, proporciona una arquitectura modular para la gestión de productos, inventario, ventas y otros servicios. Utiliza Zod para la validación de datos y LibSQL (Turso) para la persistencia.

## Stack Tecnológico

- **Runtime:** Bun
- **Framework:** Express.js
- **Base de datos:** LibSQL / Turso
- **Validación de esquemas:** Zod
- **Lenguaje:** TypeScript

## Configuración y Ejecución Local

### Prerrequisitos

- Tener instalado Bun o pnpm.

### 1. Clonar e instalar dependencias

```sh
git clone --depth 1 https://github.com/Ubiufboeuf/aegis
cd aegis
bun install # o pnpm install
```

### 2. Configurar las Variables de Entorno

Crea un archivo `.env` con las variables necesarias para el entorno de desarrollo o producción:

```dotenv
TURSO_DATABASE_URL='tu_url_de_turso'
TURSO_AUTH_TOKEN='tu_token_de_turso'
LOCAL_DATABASE_URL='file:zenith.db'

PORT=8080
DB='local' # o 'prod'. Indica qué BD usar

ENV_ORIGINS='http://localhost:5173'
```

### 3. Ejecutar en modo desarrollo

Para iniciar el servidor en desarrollo, ejecuta:

```sh
bun run dev
```

## Arquitectura

Aegis centraliza los servicios compartidos por Zenith y Nova, permitiendo que ambas aplicaciones utilicen una misma fuente de datos sin duplicar la lógica de negocio.

- **Zenith:** Sistema de gestión comercial, inventario y punto de venta.
- **Nova:** Plataforma de comercio electrónico.
- **Aegis:** Servidor encargado de procesar solicitudes, aplicar reglas de negocio y gestionar la persistencia de datos.

Esta arquitectura permite desarrollar y desplegar los clientes de forma independiente, manteniendo una lógica de negocio centralizada y extensible.

## Despliegue

Aegis está preparado para ejecutarse en entornos cloud mediante contenedores. Actualmente se encuentra desplegado en Railway, utilizando Turso como base de datos de producción.

## Licencia

Este proyecto está bajo la licencia [MIT](LICENSE.md).
