## 18. EJECUCIÓN DE TRABAJO / ENTREGA DEL BIEN

### 18.1. Objetivo del Módulo

Gestionar la ejecución de trabajos y entrega de bienes, desde la coordinación de fechas de inicio hasta el cierre final, controlando la documentación obligatoria según el tipo de trabajo, automatizando notificaciones y asegurando la trazabilidad completa del proceso.

### 18.2. Flujo del Proceso

#### 18.2.1. Coordinación y Solicitud de Documentos

1. **Supervisor de MTTO coordina fecha de inicio**: Revisa solicitud, contacta proveedor, valida disponibilidad cliente/sede
2. **Sistema determina documentos obligatorios** según tipo de trabajo (ver tabla en 18.2.2)
3. **Sistema envía mail al proveedor** con lista de documentos requeridos, plazo de entrega y enlace al portal

**Plazos de Entrega de Documentos**:
- **Trabajos Menores - Bajo Riesgo**: 2 días hábiles
- **Trabajos de Alto Riesgo Programados**: 2 días hábiles
- **Emergencia**: 4 horas

#### 18.2.2. Tabla de Documentos Obligatorios según Tipo de Trabajo

| N° | DOCUMENTO | REVISIÓN | TRABAJOS MENORES | ALTO RIESGO | EMERGENCIA |
|----|-----------|----------|------------------|-------------|------------|
| 1 | Relación de Personal | CONTRALOR | ✓ | ✓ | ✓ |
| 2 | Certificado de Homologación | CONTRALOR | ✓ | ✓ | ✓ |
| 3 | Constancia SCTR (Salud y Pensión) | CONTRALOR | ✓ | ✓ | ✓ |
| 4 | Certificado de Operatividad de Equipos | SST | - | ✓ | ✓ |
| 5 | Procedimiento de Trabajo Seguro | SST | - | ✓ | ✓ |
| 6 | Carnet SST Terceros | CONTRALOR | ✓ | ✓ | ✓ |
| 7 | CV Documento de Prevencionista de Riesgo | SST | - | ✓ | ✓ |
| 8 | Certificado de Aptitud Médico | SST | - | ✓ | - |
| 9 | Certificado de Capacitación Trabajo Alto Riesgo | SST | - | ✓ | - |
| 10 | Registro de Entrega EPPS | SST | - | ✓ | - |
| 11 | IPERC Específico | SST | ✓ | ✓ | ✓ |
| 12 | Plan de Emergencia | SST | ✓ | ✓ | ✓ |
| 13 | Competencia de Trabajadores - CV Certificados | SST | - | ✓ | - |
| 14 | Hojas de Seguridad - MSDS | SST | ✓ | ✓ | ✓ |
| 15 | Carta de Autorización de Corte de Energía | SST | - | ✓ | ✓ |

**Leyenda**: ✓ Obligatorio | - No requerido | CONTRALOR: Revisión Contraloría | SST: Revisión Seguridad y Salud

**Total documentos obligatorios**: Menores (7), Alto Riesgo (15), Emergencia (11)

#### 18.2.3. Proveedor Carga Documentación

1. Proveedor accede al portal y visualiza lista de documentos requeridos
2. Carga cada documento (formato PDF, máximo 10 MB)
3. Sistema valida formato, tamaño y vigencia (si aplica)
4. Sistema muestra progreso: "X de Y documentos cargados"
5. Proveedor confirma envío → Sistema notifica a Supervisor y SSDMA

#### 18.2.4. Supervisor y SSDMA Validan Documentación

1. **Supervisor revisa documentación**: Verifica completitud y vigencia
2. **SSDMA valida documentos SST**: Checklist de seguridad (charla, personal autorizado, EPPs, permisos especiales)
3. **Gateway de Decisión: ¿Es correcto?**
   - **SÍ**: Supervisor confirma fecha de inicio → Estado: "Fecha de Inicio Confirmada"
   - **NO**: SSDMA registra observaciones (Crítica/Media/Leve) → Proveedor debe subsanar

**Observaciones Críticas**: Bloquean inicio del servicio hasta subsanación

#### 18.2.5. Ejecución del Servicio

1. **Inicio de ejecución**: Sistema registra fecha/hora de inicio y activa contador de 48 horas
2. **Alertas progresivas de cierre**:
   - A las 24 horas: Primera alerta al Supervisor
   - A las 40 horas: Alerta de urgencia
   - A las 48 horas: Alerta crítica al Supervisor y Gerente FM

#### 18.2.6. Cierre del Servicio

1. **Proveedor carga documentación de cierre**:
   - Acta de Conformidad firmada por cliente
   - Orden de Trabajo cerrada
   - Evidencias fotográficas (mínimo 3)
   - Documentación geolocalizable (si aplica)
   - Certificados de Prueba/Garantía (si aplica)
2. **Supervisor valida documentación de cierre**: Revisa acta, valida alcance, aprueba o solicita correcciones
3. **Sistema cierra el ticket**: Estado final "Cerrado", genera reporte, archiva documentación

---

### 18.3. Flujo de Entrega del Bien

#### 18.3.1. Vía Email

1. Service Desk coordina fecha de entrega con proveedor
2. Proveedor envía información para ingreso (guía de remisión, factura, certificados)
3. Service Desk valida documentación de ingreso
4. **Gateway: ¿Es correcto?**
   - **SÍ**: Service Desk genera PI (Parte de Ingreso) y lo envía al almacén
   - **NO**: Proveedor debe corregir documentación
5. Almacén recepciona bien con PI

#### 18.3.2. Vía Puesta a Calle (CC - Centro de Costo/Cliente)

1. Supervisor coordina fecha de ejecución con cliente
2. Proveedor ejecuta servicio (instalación/puesta en marcha)
3. Sistema alerta plazo de 48 horas para cierre
4. Cliente comunica aprobación
5. Supervisor registra fecha de cierre y adjunta documentación
6. Sistema cierra el ticket

---

### 18.4. Estados del Servicio en Ejecución

