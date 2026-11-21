# Changelog

Cambios realizados a las especificaciones publicadas en SwaggerHub. / Change log for the specifications published on SwaggerHub.

- **DMS-Guide** (`DMS-Guide/openapi.yaml`) → SwaggerHub `openapi-cmos/DMS-ERP`
- **Product-API** (`Product-API/openapi.yaml`) → SwaggerHub `openapi-cmos/CMOS-Clear-ProductAPI`

Las entradas más recientes van primero. / Newest entries first.

---

## DMS-Guide

### 4.0.0

- **Contrato / Contract:**
  - `GET /operationCodes`: el esquema de respuesta era una copia del de ofertas; ahora cada elemento de `data` es `{operationCode, description, hours}`. / The response schema was a copy of the offers schema; each `data` item is now `{operationCode, description, hours}`.
  - `GET /operationCodes`: el parámetro de query `oeprationCode` se corrige a `operationCode`. / Query parameter `oeprationCode` fixed to `operationCode`.
  - `POST /quotes` y `POST /inspectionItemsQuotes` (respuesta): el campo `avalibility` se renombra a `availability`. / Response field `avalibility` renamed to `availability`.
  - `availability` es `number` (entero o decimal) en todas las solicitudes y respuestas. / `availability` is `number` (integer or decimal) in every request and response.
  - `POST /inspectionItemsQuotes` (respuesta): `quoteId` y `customerId` son `string`, igual que en `POST /quotes`. / `quoteId` and `customerId` are `string`, same as `POST /quotes`.
  - Prioridad de artículos de cotización: valores `Low`, `Med`, `Urgent`, `NA`. / Quote item priority values: `Low`, `Med`, `Urgent`, `NA`.

- **Textos / Texts:** corrección de ortografía, descripciones copiadas que no correspondían al endpoint, contradicciones entre español e inglés; versión bilingüe completa ("Español. / English.") en todas las descripciones.
- **Terminología / Terminology:** "motivo de visita" (no "razón de visita"), "ClearMechanic" (no "CM"), "cliente final" / "final customer", "Estatus", "Placas", "artículo", "software de terceros"; "técnico" y "asesor de servicio" en minúsculas.
- **Estructura / Structure:**
  - Nuevos componentes / New components: `parameters/OrganizationIdHeader`, `responses/JobNotFound`, `responses/TaskNotFound`, `schemas/Appointment`, `schemas/Order`, `schemas/Task`, `schemas/TaskRequest`, `schemas/TaskResult`.
  - Respuestas de error 400/404/500 y esquemas repetidos referenciados con `$ref`. / Repeated 400/404/500 error responses and copied schemas now use `$ref`.
  - `GET /orders/{orderNumber}` documenta ahora `checkin` y `checkout` (opcionales), igual que `GET /orders`. / now documents the optional `checkin` and `checkout` fields, same as `GET /orders`.
- **Enums:** estatus documentados como `enum` (citas, garantías, campañas, prioridad/estatus de artículos de cotización, estatus/acción de trabajos del Planeador de Taller, `approvalStatus` de Puntos de Inspección). Ejemplos ajustados a esos valores.
- **operationId:** `postUnspectionItemsQuotes` → `postInspectionItemsQuotes`; `*EstimateByOrderId` → `*EstimateByOrderNumber`; `getOrderById` / `updateOrderById` → `getOrderByOrderNumber` / `updateOrderByOrderNumber`.
- **Ejemplos / Examples:** valores `string` entre comillas (fechas, identificadores); fecha inválida corregida; ejemplo de `GET /operationCodes` renombrado a "Código de operación".
- **info:** título y descripción en inglés, `license` agregada, `externalDocs` apunta a este archivo (antes un Google Doc).

### 1.2.5 — 2022-02-11

Se agregan nuevos recursos:

- `GET /inventoryItems` — obtiene el listado de los objetos en el sistema de inventarios de un software de terceros.
- `GET /inventoryItems/{itemId}` — obtiene el detalle de un objeto en el sistema de inventarios de un software de terceros.

### 1.2.4 — 2022-02-01

- `GET, POST, PUT /orders/{orderId}/estimates`
  - Schema: se elimina el parámetro `subItems`; se agregan `jobs`, `parts` y `labors`.
    - `jobs`: arreglo de trabajos; puede o no tener un listado de partes y de manos de obra.
    - `parts`: arreglo de partes.
    - `labors`: arreglo de manos de obra.
  - Example: se ajustan los ejemplos al nuevo schema.
- `GET /customers` — Example/Schema: el campo `clientId` cambia a `customerId`.
- `GET /advisors` — Example/Schema: el campo `advisorId` cambia a `serviceAdvisorId`.

### 1.2.3 — 2022-01-06

Se agrega nuevo recurso: `PUT /orders/{orderId}`.

### 1.2.2 — 2021-12-20

- Schemas: todos los formatos de fecha cambian de `YYYY-MM-DD HH:mm:ss` a `YYYY-MM-DDTHH:mm:ss.000Z`.
- `GET /appointments`
  - Example: el cuerpo de cada elemento del arreglo es el mismo que regresa `GET /appointments/{appointmentId}`.
  - Schema: el cuerpo es el mismo del detalle de una cita; `remarks` ahora se llama `comments`; se quitan `paternalName` y `maternalName` y se agrega `lastName`; `secondaryPhone`, `socialName`, `comments` y `orderTypeId` ya no son requeridos.
- `GET /appointments/{appointmentId}`
  - Example: `remarks` cambia a `comments`.
  - Schema: `remarks` ahora se llama `comments`; se quitan `paternalName` y `maternalName` y se agrega `lastName`; `secondaryPhone`, `socialName`, `comments` y `orderTypeId` ya no son requeridos.
- `GET /appointments/{appointmentId}/jobs`
  - Estructura del endpoint: antes era `GET /jobs?appointmentId=xxx`.
  - Schema: se describen correctamente los campos de la respuesta.
- `GET /orders`
  - Example: cada elemento del arreglo es igual al detalle de una orden.
  - Schema: `insuranceData` es un objeto con la información de la póliza de seguros; `orderNumber` se vuelve requerido.
- `POST /orders`
  - Example: la respuesta es igual a la del `GET /orders`.
  - Schema: se ajusta al ejemplo.
- Estimate — Schema: el campo `orderId` cambia a `orderNumber`.

---

## Product-API

_Sin entradas todavía. / No entries yet._
