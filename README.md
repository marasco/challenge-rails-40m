# 🚀 Rails Challenge: API de Autos con Autenticación y Favoritos

## 🧩 Objetivo

Crear una API en Ruby on Rails que permita a usuarios registrarse, iniciar sesión, listar autos y marcarlos como favoritos. Lo requerido si o si es la parte de APIs, si hay vistas, mucho mejor.

---

## 🔐 Autenticación

- `POST /register` → Registro de usuario con email y contraseña
- `POST /login` → Login que devuelve un JWT válido
- Autenticación mediante JWT (token en el header: `Authorization: Bearer <token>`)
- Usar `has_secure_password` y la gema `bcrypt`
- Middleware (`before_action`) que proteja rutas privadas como `/cars` y `/favorites`

---

## 🚘 Listado de Autos

- `GET /cars` devuelve un array con todos los autos
- `GET /cars?brand=Toyota` filtra por marca
- Solo accesible si el usuario está autenticado

---

## ⭐ Favoritos

- Los usuarios pueden marcar autos como favoritos
- Rutas adicionales:
  - `POST /favorites` → agregar un auto a favoritos (enviar `car_id`)
  - `GET /favorites` → ver autos favoritos del usuario autenticado
  - `DELETE /favorites/:id` → quitar un auto de favoritos
- Asociación muchos-a-muchos entre `User` y `Car` (a través de `Favorite`)

---

## 🧱 Base de Datos

- SQLite o la que elijas.
- Modelo `User`: `email:string`, `password_digest:string`
- Modelo `Car`: `brand:string`, `model:string`, `year:integer`
- Modelo `Favorite`: `user_id`, `car_id` (índices únicos por combinación)
- `db/seeds.rb`: al menos 5 autos de distintas marcas

---

## ⚙️ Tech Stack

- Ruby on Rails
- Validaciones básicas en los modelos

---

## 📦 Entregable

- Código del proyecto (GitHub público)
- `README.md` con:
  - Pasos para instalación y ejecución (`rails db:setup`, etc.)
  - Comandos de prueba con `curl` o colección de Postman

---

## 🧪 Comandos de ejemplo

### Registro
```bash
curl -X POST http://localhost:3000/register \
  -H "Content-Type: application/json" \
  -d '{"email":"test@example.com", "password":"123456"}'

### * Se valorarán:
- Prioridad al elegir features 
- Cualquier agregado no solicitado que de valor al entregable, por ejemplo, que se pueda usar desde google chrome y no solo via Postman o Curl (con vistas)
- Loom video o similar mostrando como se usa y se prueba, explicando claramente el objetivo. Si hay video, se contemplarán 10 minutos más al entregable.
