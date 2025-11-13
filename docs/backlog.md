# Backlog Oficial — CofradíaGo

**Versión:** Backlog completo inicial  
**Propósito:** Registro oficial de épicas y Historias de Usuario (HU). Usar para crear Issues y planificar sprints.

---

## Épicas (alto nivel)

- **E1 — Configuración Inicial y Base del Sistema**  
  Infraestructura: repos, CI, entornos `.env`, DB de desarrollo, templates, y guidelines.

- **E2 — Gestión de Hermandades**  
  CRUD de la hermandad, datos oficiales, normas y plantillas por hermandad.

- **E3 — Gestión de Hermanos**  
  Registro, importación, edición, historiales, listas de antigüedad.

- **E4 — Cortejo Procesional**  
  Tramos, posiciones, orden de salida, reglas de orden (antigüedad, edad, mixto), asignaciones.

- **E5 — Papeleta de Sitio Digital**  
  Solicitud, aprobación, generación PDF, plantillas personalizables por año.

- **E6 — Portal del Hermano** *(v2)*  
  Acceso personal, descarga de papeleta, actualización de datos y estado.

- **E7 — Panel del Diputado** *(v2)*  
  Dashboard operativo, control de día, listados, exportaciones.

- **E8 — Comunicación y Avisos** *(v2)*  
  Emails, avisos, templates, integración con WhatsApp/Telegram (opcional).

- **E9 — Multi-hermandad / Infraestructura** *(futuro)*  
  Multi-tenant, esquemas por tenant, backups y facturación SaaS.

- **E10 — Administración General** *(futuro)*  
  Gestión de superadmin, auditoría global, logs y controles.

---

## Historias de Usuario — MVP (HU-01 .. HU-19)

### HU-01 · E1 · Setup Frontend (React + Vite + Tailwind)
**Como** desarrollador  
**Quiero** una estructura base de frontend (React + Vite + Tailwind)  
**Para** arrancar el desarrollo del panel y portal.

**Criterios de aceptación**
- [ ] Proyecto Vite creado en `cofradiago-frontend`
- [ ] `pnpm install` y `pnpm run dev` funcionan
- [ ] README con comandos básicos

**Notas técnicas**
- Tipo: Frontend
- Milestone: M1 - Setup técnico
- Prioridad: High

---

### HU-02 · E1 · Setup Backend (NestJS + Prisma)
**Como** desarrollador  
**Quiero** un backend base en NestJS con Prisma y conexión a PostgreSQL  
**Para** exponer las APIs necesarias.

**Criterios de aceptación**
- [ ] Proyecto NestJS creado en `cofradiago-backend`
- [ ] `prisma/schema.prisma` inicial y `.env.example`
- [ ] `pnpm start:dev` funciona localmente

**Notas técnicas**
- Tipo: Backend
- Milestone: M1
- Prioridad: High

---

### HU-03 · E1 · `.env.example` y docs de setup
**Como** desarrollador  
**Quiero** un `.env.example` y una guía de setup en `docs/setup.md`  
**Para** que cualquier dev reproduzca el entorno local.

**Criterios**
- [ ] `.env.example` documentado en backend
- [ ] `docs/setup.md` en `cofradiago-docs`

**Notas**
- Milestone: M1
- Prioridad: High

---

### HU-04 · E1 · Scripts y CI básicos
**Como** equipo  
**Quiero** scripts de `package.json` (dev, build, test, lint) y CI simple en GitHub Actions  
**Para** automatizar checks en PRs.

**Criterios**
- [ ] `scripts` en ambos repos
- [ ] GH Actions workflow que ejecuta `pnpm install` y `pnpm test` (si aplica)

**Notas**
- Milestone: M1
- Prioridad: High

---

### HU-05 · E2 · Crear Hermandad (CRUD)
**Como** Diputado  
**Quiero** crear la ficha de mi Hermandad (nombre, escudo, sede, colores)  
**Para** registrar la entidad en el sistema.

**Criterios**
- [ ] Endpoint POST `/api/hermandades`
- [ ] UI formulario en frontend
- [ ] Validaciones básicas (nombre obligatorio)

**Notas**
- Milestone: M2 - Configuración Hermandad
- Prioridad: High

---

### HU-06 · E2 · Editar/Eliminar Hermandad
**Como** Diputado  
**Quiero** editar o eliminar la ficha de la Hermandad  
**Para** mantener los datos actualizados.

**Criterios**
- [ ] Endpoints PUT `/api/hermandades/:id`, DELETE `/api/hermandades/:id`
- [ ] UI para edición y eliminación segura (confirm)

**Notas**
- Milestone: M2
- Prioridad: High

---

### HU-07 · E2 · Configurar reglas del cortejo
**Como** Diputado  
**Quiero** definir las reglas del orden del cortejo (antigüedad, edad, mixto, listas)  
**Para** que la generación automática respete las normas de mi hermandad.

**Criterios**
- [ ] UI para seleccionar regla (antigüedad / edad / mixto)
- [ ] API para persistir `reglas_cortejo` por hermandad
- [ ] Documentación de la lógica (docs)

