
# Programa en Workshops (5×8 h = 40 h) — .NET 8 / ASP.NET Core Web API (desde cero)
**Versión:** 2025-09-22  
**Formato:** 5 workshops de **8 horas** cada uno (con descansos planificados)  
**Stack:** .NET 8, ASP.NET Core (Controllers), Dapper, JWT, FluentValidation, Serilog, SQL Server

---

## Visión general
Cada workshop es **autocontenible**: breve teoría, setup guiado y **laboratorios** prácticos. Al finalizar el W5, el estudiante entrega una **API REST productiva y segura**, con datos en SQL (Dapper), autenticación JWT, validaciones y despliegue a IIS/Azure.

---

## Prework (antes del W1)
- Instalar **.NET 8 SDK**, **VS 2022** o **VS Code** + extensión C#.
- Instalar **SQL Server** (o Docker SQL) + **Azure Data Studio/SSMS**.
- Crear cuenta GitHub y tener **Git** instalado.
- Postman o Insomnia.
- Clonar repo plantillas (se proveerá en el W1).

---

## W1 — Fundamentos C# + ASP.NET Core Base (8 h)
**Objetivo:** arrancar desde cero con C# moderno y levantar la primera Web API con buenas bases.

**Agenda**
- (0:30) Bienvenida, objetivos, overview REST/HTTP.
- (2:00) C# Essentials: tipos, colecciones, nullability (`?`, `??`, `?.`), pattern matching, registros vs clases.
- (1:30) POO: clases/constructores, encapsulación, interfaces/abstractas, herencia y polimorfismo.
- (1:30) ASP.NET Core architecture: hosting, DI, middleware/pipeline; Controllers vs Minimal APIs.
- (0:45) Swagger/OpenAPI, convenciones de rutas y status codes.
- (0:45) Laboratorio integrador W1.

**Lab W1 (entregable)**
- Solución **ApiCourse** con proyecto `Api` (Web API).
- Endpoint `/health` + CRUD en memoria `Items` (Controllers).
- Respuestas coherentes (envelope simple) + Swagger habilitado.

---

## W2 — Routing, Respuestas, Errores y Asincronía (8 h)
**Objetivo:** diseñar contratos REST sólidos, manejo de errores centralizado y `async/await` end-to-end.

**Agenda**
- (1:15) Routing por atributos, verbos HTTP, convención de nombres (recursos/colecciones).
- (1:15) `IActionResult` vs tipos genéricos; status codes; respuestas paginadas.
- (1:30) Manejo de excepciones: filtros vs middleware global; modelo de error.
- (2:00) Asincronía: `Task`/`ValueTask`, cancelación (`CancellationToken`), I/O bound vs CPU bound.
- (2:00) Laboratorio W2.

**Lab W2 (entregable)**
- Middleware de error global + contrato de error JSON.
- CRUD en memoria migrado a **async** con cancelación.
- Paginación y filtros en endpoints (query params).

---

## W3 — Datos con Dapper (8 h)
**Objetivo:** persistir datos en SQL con Dapper, consultas parametrizadas, multi-mapping y transacciones.

**Agenda**
- (1:00) Setup conexión (`IDbConnection`, `SqlConnection`), buenas prácticas de cadena de conexión.
- (1:45) Queries: `Query`, `QueryFirstOrDefault`, `Execute`; parámetros anónimos y seguridad SQL.
- (1:30) Multi-mapping (1–N) y proyecciones DTO.
- (1:00) Transacciones: `BeginTransaction`, commit/rollback.
- (0:45) Paginación/orden/filtrado a nivel SQL.
- (2:00) Laboratorio W3.

**Lab W3 (entregable)**
- Capa `Infrastructure` con repositorio Dapper para 1–2 recursos.
- Servicios de aplicación con operaciones CRUD + filtros/paginación.
- Script SQL inicial + seed de datos.

---

## W4 — Patrones + Seguridad + Calidad (8 h)
**Objetivo:** aplicar patrones clave, asegurar la API con JWT y mejorar calidad (validaciones/logging/config).

**Agenda**
- (1:00) Repository + Unit of Work **light**; DTOs; (opcional) mapeo manual.
- (2:15) JWT: generación/validación, claims/roles, políticas; **CORS**.
- (1:15) Validaciones: DataAnnotations y **FluentValidation**.
- (1:00) Logging: `ILogger`, **Serilog**; correlación y trazabilidad.
- (0:45) Configuración: `appsettings`, variables de entorno, Secret Manager.
- (1:45) Laboratorio W4.

**Lab W4 (entregable)**
- Endpoints protegidos por **roles/políticas** + CORS.
- Validaciones de entrada con FluentValidation (filtro global).
- Serilog configurado + manejo de correlación de requests.

---

## W5 — Testing + Despliegue (8 h)
**Objetivo:** pruebas (unit e integración), CI/CD básico y despliegue a IIS/Azure App Service.

**Agenda**
- (1:45) Unit tests con xUnit/NUnit, Moq para dobles de prueba.
- (1:45) Integration tests con `WebApplicationFactory` / TestServer.
- (1:30) CI/CD: GitHub Actions (build+test+publish).
- (1:00) Despliegue a IIS (hosting bundle) y Azure App Service (variables, slots).
- (2:00) Laboratorio W5 + Demo final.

**Lab W5 (entregable)**
- 2–3 pruebas unitarias + 1 prueba de integración real.
- Pipeline YAML que build/test/publish la API.
- Publicación a IIS o App Service y verificación en Postman.

---

## Criterios de evaluación
- Entregables de cada workshop (W1–W5): **50%**
- Proyecto final (API funcional con seguridad y datos): **40%**
- Presentación/demo final: **10%**

**Rúbrica del proyecto** (resumen): Diseño/limpieza (SOLID) 25% · Calidad (errores, validaciones, logs) 25% · Seguridad (JWT/roles/CORS) 20% · Datos (Dapper, SQL, paginación) 20% · Operación (tests, deploy, docs) 10%

---

## Repositorio y estructura 
```
/ApiCourse
  /src
    /Api                # ASP.NET Core Web API
    /Application        # Servicios, DTOs, validadores
    /Infrastructure     # Dapper, repos, SQL scripts
    /Domain             # Entidades simples
  /tests
    /Api.Tests          # Unit + Integration
  /docs
    endpoints.md
    deployment.md
```

## Paquetes a utilizar
- `Swashbuckle.AspNetCore` (Swagger/OpenAPI)
- `Dapper`, `Microsoft.Data.SqlClient`
- `FluentValidation.AspNetCore`
- `Microsoft.AspNetCore.Authentication.JwtBearer`
- `Serilog.AspNetCore` (+ sinks)
- `xunit`, `Moq`, `Microsoft.AspNetCore.Mvc.Testing`

---

## Checklist de cierre (al terminar W5)
- [ ] CRUDs clave con filtros/paginación async.
- [ ] Dapper con transacciones y multi-mapping.
- [ ] Seguridad JWT + roles; CORS correcto.
- [ ] Validaciones + middleware de errores.
- [ ] Serilog + correlación de requests.
- [ ] Tests (unit e integración) pasando.
- [ ] Pipeline YAML funcionando.
- [ ] API desplegada (IIS o Azure App Service).