1. **Coordinación de Inicio** | 2. **Documentación Solicitada** | 3. **Documentación en Carga** | 4. **Documentación en Revisión** | 5. **Documentación Observada** | 6. **Documentación Aprobada** | 7. **Fecha de Inicio Confirmada** | 8. **En Ejecución** | 9. **Pendiente de Cierre** | 10. **Alerta 48 Horas** | 11. **Documentación de Cierre en Revisión** | 12. **Aprobado por Cliente** | 13. **Cerrado** | 14. **Entrega Programada** (bienes) | 15. **En Tránsito** (bienes) | 16. **Recibido en Almacén** (bienes)

---

### 18.5. Pantallas del Módulo

#### 18.5.1. Pantalla de Coordinación de Inicio
- Campos: Código Servicio, Proveedor, Tipo de Trabajo, Fecha/Hora Estimada, Personal Asignado, Equipos, Observaciones
- Botones: Solicitar Documentación, Guardar Coordinación

#### 18.5.2. Portal de Proveedores - Carga de Documentos
- Información: Código Servicio, Tipo de Trabajo, Plazo de Entrega, Progreso (X de Y documentos)
- Formulario: Tipo de Documento, Adjuntar Archivo (PDF, 10 MB máx.), Fecha Vencimiento, Observaciones
- Validación: Solo PDF, tamaño máximo, fechas vigentes
- Botones: Cargar Documento, Enviar Documentación Completa

#### 18.5.3. Pantalla de Gestión de Documentos (Supervisor/SSDMA)
- Tabla: N°, Documento, Responsable Revisión, Estado (Pendiente/Cargado/Aprobado/Observado), Fecha Carga, Vencimiento, Acciones
- Filtros: Por Estado, Por Responsable (CONTRALOR/SST)
- Botones: Aprobar Todos, Enviar Observaciones

#### 18.5.4. Pantalla de Revisión SSDMA
- Checklist SST: Charla Seguridad, Personal Autorizado, EPPs Verificados, Permisos Especiales, Documentación Vigente
- Observaciones: Tipo (Crítica/Media/Leve), Descripción, Documentos Afectados, Acción Correctiva, Plazo, Evidencia Fotográfica
- Botones: Aprobar Documentación SST, Registrar Observación, Rechazar

#### 18.5.5. Pantalla de Seguimiento de Ejecución
- Información: Código, Estado Actual, Proveedor, Fechas (Inicio/Cierre Programada), Tiempo Transcurrido/Restante
- Timeline: Coordinación → Solicitud Docs → Carga → Aprobación → Inicio Ejecución → Cierre
- Acciones: Confirmar Inicio, Registrar Avance, Adjuntar Evidencias, Cargar Acta Conformidad, Cerrar Servicio

#### 18.5.6. Pantalla de Cierre de Servicio
- Documentación obligatoria: Acta Conformidad, OT Cerrada, Evidencias Fotográficas (mín. 3), Documentación Geolocalizable, Certificados
- Conformidad Cliente: ¿Dio conformidad? (Sí/No), Nombre Cliente, Observaciones
- Evaluación: Calidad, Cumplimiento Plazo, Atención Proveedor (1-5 estrellas)
- Botones: Cerrar Servicio, Guardar Borrador, Solicitar Correcciones

#### 18.5.7. Pantalla de Gestión de Entrega de Bienes
- Coordinación: Fecha/Hora Entrega, Punto Entrega, Responsable Recepción, Observaciones
- Documentos Ingreso: Guía Remisión, Factura, Certificados, Ficha Técnica, Garantía
- Parte de Ingreso: Generar PI, N° PI (autogenerado), Adjuntar al Expediente
- Botones: Confirmar Entrega, Generar PI, Notificar Almacén

---

### 18.6. Reglas de Negocio

1. **Documentación Obligatoria**: Sistema NO permite confirmar fecha de inicio sin documentación completa y aprobada según tipo de trabajo
2. **Vigencia de Documentos**: SCTR vigente durante ejecución; homologación activa; certificados de equipos y médicos no vencidos
3. **Observaciones Críticas**: Bloquean inicio; Medias permiten inicio con compromiso; Leves se subsanan durante ejecución
4. **Alerta 48 Horas**: Contador automático desde inicio; alertas a las 24, 40 y 48 horas; exceder plazo requiere justificación escrita
5. **Conformidad Cliente**: Acta firmada por cliente es obligatoria para cerrar servicio; sin conformidad NO se puede cerrar
6. **Parte de Ingreso (PI)**: Obligatorio para recepción de bienes; debe estar vinculado a OC; sin PI almacén NO recepciona

---

### 18.7. Consideraciones Técnicas

- **Almacenamiento**: Repositorio seguro, backup diario, versionado de documentos, retención 7 años, encriptación de docs sensibles
- **Seguridad**: Acceso por roles (Supervisor, SSDMA, Proveedor, Almacén), permisos granulares, registro de accesos, auditoría completa
- **Performance**: Carga docs < 30 seg, visualización < 3 seg, generación PI < 5 seg, consulta estado < 2 seg
- **Disponibilidad**: Sistema 24/7 (especialmente emergencias), mantenimientos fuera de horario laboral, notificación previa 48 horas
- **Notificaciones**: Envío en tiempo real (< 5 seg), múltiples canales (email, sistema, WhatsApp para urgentes), reintentos automáticos (3 intentos)

---

**Nota Final**: El módulo de Ejecución de Trabajo/Entrega del Bien es crítico para controlar la documentación obligatoria de seguridad según el tipo de trabajo (15 documentos para Alto Riesgo, 11 para Emergencia, 7 para Trabajos Menores), garantizar cumplimiento de plazos de cierre (48 horas) y asegurar la trazabilidad completa desde coordinación hasta cierre final.

---

## 19. EMISIÓN DE HES (Hoja de Entrada de Servicio)

### 19.1. Objetivo del Módulo

Gestionar la emisión de HES (Hoja de Entrada de Servicio) para formalizar la culminación de servicios ejecutados por proveedores, validando la documentación requerida y asegurando la notificación automática al proveedor. Este proceso es fundamental para el cierre administrativo y contable de los servicios prestados.

**Nota Importante**: Este módulo NO tiene integración con SAP. Toda la gestión es independiente dentro del sistema FM.

### 19.2. Flujo del Proceso

#### 19.2.1. Proveedor Entrega Documentación Requerida

1. Proveedor accede al Portal de Proveedores y navega a "Solicitud de HES"
2. Visualiza servicios completados pendientes de HES (filtros: Fecha, Cliente, Sede, Monto)
3. Selecciona servicio y carga documentos obligatorios según tipo de servicio

