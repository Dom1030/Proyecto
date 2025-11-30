# Proyecto Completo: Auth System y Store App

Este proyecto consta de dos partes principales: un backend de autenticación (`auth-system-backend`) y una aplicación frontend de tienda (`my-store-app`). El backend proporciona una API para autenticación de usuarios utilizando MySQL, Sequelize, JWT y bcrypt. El frontend es una aplicación React construida con Vite y Tailwind CSS, que puede consumir la API del backend.

## Requisitos Previos

- **Node.js** instalado (versión 16 o superior recomendada).
- **MySQL** instalado y corriendo en tu sistema.
- Crear una base de datos en MySQL llamada `auth_db` (o el nombre que configures en el archivo `.env`).

## auth-system-backend (Backend de Autenticación)

### Instalación

1. Navega al directorio del backend:
   ```
   cd auth-system-backend
   ```

2. Instala las dependencias:
   ```
   npm install
   ```

### Configuración

3. Crea un archivo `.env` en la raíz del directorio `auth-system-backend` con las siguientes variables de entorno (ajusta los valores según tu configuración de MySQL):
   ```
   DB_NAME=auth_db
   DB_USER=root
   DB_PASSWORD=
   DB_HOST=localhost
   DB_PORT=3306
   JWT_SECRET=mi_secreto_super_seguro_para_jwt
   JWT_EXPIRES_IN=1h
   PORT=3001
   ```

   - `DB_NAME`: Nombre de la base de datos MySQL.
   - `DB_USER`: Usuario de MySQL (por defecto `root`).
   - `DB_PASSWORD`: Contraseña de MySQL (deja vacío si no hay contraseña).
   - `DB_HOST`: Host de MySQL (generalmente `localhost`).
   - `DB_PORT`: Puerto de MySQL (por defecto `3306`).
   - `JWT_SECRET`: Secreto para firmar los tokens JWT (usa un valor seguro en producción).
   - `JWT_EXPIRES_IN`: Tiempo de expiración del token (ej. `1h` para 1 hora).
   - `PORT`: Puerto en el que correrá el servidor (por defecto `3001`).

### Ejecución

4. Ejecuta el servidor en modo desarrollo:
   ```
   npm run dev
   ```

   El servidor se iniciará y sincronizará los modelos con la base de datos. Deberías ver mensajes en la consola indicando que la conexión a MySQL se estableció correctamente y que los modelos se sincronizaron.

5. Opcional: Crea un usuario de prueba ejecutando:
   ```
   npm run create-user
   ```

   Esto creará un usuario con email `admin@example.com` y contraseña `password123` (la contraseña ya está hasheada en el seeder).

El backend estará disponible en `http://localhost:3001`. Puedes probar los endpoints:
- `GET /`: Verifica que el servidor esté funcionando.
- `POST /api/v1/auth/register`: Registra un nuevo usuario.
- `POST /api/v1/auth/login`: Inicia sesión.

## my-store-app (Aplicación Frontend de Tienda)

### Instalación

1. Navega al directorio del frontend:
   ```
   cd my-store-app
   ```

2. Instala las dependencias:
   ```
   npm install
   ```

### Ejecución

3. Ejecuta el servidor de desarrollo:
   ```
   npm run dev
   ```

   La aplicación se abrirá en `http://localhost:5173` (puerto por defecto de Vite). Puedes acceder desde tu navegador.

## Uso General

- Asegúrate de que el backend esté corriendo antes de usar el frontend.
- El frontend puede hacer solicitudes HTTP al backend usando Axios para autenticación.
- Para producción, construye el frontend con `npm run build` y sirve los archivos estáticos.
- Recuerda configurar variables de entorno seguras y no commitear el archivo `.env` al repositorio (ya está en `.gitignore`).

## Notas Adicionales

- Si encuentras errores de conexión a MySQL, verifica que el servicio esté corriendo y que las credenciales en `.env` sean correctas.
- Los modelos de la base de datos se sincronizan automáticamente al iniciar el servidor (con `alter: true` para modificar tablas si es necesario).
- El frontend incluye Tailwind CSS para estilos y ESLint para linting.


