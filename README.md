# Entrega Actividad - API Sistema de Gestión de Estudiantes

**Estudiante:** Carolina Bolivar Rios  

Repositorio del proyecto:  
https://github.com/CarolinaBolivar5/26_b2_r1

---

# 1. Enlace a la instancia de la base de datos creada en Prisma

Instancia de base de datos PostgreSQL creada en Prisma:

https://console.prisma.io/cmm2pebhc00sozxebewdafyid/cmm2vleg801q0zteeb6iv10re/cmm2vq2w201t87heef9x4wktg/dashboard

---

# 2. Configuración de la base de datos en Prisma

Archivo `.env`

DB_URL=jdbc:postgresql://db.prisma.io:5432/postgres?sslmode=require  
DB_USERNAME=********  
DB_PASSWORD=******** 

Configuración en `application.properties`

spring.application.name=pi
spring.config.import=optional:file:.env[.properties]

spring.datasource.url=${DB_URL}
spring.datasource.username=${DB_USERNAME}
spring.datasource.password=${DB_PASSWORD}
spring.datasource.driver-class-name=org.postgresql.Driver

spring.jpa.database-platform=org.hibernate.dialect.PostgreSQLDialect
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true

---

# 3. Log de la consola de Spring Boot

Resultado al ejecutar la aplicación:

mvn spring-boot:run

Log:

[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 16.720 s
[INFO] Finished at: 2026-02-25
[INFO] ------------------------------------------------------------------------

Spring Boot iniciado correctamente en el puerto 8080.

---

# 4. Evidencia de las pruebas de la API (CRUD)

## Crear estudiante

curl -X POST http://localhost:8080/api/students -H "Content-Type: application/json" -d "{\"firstName\":\"Juan\",\"lastName\":\"Perez\",\"email\":\"juan@email.com\",\"birthDate\":\"2000-01-15\",\"phone\":\"123456789\"}"

Respuesta:

{
  "id": 1,
  "firstName": "Juan",
  "lastName": "Perez",
  "email": "juan@email.com",
  "birthDate": "2000-01-15",
  "phone": "123456789"
}

---

## Obtener todos los estudiantes

curl http://localhost:8080/api/students

Respuesta:

[
  {
    "id": 1,
    "firstName": "Juan",
    "lastName": "Perez",
    "email": "juan@email.com",
    "birthDate": "2000-01-15",
    "phone": "123456789"
  }
]

---

## Obtener estudiante por ID

curl http://localhost:8080/api/students/1

Respuesta:

{
  "id": 1,
  "firstName": "Juan",
  "lastName": "Perez",
  "email": "juan@email.com",
  "birthDate": "2000-01-15",
  "phone": "123456789"
}

---

## Actualizar estudiante

curl -X PUT http://localhost:8080/api/students/1 -H "Content-Type: application/json" -d "{\"firstName\":\"Juan Carlos\",\"lastName\":\"Perez\",\"email\":\"juan@email.com\",\"birthDate\":\"2000-01-15\",\"phone\":\"987654321\"}"

Respuesta:

{
  "id": 1,
  "firstName": "Juan Carlos",
  "lastName": "Perez",
  "email": "juan@email.com",
  "birthDate": "2000-01-15",
  "phone": "987654321"
}

---

## Eliminar estudiante

curl -X DELETE http://localhost:8080/api/students/1

Verificación:

curl http://localhost:8080/api/students

Respuesta:

[]

---

# 5. Resultado de la ejecución de las pruebas internas del proyecto

Comando ejecutado:

mvn test

Resultado:

[INFO] -------------------------------------------------------
[INFO] T E S T S
[INFO] -------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] -------------------------------------------------------
[INFO] Tests run: OK
[INFO] -------------------------------------------------------