**Notas**
- Milestone: M2
- Prioridad: High

---

### HU-08 · E2 · Definir cargos y puestos
**Como** Diputado  
**Quiero** definir cargos (capataz, acólito, costalero, etc.) y puestos por tramo  
**Para** estructurar el cortejo y poder asignar personas.

**Criterios**
- [ ] CRUD de cargos/puestos
- [ ] UI para añadir/editar puestos en tramos

**Notas**
- Milestone: M2
- Prioridad: High

---

### HU-09 · E3 · Importar hermanos (CSV/XLSX)
**Como** Diputado  
**Quiero** importar listados de hermanos por CSV/XLSX  
**Para** poblar la base de datos rápidamente.

**Criterios**
- [ ] Endpoint / UI para importar con mapeo de columnas
- [ ] Validaciones de duplicados y reporte de errores
- [ ] Evento log de importación

**Notas**
- Milestone: M3 - Cortejo y Hermanos
- Prioridad: High

---

### HU-10 · E3 · Editar ficha de hermano
**Como** Diputado  
**Quiero** editar datos personales de un hermano (nombre, DNI opcional, antigüedad, fecha de alta)  
**Para** mantener registros exactos.

**Criterios**
- [ ] CRUD de `hermano`
- [ ] Auditoría (quién editó y cuándo)

**Notas**
- Milestone: M3
- Prioridad: High

---

### HU-11 · E3 · Asignar tramo/puesto a hermano
**Como** Diputado  
**Quiero** asignar manualmente un hermano a una posición concreta en el cortejo  
**Para** completar la distribución final del cortejo.

**Criterios**
- [ ] Endpoint para asignación `/api/posiciones/:id/assign`
- [ ] UI con drag & drop o selector
- [ ] Registro de cambios (evento_log)

**Notas**
- Milestone: M3
- Prioridad: High

---

### HU-12 · E3 · Vista perfil hermano (readonly)
**Como** Hermano  
**Quiero** ver mi ficha con historial y número de antigüedad (solo lectura)  
**Para** comprobar mis datos.

**Criterios**
- [ ] UI pública desde Portal o vista en Admin
- [ ] Muestra historial de participación y antigüedad

**Notas**
- Milestone: M3
- Prioridad: Medium

---

### HU-13 · E4 · Crear tramos y ordenar cortejo
**Como** Diputado  
**Quiero** crear tramos, ordenarlos y visualizar la secuencia del cortejo  
**Para** planificar el orden de salida.

**Criterios**
- [ ] CRUD tramos
- [ ] Reordenamiento (drag & drop) en UI
- [ ] Persistencia del orden

**Notas**
- Milestone: M3
- Prioridad: High

---

### HU-14 · E4 · Asignar hermanos a tramos (masivo)
**Como** Diputado  
**Quiero** asignar hermanos a tramos masivamente (p. ej. importar asignaciones)  
**Para** ahorrar tiempo en el montaje.

**Criterios**
- [ ] Upload de CSV con `hermano_id` + `tramo_id`
- [ ] Resultado con resumen de cambios aceptados y rechazados

**Notas**
- Milestone: M3
- Prioridad: Medium

---

### HU-15 · E4 · Exportar plan del cortejo (PDF/Excel)
**Como** Diputado  
**Quiero** exportar el plan del cortejo en PDF y Excel (Libro de Orden)  
**Para** imprimir y usar en administración.

**Criterios**
- [ ] Generación de PDF con plantilla básica
- [ ] Exportar Excel/CSV con columnas relevantes
- [ ] Guardado del documento en `documentos` con metadata

**Notas**
- Milestone: M3
- Prioridad: High

---

### HU-16 · E5 · Solicitud de papeleta (formulario público/protegido)
**Como** Hermano  
**Quiero** solicitar mi papeleta de sitio online con mis datos y preferencia de puesto  
**Para** agilizar el proceso y evitar desplazamientos.

**Criterios**
- [ ] Form con validaciones (email + datos mínimos)
- [ ] Registro de solicitud en estado `pendiente`
- [ ] Envío confirmación por email (opcional en MVP)

**Notas**
- Milestone: M4 - Papeleta Digital
- Prioridad: High

---

### HU-17 · E5 · Aprobar/Rechazar papeletas (workflow)
**Como** Diputado  
**Quiero** revisar solicitudes y aprobar/rechazar papeletas con comentarios  
**Para** gestionar el cortejo y mantener trazabilidad.

**Criterios**
- [ ] Cambio de estado `pendiente` → `aprobada`/`rechazada`
- [ ] Notificación interna del cambio (registro)
- [ ] Registro del motivo en caso de rechazo

**Notas**
- Milestone: M4
- Prioridad: High

---

### HU-18 · E5 · Generar papeleta PDF (plantilla anual)
**Como** Hermano  
**Quiero** recibir mi papeleta en PDF personalizada con el diseño del año  
**Para** presentarla impresa o mostrada en dispositivos.

