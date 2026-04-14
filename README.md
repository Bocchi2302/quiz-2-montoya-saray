# Quiz 2 - API completa (User, Doctor, Hospital)

Proyecto listo para el requerimiento del último tablero:

- **User**: id, username, password, role
- **Roles**: `ADMIN`, `DOCTOR`
- **Doctor**: id, username asociado, name, lastName, age, specialization, hospitalId
- **Hospital**: id, name
- Endpoint especial **`GET /api/doctors/me`** usando `SecurityContextHolder`
- Seguridad con **JWT**
- CRUD completo de **Hospital**
- Validación para asegurar que el usuario asociado al doctor tenga rol **DOCTOR**

## Requisitos
- Java 17
- Maven 3.9+ o usar `./mvnw`

## Ejecutar
En Windows:
```bash
mvnw.cmd spring-boot:run
```

En Linux/Mac:
```bash
./mvnw spring-boot:run
```

## Usuario ADMIN inicial
Al iniciar por primera vez se crea automáticamente:

- username: `admin`
- password: `Admin123*`

## Endpoints principales

### Auth
- `POST /api/auth/signup`
- `POST /api/auth/login`

### Hospital
- `POST /api/hospitals`
- `GET /api/hospitals`
- `GET /api/hospitals/{id}`
- `PUT /api/hospitals/{id}`
- `DELETE /api/hospitals/{id}`

### Doctor
- `POST /api/doctors`
- `GET /api/doctors`
- `GET /api/doctors/{id}`
- `GET /api/doctors/me`

## Flujo recomendado para el quiz
- `main`
- `dev`
- `feature/security`
- `feature/crud-hospital`

## Ejemplos rápidos

### 1. Login ADMIN
```json
POST /api/auth/login
{
  "username": "admin",
  "password": "Admin123*"
}
```

### 2. Registrar usuario doctor
```json
POST /api/auth/signup
{
  "username": "doctor1",
  "password": "Doctor123*",
  "role": "DOCTOR"
}
```

### 3. Crear hospital con token ADMIN
```json
POST /api/hospitals
{
  "name": "Hospital Central"
}
```

### 4. Crear doctor con token ADMIN
```json
POST /api/doctors
{
  "username": "doctor1",
  "name": "Laura",
  "lastName": "Gomez",
  "age": 34,
  "specialization": "Cardiologia",
  "hospitalId": 1
}
```

### 5. Login doctor
```json
POST /api/auth/login
{
  "username": "doctor1",
  "password": "Doctor123*"
}
```

### 6. Consultar perfil del doctor autenticado
```json
GET /api/doctors/me
Authorization: Bearer <token_doctor>
```

## Notas
- La base usa **H2 en archivo**, no en memoria, para que no se pierdan los datos al reiniciar.
- La consola H2 queda disponible en:
  - `http://localhost:8080/h2-console`
- JDBC URL:
  - `jdbc:h2:file:./data/quiz2db`
