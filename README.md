README.md — Auth Service
# Auth Service

Servicio de autenticación desarrollado con Laravel 11 utilizando Laravel Sanctum para autenticación basada en tokens.

Este microservicio permite:

- Inicio de sesión
- Obtención del usuario autenticado
- Cierre de sesión
- Protección de rutas mediante middleware

---

# Tecnologías utilizadas

- PHP 8.2
- Laravel 11
- Laravel Sanctum
- MySQL
- XAMPP
- Composer

---

# Arquitectura y decisiones técnicas

El servicio fue desarrollado utilizando el patrón MVC de Laravel:

- Models → manejo de datos
- Controllers → lógica de negocio
- Routes → definición de endpoints
- Middleware → protección de rutas

## Decisiones técnicas

### Laravel Sanctum

Se utilizó Sanctum debido a que:

- Es liviano
- Fácil de integrar
- Ideal para APIs REST
- Maneja autenticación por tokens

### MySQL

Se utilizó MySQL como motor de base de datos por simplicidad y rápida integración con Laravel.

### XAMPP

El entorno local fue configurado utilizando XAMPP para facilitar el desarrollo rápido.

### Docker

No se implementó Docker en esta etapa debido a que el alcance actual de la prueba técnica no lo requería.  
Sin embargo, el proyecto puede dockerizarse fácilmente si escala a un entorno más robusto.

---

# Endpoints principales

## Test API

### GET `/api/test`

Verifica que el servicio esté funcionando.

### Response

```json
{
  "message": "Auth Service Funcionando"
}
Login
POST /api/login

Autentica un usuario y genera un token.

Body
{
  "email": "admin@test.com",
  "password": "123456"
}
Response
{
  "token": "TOKEN_GENERADO"
}
Usuario autenticado
GET /api/me

Obtiene la información del usuario autenticado.

Headers
Authorization: Bearer TOKEN
Logout
POST /api/logout

Cierra la sesión eliminando el token actual.

Headers
Authorization: Bearer TOKEN
Variables de entorno

Configurar el archivo .env:

APP_NAME=AuthService
APP_ENV=local
APP_KEY=
APP_DEBUG=true
APP_URL=http://localhost

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=auth_service
DB_USERNAME=root
DB_PASSWORD=

SANCTUM_STATEFUL_DOMAINS=localhost
SESSION_DRIVER=file
Instalación y ejecución
1. Clonar repositorio
git clone URL_DEL_REPOSITORIO
2. Entrar al proyecto
cd auth-service
3. Instalar dependencias
composer install
4. Configurar variables de entorno
cp .env.example .env

Configurar conexión MySQL.

5. Generar APP_KEY
php artisan key:generate
6. Ejecutar migraciones
php artisan migrate
7. Levantar servidor
php artisan serve

Servidor:

http://127.0.0.1:8000
Middleware utilizado
auth:sanctum

Protege rutas autenticadas.

verify.token

Middleware personalizado utilizado para validar tokens en endpoints protegidos.

Estructura general
app/
 ├── Http/
 │   ├── Controllers/
 │   ├── Middleware/
 │
 ├── Models/

routes/
 ├── api.php
Autor: Rafael Hernandez Meza

Desarrollado como prueba técnica utilizando Laravel 11 y Sanctum.