**Documentos Obligatorios**:

| N° | Documento | Formato | Obligatorio |
|----|-----------|---------|-------------|
| 1 | Ficha de Atención | PDF | Sí |
| 2 | Informe Técnico | PDF | Sí |
| 3 | Protocolo de Mantenimiento | PDF | Condicional* |
| 4 | Acta de Conformidad | PDF | Sí |
| 5 | Evidencias Fotográficas | JPG/PNG/PDF | Sí |
| 6 | Orden de Trabajo Cerrada | PDF | Sí |
| 7 | Reporte de Materiales Utilizados | PDF/Excel | Condicional* |
| 8 | Certificados de Prueba | PDF | Condicional* |

*Condicional: Según tipo de servicio (preventivo/correctivo, uso de materiales, alto riesgo)

**Validaciones**: Formato PDF, tamaño máximo 10 MB, nomenclatura con código de servicio

#### 19.2.2. Proveedor Solicita Emisión de HES

1. Proveedor revisa documentación cargada (progreso: "X de Y documentos cargados")
2. Completa formulario de solicitud con datos del servicio (solo lectura) y observaciones (opcional)
3. Hace clic en "Solicitar Emisión de HES"
4. Sistema genera número de solicitud y cambia estado a "Solicitud de HES en Revisión"
5. Sistema notifica al Service Desk

#### 19.2.3. Service Desk Valida la Documentación

1. Service Desk accede al módulo de Validación de HES (filtros: Estado, Proveedor, Fecha, Cliente)
2. Selecciona solicitud y accede a documentación cargada
3. Revisa cada documento con checklist:
   - Ficha de Atención completa y firmada
   - Informe Técnico detallado con hallazgos
   - Protocolo de Mantenimiento (si aplica)
   - Acta de Conformidad con firma del cliente
   - Evidencias fotográficas claras (mínimo 3: antes, durante, después)
   - Orden de Trabajo cerrada
   - Reporte de Materiales coincide con OC (si aplica)
   - Certificados de Prueba vigentes (si aplica)
4. Valida específicamente:
   - **Acta de Conformidad**: Firma cliente, fecha posterior a inicio, conformidad total
   - **Informe Técnico**: Actividades, hallazgos, coincide con OC, firmado
   - **Evidencias Fotográficas**: Mínimo 3, claras, muestran trabajo, fecha dentro del periodo
   - **Montos**: Materiales no exceden OC, coherencia con servicio
5. Marca cada documento como "Aprobado" o "Observado"

#### 19.2.4. Gateway de Decisión: ¿Es Correcto?

**CASO A: SÍ - Documentación Correcta**
- Todos los documentos aprobados, sin observaciones críticas, checklist completo
- Continúa a 19.2.5 (Service Desk emite HES)

**CASO B: NO - Documentación Incorrecta/Incompleta**
- Documentos faltantes, observaciones críticas, documentos no conformes
- Service Desk registra observaciones (tipo, descripción, plazo: 2 días hábiles)
- Sistema notifica al proveedor con lista de observaciones y enlace para corregir
- Proveedor corrige y reenvía (máximo 3 oportunidades; después requiere aprobación Supervisor)
- Regresa a revisión

#### 19.2.5. Service Desk Emite la HES

1. Service Desk accede a módulo de Emisión de HES
2. Sistema pre-llena datos automáticamente:
   - Número de HES (formato: HES-[Año]-[Mes]-[Correlativo])
   - Código de Servicio, OC, Proveedor, Cliente, Sede
   - Descripción, Fechas, Monto Total
3. Service Desk completa información adicional (opcional):
   - Observaciones, Área Solicitante, Centro de Costo, N° de PI, Anexos
4. Genera HES en PDF (plantilla estándar con logo Panorama BPO)
5. Revisa vista previa y confirma
6. Hace clic en "Emitir HES" → Estado: "HES Emitida"

#### 19.2.6. Service Desk Carga la HES al Sistema

1. Sistema almacena HES automáticamente (PDF en repositorio)
2. Vincula HES con: OC, Documentación del servicio, Acta de conformidad, PI (si aplica)
3. Actualiza estado: "HES Emitida y Registrada"
4. Marca servicio como "Listo para Facturación"

#### 19.2.7. Sistema Envía la HES vía Mail al Proveedor

1. Sistema genera correo automático con:
   - Asunto: "HES Emitida - [Número] - [Código Servicio]"
   - Datos de HES (número, servicio, OC, cliente, monto)
   - HES adjunta en PDF
   - Instrucciones: Facturar en 5 días hábiles con referencia a HES y OC
2. Registra envío (fecha, hora, destinatario, estado)
3. Notifica a Supervisor de MTTO y Gerente FM (si monto > umbral)
4. Estado final: "Proceso de HES Completado"

---

### 19.3. Estados de la Solicitud de HES

1. **Pendiente de Solicitud** | 2. **Documentación en Carga** | 3. **Solicitud en Revisión** | 4. **Documentación Observada** | 5. **Solicitud en Revisión (Corrección)** | 6. **Documentación Aprobada** | 7. **HES en Emisión** | 8. **HES Emitida** | 9. **HES Emitida y Registrada** | 10. **HES Enviada al Proveedor** | 11. **Proceso Completado** | 12. **Suspendida**

---

### 19.4. Pantallas del Módulo

#### 19.4.1. Portal de Proveedores - Solicitud de HES
- Lista de servicios completados (filtros: Estado HES, Cliente, Fechas, Monto)
- Formulario de solicitud: Datos servicio (solo lectura), Carga de documentos, Barra de progreso, Observaciones
- Botones: Cargar Documento, Guardar Borrador, Solicitar Emisión de HES

#### 19.4.2. Pantalla de Validación de HES (Service Desk)
- Información del servicio (código, proveedor, cliente, fecha, monto)
- Checklist de documentos (estado, ver/descargar, observaciones)
- Botones: Aprobar Documento, Observar Documento, Aprobar Todos, Solicitar Correcciones, Emitir HES

#### 19.4.3. Pantalla de Emisión de HES
- Datos pre-llenados (automáticos)
- Campos editables (observaciones, área, centro costo, PI, anexos)
- Vista previa de HES en PDF
- Botones: Generar Vista Previa, Emitir HES, Cancelar, Guardar Borrador

