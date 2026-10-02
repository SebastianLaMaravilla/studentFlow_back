# Skill de IA: Guía Estándar para Adicionar un Endpoint GET de Sub-recurso

## Objetivo
Instruir a la Inteligencia Artificial para que añada de forma automatizada y estructurada un nuevo endpoint de tipo `GET` que consulte sub-recursos asociados a un recurso principal, respetando estrictamente la arquitectura en capas, las anotaciones JSDoc y la seguridad por ID de usuario (`userId`).

## Patrón de Arquitectura en Capas (Flujo de Datos)
1. **Capa de Repositorio** (`src/repositories/`)
2. **Capa de Servicio** (`src/services/`)
3. **Capa de Controlador** (`src/controllers/`)
4. **Capa de Rutas** (`src/routes/`)

## Paso 1: Capa de Repositorio
- **Ubicación:** `src/repositories/materias.repositorio.js`
- **Propósito:** Ejecutar la consulta SQL con `INNER JOIN` para blindar la consulta por `userId`.

## Paso 2: Capa de Servicio
- **Ubicación:** `src/services/materias.service.js`
- **Propósito:** Validar que la materia exista y pertenezca al usuario antes de pedir los datos al repositorio.

## Paso 3: Capa de Controlador
- **Ubicación:** `src/controllers/materias.controller.js`
- **Propósito:** Extraer y validar el `params.id`, invocar el servicio y responder con `sendSuccess`.

## Paso 4: Capa de Rutas
- **Ubicación:** `src/routes/materias.routes.js`
- **Propósito:** Exponer el endpoint bajo `router.get("/:id/subrecurso", controlador)`.