**Criterios**
- [ ] Motor de templates HTML → PDF (Puppeteer o similar)
- [ ] Plantillas por hermandad + por año
- [ ] PDF incluye QR con firma/verificación

**Notas**
- Milestone: M4
- Prioridad: High

---

### HU-19 · E5 · Listado de papeletas emitidas
**Como** Diputado  
**Quiero** listar y filtrar papeletas por estado, año y hermano  
**Para** controlar la logística y recaudación.

**Criterios**
- [ ] Tabla con filtros (estado, año, tramo)
- [ ] Export CSV de papeletas seleccionadas

**Notas**
- Milestone: M4
- Prioridad: High

---

## Historias de Usuario — Versión 2 (HU-20 .. HU-26)

### HU-20 · E6 · Login Hermano (Portal)
**Como** Hermano  
**Quiero** poder iniciar sesión con email/contraseña y ver mi panel  
**Para** acceder a mis papeletas y estado.

**Criterios**
- [ ] Auth JWT para portal
- [ ] Vista de panel con papeletas

**Notas**
- Prioridad: Medium
- Milestone: M5 - MVP Release

---

### HU-21 · E6 · Edición de datos personales (Portal)
**Como** Hermano  
**Quiero** actualizar mi teléfono, talla y observaciones médicas  
**Para** mantener mis datos actualizados.

**Criterios**
- [ ] Form de edición con validaciones
- [ ] Registro de cambios (audit)

**Notas**
- Prioridad: Medium

---

### HU-22 · E6 · Notificaciones básicas en portal
**Como** Hermano  
**Quiero** recibir mensajes sobre el estado de mi papeleta (interno)  
**Para** estar informado sin email.

**Criterios**
- [ ] Bandeja de mensajes en portal (simple)
- [ ] Notificación visible cuando hay nuevas comunicaciones

**Notas**
- Prioridad: Medium

---

### HU-23 · E7 · Dashboard Diputado (resumen)
**Como** Diputado  
**Quiero** un panel con totales (nº nazarenos, papeletas, tramos)  
**Para** tener una visión rápida del estado.

**Criterios**
- [ ] Widgets: totales, gráficos básicos
- [ ] Link rápido a hojas de gestión

**Notas**
- Prioridad: Medium

---

### HU-24 · E7 · Control en vivo (día de procesión)
**Como** Diputado  
**Quiero** ver en tiempo real retrasos/avisos por tramo (básico)  
**Para** gestionar incidencias el día del evento.

**Criterios**
- [ ] Módulo simple de estado por tramo (ok/retraso)
- [ ] Registro de incidencias

**Notas**
- Prioridad: Medium

---

### HU-25 · E8 · Envío de comunicados (email)
**Como** Diputado  
**Quiero** enviar comunicados masivos por email a hermanos (plantillas)  
**Para** convocatorias y avisos.

**Criterios**
- [ ] Interfaz de envío con plantilla
- [ ] Log de envíos

**Notas**
- Prioridad: Medium

---

### HU-26 · E8 · Integración con WhatsApp/Telegram (opcional)
**Como** Diputado  
**Quiero** avisar por WhatsApp o Telegram (opcional)  
**Para** llegada inmediata de avisos (futuros integradores).

**Criterios**
- [ ] Diseño de integración (prototipo)
- [ ] Opcional: envío de prueba con provider

**Notas**
- Prioridad: Low

---

## Historias de Usuario — Futuro / Escalado (HU-27 .. HU-30)

### HU-27 · E9 · Soporte multi-hermandad (multi-tenant)
**Como** Administrador  
**Quiero** permitir que varias hermandades usen la plataforma con aislamiento lógico  
**Para** ofrecer servicio SaaS.

**Criterios**
- [ ] Diseño multi-tenant por `tenant_id` (MVP) o por `schema` (futuro)
- [ ] Documentación de migración

**Notas**
- Prioridad: Low

---

### HU-28 · E9 · Exportaciones y backups
**Como** Administrador  
**Quiero** exportar datos y configurar backups automáticos  
**Para** seguridad y recuperación.

**Criterios**
- [ ] Export JSON/CSV por hermandad
- [ ] Cron de backups y restauración documentada

**Notas**
- Prioridad: Low

---

### HU-29 · E10 · Gestión global de permisos (Superadmin)
**Como** Superadmin  
**Quiero** gestionar permisos globales y roles por organización  
**Para** administrar la plataforma.

**Criterios**
- [ ] CRUD de roles y permisos globales
- [ ] UI de administración básica

**Notas**
- Prioridad: Low

---

### HU-30 · E10 · Auditoría y logs
**Como** Administrador  
**Quiero** logs de auditoría de acciones críticas (asignaciones, cambios de estado)  
**Para** trazabilidad y cumplimiento.

**Criterios**
- [ ] Tabla de `evento_log`
- [ ] Interfaz de filtrado por entidad/usuario/fecha

**Notas**
- Prioridad: Low

---

*Fin del backlog completo.*