#### 19.4.4. Pantalla de Seguimiento de HES
- Filtros: Estado, Proveedor, Cliente, Fechas, Número HES
- Tabla: Número HES, Código Servicio, Proveedor, Cliente, Fecha Emisión, Monto, Estado, Días desde Emisión
- Acciones: Ver Detalle, Descargar PDF, Ver Documentación, Reenviar, Auditoría, Imprimir, Exportar Excel

---

### 19.5. Reglas de Negocio

1. **Documentación Obligatoria**: Sistema NO permite solicitar HES sin documentos obligatorios completos (5 siempre + 3 condicionales)
2. **Acta de Conformidad**: Debe tener firma cliente; sin acta NO se puede emitir HES
3. **Límite de Rechazos**: Máximo 3 oportunidades para corregir; después se suspende automáticamente
4. **Plazos**: Corrección en 2 días hábiles (ampliable a 5 máximo); recordatorio 1 día antes; vencimiento suspende solicitud
5. **Numeración HES**: Formato HES-[Año]-[Mes]-[Correlativo]; secuencial y única; no modificable una vez emitida
6. **Facturación**: Proveedor debe facturar en 5 días hábiles; recordatorio a los 3 días; referencia obligatoria a HES y OC
7. **Modificación HES**: Una vez emitida es inmutable; anulación requiere aprobación Gerente FM
8. **Vinculación OC**: HES debe estar vinculada a OC válida; monto no puede exceder OC (±2% tolerancia)

---

### 19.6. Consideraciones Técnicas

- **Almacenamiento**: Repositorio seguro, backup diario, formato PDF/A, retención 7 años, indexación por HES/OC/servicio/proveedor
- **Seguridad**: HES inmutables, solo lectura proveedores, control acceso por rol, auditoría completa
- **Performance**: Generación PDF < 10 seg, consulta < 2 seg, descarga < 5 seg, envío email < 30 seg
- **Sin SAP**: No hay integración; gestión exclusiva en FM; exportación manual a Excel si necesario
- **Trazabilidad**: Vinculación completa Solicitud → Cotización → OC → Ejecución → Cierre → HES

---

**Nota Final**: El módulo de Emisión de HES es crítico para el cierre administrativo de servicios. La correcta validación de documentación y emisión oportuna asegura el flujo de facturación y pago a proveedores. El sistema garantiza la inmutabilidad de las HES emitidas y mantiene una auditoría completa del proceso.


---

## 20. PRESENTACIÓN DE KPI's

### 20.1. Objetivo del Módulo

Proporcionar visualización y análisis de indicadores clave de rendimiento (KPI's) del sistema FM mediante reportes estándares predefinidos y dashboards personalizados. El módulo permite monitorear el desempeño de servicios, equipos y proveedores para facilitar la toma de decisiones basadas en datos.

### 20.2. Flujo del Proceso

#### 20.2.1. FM Ingresa al Sistema

1. Usuario FM accede al módulo "Reportes y KPI's"
2. Sistema valida permisos según rol (Gerente FM, Supervisor, Analista)
3. Sistema muestra dashboard principal con KPI's relevantes

#### 20.2.2. Ingresa al Módulo de Reportes

**Gateway de Decisión: ¿Para Nuevos KPI's?**

**Para nuevos KPI's debe ser configurado por FM.**

- **CASO A - KPI Estándar**: Usuario selecciona KPI de la lista de 23 predefinidos → Sistema permite visualizar reportes estándares
- **CASO B - Nuevo KPI**: Usuario crea dashboard personalizado → Sistema permite crear y sugerir reportes personalizados (Estilo Power BI + IA)

#### 20.2.3. Sistema Permite Visualizar Reportes Estándares

1. Usuario selecciona KPI estándar (ver Tabla en 20.3)
2. Sistema muestra gráfico principal con indicadores
3. Filtros disponibles: Periodo, Cliente, Sede, Proveedor, Categoría de Servicio, Tipo de Equipo
4. Acciones: Exportar (Excel/PDF), Guardar favorito, Compartir, Programar envío

#### 20.2.4. Sistema Permite Crear Reportes Personalizados (Estilo Power BI + IA)

1. **Usuario define reporte**: Nombre, descripción, categoría
2. **Usuario selecciona fuente de datos**: Servicios, OT's, Equipos, Preventivos, Proveedores, Tiempos, Costos, HES, Cotizaciones, OC's
3. **Usuario selecciona campos**:
   - Dimensiones: Fecha, Cliente, Sede, Proveedor, Tipo de Servicio, Estado, Categoría de Equipo
   - Métricas: Conteo, Suma, Promedio, Porcentaje, Cantidad
4. **Sistema sugiere gráficos según campos seleccionados** (IA analiza y recomienda visualizaciones)
5. **Usuario decide**:
   - Selecciona dashboard sugerido por IA
   - O diseña reporte visual manualmente (drag-and-drop)
6. Usuario guarda reporte personalizado

---

### 20.3. Catálogo de KPI's Estándares

El sistema FM incluye 23 KPI's predefinidos:

| N° | Nombre de indicador, KPI/OKR | Categorías | Lógica | Fórmula | Modo de Recaudación |
|----|------------------------------|------------|--------|---------|---------------------|
| 1 | **Cumplimiento del preventivo** | Preventivo | Compara los servicios preventivos programados versus los efectivamente ejecutados. | Ejecutados/Programados | Se obtiene de los registros de mantenimientos programados y ejecutados en el sistema. |
| 2 | **Cumplimiento de entregables (Preventivos)** | Preventivo | Mide el cumplimiento de la entrega de reportes, informes o entregables correspondientes a los mantenimientos preventivos. | Entregables emitidos/Entregables Programados | Se toma del control de entregas documentarias asociadas a cada mantenimiento preventivo. |
| 3 | **MTBF (Mean Time Between Failures)** | Equipos | Mide el tiempo promedio entre una falla y la siguiente, reflejando la confiabilidad del activo. | Tiempo total de funcionamiento/Número de fallas | Se calcula con base en los registros de fallas y reparaciones de los equipos. |
| 4 | **Tiempo medio de atención de Compras CSC** | Servicio | Promedio del tiempo que tarda el área de compras en atender un requerimiento o servicio. | Tiempo total de atención/Número de servicios adjudicados | Se obtiene del registro de solicitudes enviadas y fechas de atención de Compras CSC. |
| 5 | **MTTR (Mean Time To Repair)** | Equipos | Mide el tiempo promedio que tarda en repararse un equipo tras una falla. | Tiempo total de reparación/Número de fallas | Se obtiene del tiempo registrado entre inicio y fin de cada reparación. |
| 6 | **Disponibilidad de equipos** | Equipos | Indica el porcentaje de tiempo que un equipo está disponible para operar respecto al total de tiempo del periodo analizado. | (Tiempo operativo/(Tiempo operativo + Tiempo fuera de servicio))*100 | Se calcula a partir de los registros de operación y tiempos fuera de servicio. |
| 7 | **Ciclo del activo** | Equipos | Mide el tiempo que transcurre desde la adquisición hasta el retiro o reemplazo del activo. | Fecha de retiro - Fecha de adquisición | Se obtiene de las fechas de alta y baja registradas para cada equipo. |
| 8 | **Tiempo de vida del activo** | Equipos | Mide el tiempo de funcionamiento real del activo desde su puesta en marcha. | Fecha actual - Fecha de inicio de operación | Se calcula con las fechas de inicio de operación registradas en el sistema. |
| 9 | **Tiempo de envío de presupuesto** | Servicio | Mide el tiempo promedio que tarda en enviarse un presupuesto de Facilities Management al cliente. | Fecha de envío - Fecha de solicitud x cliente | Se obtiene de las fechas de solicitud y envío de presupuesto registradas. |
| 10 | **OEE (Overall Equipment Effectiveness)** | Equipos | Mide la eficiencia global del equipo considerando disponibilidad, rendimiento y calidad. | Disponibilidad * Rendimiento * Calidad | Se obtiene integrando tres fuentes del sistema: disponibilidad (horas operativas vs paradas), rendimiento (producción real vs esperada) y calidad (unidades buenas vs totales). La información se consolida automáticamente por equipo y periodo. |
| 11 | **Tasa de fallos o paros inesperados** | Equipos | Mide la frecuencia de fallas o detenciones no planificadas respecto al total de horas de operación. | (Número de fallas inesperadas/Horas totales de operación)*100 | Se calcula con base en los reportes de fallas y el total de horas operativas. |
| 12 | **Porcentaje de fallas no planificadas** | Equipos | Mide el porcentaje de fallas no previstas sobre el total de intervenciones. | (Fallas no planificadas/Total de intervenciones)*100 | Se obtiene del registro de órdenes de trabajo clasificadas como no planificadas. |
| 13 | **Cumplimiento de entrega de inventario de equipos** | Equipos | Mide el cumplimiento de la entrega del inventario físico o técnico de equipos. | (Locales intervenidos/Locales Programados)*100 | Se toma de los registros de entregas de inventario programadas y realizadas. |
| 14 | **Nivel de cumplimiento de Tiempo medio de llegada a sitio por Emergencias** | Servicio | Mide el cumplimiento del tiempo objetivo de llegada ante emergencias. | (Llegadas dentro del Tiempo objetivo/Total de emergencias)*100 | Se obtiene de los tiempos de llegada registrados en cada atención de emergencia. |
| 15 | **Nivel de cumplimiento de Tiempo medio de ejecución de Emergencias** | Servicio | Mide el cumplimiento del tiempo establecido para ejecutar las atenciones de emergencia. | (Ejecuciones dentro del Tiempo objetivo/Total de emergencias)*100 | Se toma del control de tiempos de ejecución registrados para servicios de emergencia. |
| 16 | **Nivel de cumplimiento de Tiempo medio de llegada a sitio para Correctivos normales** | Servicio | Mide el cumplimiento del tiempo objetivo de llegada para atenciones correctivas no urgentes. | (Llegadas dentro del Tiempo objetivo/Total de correctivos normales)*100 | Se obtiene del registro de tiempos de atención de servicios correctivos normales. |
| 17 | **Nivel de cumplimiento de Tiempo medio de ejecución de Correctivos normales** | Servicio | Mide el cumplimiento del tiempo establecido para ejecutar las órdenes correctivas. | (Ejecuciones dentro del Tiempo objetivo/Total de correctivos normales)*100 | Se calcula con base en los tiempos de ejecución de cada orden correctiva. |
| 18 | **Ratio de Confiabilidad** | Equipos | Mide la proporción de equipos que no presentaron fallas durante el periodo. | (N° de equipos sin fallas/Total de equipos)*100 | Se obtiene del conteo de equipos sin registros de fallas en el periodo. |
| 19 | **Ratio de OT's de Emergencia** | Servicio | Mide la proporción de órdenes de trabajo de emergencia respecto al total de órdenes emitidas. | (OTs de emergencia/Total de OTs)*100 | Se toma del registro de órdenes de trabajo clasificadas por tipo de atención. |
| 20 | **Ratio de averías repetidas** | Equipos | Mide la proporción de fallas reincidentes sobre el total de fallas registradas. | (Fallas repetidas/Total de fallas)*100 | Se obtiene comparando las fallas reportadas de un mismo equipo en un periodo. |
| 21 | **Nivel de cumplimiento de Tiempo medio de Finalización de OT's con conformidades y revisiones** | Servicio | Mide el cumplimiento del tiempo objetivo de cierre de OT's incluyendo revisión y conformidad. | (OTs finalizadas dentro del Tiempo objetivo/Total de OTs)*100 | Se obtiene de los tiempos de cierre registrados con validación y conformidad. |
| 22 | **Nivel de cumplimiento de Entrega de Liquidaciones de los servicios realizados** | Servicio | Mide el cumplimiento en la entrega de liquidaciones administrativas dentro del plazo establecido. | (Liquidaciones entregadas a Tiempo/Total de servicios realizados)*100 | Se obtiene del registro de entregas de liquidaciones con fecha límite y de envío. |
| 23 | **Evaluación de desempeño del proveedor** | Servicio | Mide el cumplimiento de indicadores de calidad, tiempo, seguridad y documentación del proveedor. | Σ(Ponderación * Cumplimiento de cada criterio) | Se calcula con base en la evaluación de desempeño registrada por cada proveedor. |

**Categorías de KPI's**:
- **Preventivo** (2 KPI's): N° 1-2
- **Equipos** (11 KPI's): N° 3, 5-8, 10-13, 18, 20
- **Servicio** (10 KPI's): N° 4, 9, 14-17, 19, 21-23

---

### 20.4. Pantallas del Módulo

#### 20.4.1. Dashboard Principal de KPI's
- Tarjetas con KPI's principales (Top 6 configurables)
- Gráfico de tendencia de KPI prioritario
- Alertas de KPI's fuera de rango
- Filtros globales: Periodo, Cliente, Sede

#### 20.4.2. Catálogo de KPI's Estándares
- Lista de 23 KPI's predefinidos
- Filtros: Por Categoría, Por Nombre, Por Favoritos
- Acciones: Ver Reporte, Agregar a Favoritos, Exportar, Compartir

#### 20.4.3. Pantalla de Visualización de KPI
- Valor actual destacado, comparación con periodo anterior
- Gráfico principal (tipo según KPI)
- Tabla de datos detallados, drill-down
- Botones: Exportar (Excel/PDF), Compartir, Programar Envío

#### 20.4.4. Lienzo de Diseño de Reportes Personalizados
- Panel izquierdo: Componentes (gráficos, tablas, KPI cards)
- Área central: Canvas drag-and-drop
- Panel derecho: Propiedades del componente
- IA sugiere 3-5 dashboards según campos seleccionados

---

### 20.5. Reglas de Negocio

1. **Configuración de KPI's Nuevos**: Solo Gerente FM o Administrador pueden crear KPI's nuevos
2. **Acceso a Reportes**:
   - Gerente FM: Acceso total
   - Supervisor: KPI's de Equipos y Servicio (limitado a sus clientes/sedes)
   - Analista: Reportes predefinidos (sin edición)
3. **Actualización de Datos**: KPI's estándares se actualizan cada hora; KPI's en tiempo real cada 15 minutos
4. **Retención**: Datos históricos de KPI's se conservan por 24 meses
5. **Exportación**: Excel máximo 100,000 filas; PDF máximo 50 páginas
6. **Compartir Dashboards**: Creador define permisos (lectura/edición/administración)
7. **Alertas**: Usuario puede configurar alertas personalizadas (máximo 10 activas por usuario)
8. **Programación**: Máximo 20 reportes programados por usuario; envío en horario nocturno (2:00-6:00 AM)

---

### 20.6. Consideraciones Técnicas

- **Performance**: Carga de dashboard < 3 segundos; generación de gráficos < 2 segundos
- **Almacenamiento**: Datos históricos 24 meses; reportes exportados 6 meses
- **Escalabilidad**: Soportar 100 usuarios concurrentes; hasta 500 dashboards personalizados
- **Seguridad**: Control de acceso por rol; exportaciones con marca de agua; auditoría completa
- **Interactividad**: Gráficos interactivos (zoom, pan, tooltips); drill-down; filtros globales
- **Responsividad**: Dashboards adaptables a tablets y smartphones

---

**Nota Final**: El módulo de Presentación de KPI's facilita la toma de decisiones estratégicas basadas en datos mediante 23 KPI's predefinidos y capacidad de crear dashboards personalizados con IA.

---

## 21. PROGRAMACIÓN DE MANTENIMIENTO Y ACTIVIDADES

### 21.1. Objetivo del Módulo

Gestionar la programación de mantenimientos preventivos y actividades de FM mediante un calendario visual, generar automáticamente códigos de servicio únicos para PAM's (Programa Anual de Mantenimiento), calendarizar tareas, elaborar Gantt de programación y generar OT's asociadas, asegurando trazabilidad completa desde planificación hasta cierre.

### 21.2. Flujo del Proceso

#### 21.2.1. Sistema Solicita Información de Actividad

1. **Sistema solicita**: Actividad, programación, fechas, recursos y personal
2. **FM accede al módulo** "Programación de Mantenimiento y Actividades"
3. **Sistema presenta formulario** con campos requeridos

#### 21.2.2. FM Registra Programación y Actividades

1. **FM completa información**:
   - Tipo de Actividad (Preventivo, Inspección, Calibración, Limpieza, etc.)
   - Cliente/Sede
   - Equipo/Activo (si aplica)
   - Frecuencia (Mensual, Trimestral, Semestral, Anual)
   - Fecha de Inicio Programada
   - Turno (Mañana, Tarde, Noche)
   - Recursos Necesarios (herramientas, materiales)
   - Personal Asignado (técnico, proveedor)
   - Observaciones

2. **Sistema recoge información del Event Code**:
   - Fecha programada
   - Cliente
   - Tienda/Sede
   - Turno
   - Tipo de mantenimiento
   - Código de equipo (si aplica)

3. **Sistema valida información**: Disponibilidad de recursos, conflictos de calendario, capacidad del personal

**Nota**: Modificable por Gerente de FM y FM

#### 21.2.3. Sistema Agrupa y Calendariza

1. **Sistema agrupa información en el día asignado**:
   - Agrupa por fecha
   - Agrupa por cliente/sede
   - Agrupa por turno
   - Agrupa por técnico/proveedor

2. **Sistema calendariza las actividades programadas**:
   - Asigna slot en calendario
   - Valida superposición de actividades
   - Genera alertas de conflictos

#### 21.2.4. Sistema Muestra Información en Calendario

**Opciones de Visualización**:

**A. Calendario con Vista Principal Mensual**:
- Vista mensual con actividades agrupadas por día
- Código de colores por tipo de actividad
- Indicadores de carga por día (bajo/medio/alto)
- Capacidad de filtrar por rango de fechas
- Filtros: Cliente, Sede, Tipo de Actividad, Técnico, Estado

**B. Vista Gantt de Programación de Mantenimientos**:
- Sistema elabora Gantt de programación
- Línea de tiempo con tareas programadas
- Visualización de dependencias
- Hitos importantes
- Progreso de ejecución

**Gateway de Decisión: Calendario o Gantt?**
- Usuario selecciona vista preferida
- Sistema alterna entre vistas sin perder datos

#### 21.2.5. Sistema Genera las OT's

**Generación Automática**:

1. **Código único PAM**: Formato PAM-[Año]-[Mes]-[Cliente]-[Correlativo] (ej: PAM-2026-02-CLIENTEX-001)

2. **Datos obligatorios de la OT**:
   - **Trazabilidad**: Quién creó, quién solicitó, fecha creación, fecha aprobación
   - **Asociaciones**: Incidencia (si aplica con mismo concepto), Grupo MTTO, Sub Grupo MTTO, Centro de Costo
   - **Clasificación**: Tipo (Preventivo/Correctivo), Criticidad (Normal default/Urgente/Emergencia)
   - **Asignaciones**: Cliente, Sede/Inmueble, Proveedor, Técnico
   - **Programación**: Fecha inicio calendarizada, duración estimada
   - **Estado inicial**: "Programada" (Estados: Operativo, En Proceso, Programada, Ejecutada, Con Atraso, Anulada)

3. **Módulo de Gestión de OT's**:
   - **Visualización**: Modo Kanban (columnas por estado) o Modo Listado (tabla 100% de OT's)
   - **Búsqueda y Filtros**: Por todas las variables (listas desplegables: estado, cliente, sede, proveedor, grupo MTTO, criticidad, fechas, etc.)
   - **Cálculo de tiempos**: Sistema calcula tiempo de atención (horas/minutos/días), indica dentro de tiempo o atrasada
   - **Alertas automáticas**: Por correo, SMS o WhatsApp según fecha programación, estado, atrasos, asignaciones
   - **Alertas personalizadas**: Configurables por usuario
   - **Validación**: Firma digital requerida para cierre
   - **Exportación**: Imprimible y exportable a PDF

4. **Fecha de inicio = Día de ejecución programado**

#### 21.2.6. Gestión de Cierre de Mantenimiento

1. **Técnico/Proveedor ejecuta mantenimiento** y registra en sistema:
   - Fecha y hora real de ejecución
   - Actividades realizadas
   - Hallazgos/Observaciones
   - Materiales utilizados
   - Evidencias fotográficas

2. **Supervisor valida cierre**:
   - Revisa documentación
   - Aprueba o solicita correcciones
   - Confirma conformidad

#### 21.2.7. Sistema Cambia el Status del Calendario

**Estados del Calendario**:
- **Programada**: Actividad creada, pendiente de ejecución
- **En Ejecución**: Técnico ha iniciado trabajo
- **Cerrado**: Actividad completada y validada
- **Culminado**: Proceso completo con documentación archivada
- **Reprogramada**: Cambio de fecha por motivo justificado
- **Cancelada**: Actividad anulada

Sistema actualiza automáticamente el color en calendario según estado.

---

### 21.3. Pantallas del Módulo

#### 21.3.1. Pantalla de Registro de Programación

**Campos**:
- Tipo de Actividad (dropdown: Preventivo, Inspección, Calibración, Limpieza, Otro)
- Cliente/Sede (búsqueda con autocompletado)
- Equipo/Activo (búsqueda vinculada a sede, opcional)
- Frecuencia (Única, Mensual, Trimestral, Semestral, Anual)
- Fecha de Inicio Programada (calendario)
- Hora Estimada (hora)
- Turno (Mañana: 6-14h, Tarde: 14-22h, Noche: 22-6h)
- Duración Estimada (horas)
- Recursos Necesarios (texto/checklist)
- Personal Asignado (búsqueda de técnicos/proveedores)
- Observaciones (texto largo)
- Recurrencia (si aplica: cada X días/semanas/meses, hasta fecha)

**Botones**: Guardar, Guardar y Crear OT, Cancelar

#### 21.3.2. Calendario Mensual de Mantenimiento

**Vista Principal**:
- Calendario mensual con días del mes
- Cada día muestra: Cantidad de actividades, Indicador de carga (verde/amarillo/rojo)
- Click en día → Muestra detalle de actividades programadas

**Filtros Laterales**:
- Rango de Fechas (desde/hasta)
- Cliente (múltiple selección)
- Sede (múltiple selección)
- Tipo de Actividad (múltiple selección)
- Técnico Asignado (múltiple selección)
- Estado (Programada, En Ejecución, Cerrado, Culminado)

**Código de Colores**:
- 🟦 Azul: Preventivo
- 🟩 Verde: Inspección
- 🟨 Amarillo: Calibración
- 🟪 Morado: Limpieza
- 🟧 Naranja: Otro

**Acciones Rápidas**: Crear Nueva Actividad, Ver Gantt, Exportar Calendario, Imprimir

#### 21.3.3. Vista Gantt de Programación

**Componentes**:
- Eje temporal horizontal (semanas/meses)
- Lista de actividades vertical (agrupadas por cliente/sede)
- Barras de duración de cada actividad
- Hitos (fechas críticas, vencimientos)
- Líneas de dependencia (si aplica)
- Indicador de progreso (% completado)

**Interactividad**:
- Arrastrar barras para reprogramar
- Zoom in/out en timeline
- Filtros dinámicos
- Export a PDF/imagen

**Botones**: Volver a Calendario, Ajustar Fechas, Guardar Cambios, Exportar

#### 21.3.4. Pantalla de Detalle de Actividad Programada

**Información**:
- Código PAM (solo lectura)
- Tipo de Actividad, Cliente/Sede, Equipo
- Fecha Programada vs Fecha Real (si ejecutada)
- Técnico Asignado, Recursos, Duración

**Documentación**:
- OT asociada (enlace)
- Protocolo de mantenimiento (adjunto)
- Evidencias fotográficas
- Informe de cierre

**Acciones**: Editar Programación, Reprogramar, Cancelar, Generar OT, Cerrar Actividad

#### 21.3.6. Módulo de Gestión de OT's

**Visualización Dual**:
- **Modo Kanban**: Columnas por estado (Programada, En Proceso, Ejecutada, Con Atraso, Anulada), tarjetas arrastrables, indicador de criticidad por color
- **Modo Listado**: Tabla con 100% de OT's, scroll infinito, ordenable por columnas

**Tabla de OT's** (Modo Listado):
- Código OT, Código PAM, Concepto, Estado, Criticidad, Cliente, Sede, Proveedor
- Grupo MTTO, Sub Grupo MTTO, Centro de Costo, Tipo (Preventivo/Correctivo)
- Fecha Creación, Fecha Programada, Fecha Aprobación
- Creado Por, Solicitado Por
- Tiempo de Atención (horas/minutos/días), Estado Temporal (Dentro de Tiempo/Atrasada)
- Acciones (Ver, Editar, Firmar, Exportar PDF, Anular)

**Filtros Avanzados** (panel lateral):
- Estado (múltiple), Criticidad (múltiple), Cliente (búsqueda), Sede (búsqueda)
- Proveedor (búsqueda), Grupo MTTO (lista), Sub Grupo MTTO (lista), Centro de Costo (lista)
- Tipo de Mantenimiento (Preventivo/Correctivo), Fechas (rango: creación, programación, aprobación)
- Creado Por (lista usuarios), Solicitado Por (lista usuarios)
- Estado Temporal (Dentro de Tiempo/Atrasada), Incidencia Asociada (Sí/No)

**Búsqueda Global**: Por cualquier campo, autocompletado, búsqueda inteligente

**Alertas Personalizadas**: Usuario configura alertas por fecha programación, cambio de estado, asignaciones, atrasos; canal: correo/SMS/WhatsApp

**Botones**: Crear OT Manual, Cambiar Vista (Kanban/Listado), Exportar Todo, Configurar Alertas

#### 21.3.7. Pantalla de Detalle de OT

**Información General**:
- Código OT, Código PAM (si aplica), Estado, Criticidad
- Incidencia Asociada (enlace, concepto heredado)

**Trazabilidad**:
- Creado Por, Solicitado Por, Fecha Creación, Fecha Aprobación

**Asociaciones**:
- Grupo MTTO, Sub Grupo MTTO, Centro de Costo
- Tipo de Mantenimiento, Cliente, Sede/Inmueble, Proveedor

**Programación**:
- Fecha Inicio Calendarizada, Duración Estimada
- Tiempo de Atención Calculado (horas/minutos/días), Estado: Dentro de Tiempo/Atrasada

**Firma Digital**: Sección para firma del responsable al cerrar

**Botones**: Editar, Firmar y Cerrar, Exportar a PDF, Imprimir, Anular OT

#### 21.3.5. Pantalla de Cierre de Mantenimiento

**Campos**:
- Código PAM (solo lectura)
- Fecha y Hora Real de Ejecución (obligatorio)
- Actividades Realizadas (checklist + texto)
- Hallazgos/Observaciones (texto largo)
- Materiales Utilizados (tabla: Material, Cantidad, Unidad)
- Próximo Mantenimiento Sugerido (fecha, opcional)
- Evidencias Fotográficas (mínimo 2, antes/después)
- Adjuntar Protocolo/Informe (PDF, obligatorio)

**Conformidad**:
- Estado del Equipo Post-Mantenimiento (Operativo, Con Observaciones, Requiere Reparación)
- Firma Digital del Técnico (obligatorio)
- Firma/Conformidad del Cliente (si aplica)

**Botones**: Guardar Borrador, Enviar a Validación, Cerrar Mantenimiento

---

### 21.4. Reglas de Negocio

1. **Generación de Códigos PAM**: Automática y secuencial; formato PAM-[Año]-[Mes]-[Cliente]-[Correlativo]; único e irrepetible
2. **Modificación de Programación**: Solo Gerente de FM y FM pueden crear/modificar; Técnicos solo pueden cerrar/ejecutar
3. **Conflictos de Calendario**: Sistema alerta si técnico tiene 2+ actividades en mismo turno/día; permite override con justificación
4. **Recurrencia Automática**: Sistema genera automáticamente próximas ocurrencias según frecuencia (mensual, trimestral, etc.) hasta 12 meses adelante
5. **Fecha de Inicio**: Debe ser = Día de ejecución programado en calendario; modificable hasta 24 horas antes
6. **Reprogramación**: Máximo 3 reprogramaciones por actividad; más requiere aprobación Gerente FM; debe registrarse motivo
7. **Cierre Obligatorio**: Actividades en estado "En Ejecución" deben cerrarse en 48 horas; alerta automática a Supervisor
8. **Validación de Recursos**: Sistema valida disponibilidad de recursos al programar; bloquea recursos asignados
9. **Estados de OT**: 6 estados posibles (Operativo, En Proceso, Programada, Ejecutada, Con Atraso, Anulada); transiciones controladas
10. **Criticidad por Default**: Nueva OT se crea con criticidad "Normal"; Urgente/Emergencia debe indicarse explícitamente
11. **Incidencias Asociadas**: Si OT proviene de incidencia, hereda el concepto automáticamente; asociación inmutable
12. **Firma Digital Obligatoria**: OT no puede cerrarse sin firma digital del responsable; firma registra usuario, fecha y hora
13. **Cálculo de Tiempos**: Sistema calcula automáticamente tiempo de atención desde fecha programada; marca como "Atrasada" si excede plazo
14. **Alertas Multicanal**: Usuario elige canal preferido (correo/SMS/WhatsApp); alertas se envían según configuración personal
15. **Grupos MTTO**: Grupo y Sub Grupo MTTO son obligatorios; deben existir en catálogo maestro; lista desplegable con búsqueda

---

### 21.5. Consideraciones Técnicas

- **Almacenamiento**: Calendario con retención 24 meses; tareas programadas archivadas 7 años; backup diario
- **Seguridad**: Acceso por rol (Gerente FM: full, FM: crear/editar, Técnico: ejecutar/cerrar, Supervisor: validar); auditoría completa
- **Performance**: Carga calendario < 2 seg; generación Gantt < 3 seg; filtros en tiempo real < 1 seg
- **Sincronización**: Calendario se actualiza cada 5 minutos; notificaciones en tiempo real; sincronización con calendarios externos (Outlook, Google Calendar) opcional
- **Notificaciones**: Recordatorios 24h antes de mantenimiento; alertas de conflictos; notificación de cierre pendiente; resumen semanal de programación
- **Escalabilidad**: Soportar hasta 10,000 actividades programadas simultáneamente; 200 técnicos activos; múltiples clientes y sedes

---

**Nota Final**: El módulo de Programación de Mantenimiento y Actividades centraliza la planificación de mantenimientos preventivos mediante calendario visual y Gantt, generando automáticamente códigos PAM únicos y OT's asociadas, asegurando control completo desde programación hasta cierre con trazabilidad total.

