# DOCUMENTO DE ESPECIFICACIONES NO TÉCNICAS - SISTEMA FM

## 1. Objetivo

Registrar los acuerdos, configuraciones y parámetros definidos para la implementación del sistema FM, incluyendo características de equipos, codificación, parámetros técnicos, mantenimiento y reportes e integración con QR. Asegurando claridad, alcance para todos los participantes y equipos involucrados.

## 2. Ingreso al sistema

a. El ingreso deberá realizarse mediante un usuario y contraseña.

b. El usuario deberá logarse mediante un correo electrónico

c. La contraseña deberá generarla el usuario

d. Le debe llegar un token a su correo valido por 5 minutos para la creación de la contraseña

e. Debe tener un log de auditoria (con reporte)

f. Debe llegar un correo de notificación cuando se cree la contraseña o se restablezca, deberá llegar A un correo (parametrizable) del administrador

g. Debe de considerarse el restablecimiento de la contraseña, manejado también por un toquen

h. Cuando un usuario es externo (Cliente o Proveedor), su registro debe ser aprobada por el rol de gerente FM

## 3. Módulo de usuarios

a. El sistema tendrá un rol super administrador el cual ingresará los perfiles. Lo usuarios externos (proveedores y clientes) su registro en el sistema deberá pasar por aprobación del gerente de FM.

b. Los roles con los que cuenta el sistema son los siguientes:
   - Gerente general
   - Gerente de FM
   - Facility manager
   - Supervisor FM
   - Planner MTTO
   - Service desk FM
   - Técnicos
   - Proveedor
   - Cliente

### Permisos con los que cuentan los roles

| Roles/Módulos - Opciones | Clientes | Proveedores | Usuarios externos (Clientes, Proveedores) |
|--------------------------|----------|-------------|-------------------------------------------|
| Superadministrador | Registrar, editar y eliminar | | |
| Gerente general | | | |
| Gerente de FM | | | Aprueba registro de usuarios |
| Facility manager | | | |
| Supervisor FM | | | |
| Planner MTTO | | | |
| Service desk FM | | | |
| Técnicos | | | |
| Proveedor | | | |
| Cliente | | | |

c. El super administrador ingresa la data del usuario todos los campos son obligatorios:
   - Tipo de documento de identidad: DNI/CE
   - Número de Documento de identidad
   - Nombres del colaborador
   - Apellidos del colaborador
   - Correo corporativo
   - Celular

## 4. Módulo de Gestión de Clientes

Sistema que permite al Superadministrador registrar y administrar clientes con código autogenerado (RUC-CECO). Incluye datos básicos (RUC, razón social, domicilio fiscal, CECO), clasificación (público/privado, interno/externo, nacional/extranjero), y permite registrar múltiples representantes, usuarios y sucursales por cliente. Cuenta con listas desplegables con búsqueda, validación de RUC único, y capacidad de crear clientes sin salir de la ventana actual. Todas las acciones quedan registradas en auditoría.

### 4.1. Datos Generales del Cliente

#### 4.1.1. Código de Cliente
- Autogenerado por el sistema
- Formato: RUC-CECO
- Ejemplo: 20123456789-001
- Campo de solo lectura

#### 4.1.2. Nombre Completo / Razón Social
- Campo obligatorio
- Máximo 200 caracteres
- Campo de texto libre

#### 4.1.3. RUC (Registro Único de Contribuyentes)
- Campo obligatorio
- 11 dígitos numéricos
- Debe ser único en el sistema
- Validación automática de formato

#### 4.1.4. Domicilio Fiscal
- Campo obligatorio
- Dirección completa del domicilio fiscal del cliente

#### 4.1.5. Tipo de Cliente
- Campo con lista desplegable
- Opciones:
  - Público
  - Privado

#### 4.1.6. CECO (Centro de Costos)
- Campo obligatorio
- Código alfanumérico
- Utilizado para generar el Código de Cliente

#### 4.1.7. Clasificación: Interno o Externo
- Campo con lista desplegable
- Opciones: Interno, Externo

#### 4.1.8. Nacional / Extranjero
- Campo con lista desplegable
- Opciones: Nacional, Extranjero

#### 4.1.9. País
- Campo con lista desplegable
- Catálogo completo de países
- Campo obligatorio

### 4.2. Información de Contacto

#### 4.2.1. Email
- Campo obligatorio
- Validación de formato de correo electrónico
- Correo electrónico corporativo del cliente

#### 4.2.2. Teléfono
- Campo obligatorio
- Formato numérico
- Número de contacto principal del cliente

#### 4.2.3. WhatsApp
- Campo opcional
- Formato numérico
- Número de WhatsApp para contacto

### 4.3. Representante(s) del Cliente

El sistema debe permitir registrar uno o más representantes del cliente. Cada representante debe contar con los siguientes datos:

#### Campos del Representante:

- **Nombre Completo** (obligatorio)
  - Campo de texto libre
  - Nombre completo del representante

- **Correo Electrónico** (obligatorio)
  - Validación de formato de correo electrónico
  - Debe cumplir con estructura estándar de email

- **Celular** (obligatorio)
  - Formato numérico
  - Campo para número de contacto del representante

- **Cargo** (obligatorio)
  - Campo de texto libre
  - Cargo o posición del representante en la organización

#### Funcionalidades:

- Agregar representante
- Editar representante
- Eliminar representante

### 4.4. Usuarios del Cliente

El sistema debe permitir registrar uno o más usuarios del cliente. Cada usuario debe contar con los siguientes datos:

#### Campos del Usuario:

- **Nombre Completo** (obligatorio)
  - Campo de texto libre
  - Nombre completo del usuario

- **Correo Electrónico** (obligatorio)
  - Validación de formato de correo electrónico
  - Debe cumplir con estructura estándar de email

- **Celular** (obligatorio)
  - Formato numérico
  - Campo para número de contacto del usuario

- **Cargo** (obligatorio)
  - Campo de texto libre
  - Cargo o posición del usuario en la organización

#### Proceso de Aprobación:

- Estos usuarios serán aprobados por el rol de **Gerente de FM**

### 4.5. Sucursales del Cliente

El sistema debe permitir registrar una o más sucursales del cliente. Cada sucursal debe contar con:

#### Campos de la Sucursal:

- **Dirección** (obligatorio)
  - Dirección completa de la sucursal
  - Campo de texto libre

- **Sucursal Principal**
  - Opción para marcar una sucursal como principal
  - Solo una sucursal puede ser marcada como principal

### 4.6. Lógica de Generación del Código de Cliente

El sistema debe generar automáticamente el Código de Cliente mediante la concatenación de dos campos:

#### Fórmula:
```
Código de Cliente = RUC + "-" + CECO
```

#### Ejemplo:
- RUC ingresado: `20123456789`
- CECO ingresado: `001`
- Código generado: `20123456789-001`

#### Reglas:
- El código se genera automáticamente al guardar el registro del cliente
- El campo es de solo lectura, el usuario no puede editarlo
- El código debe ser único en el sistema
- El sistema debe validar que no exista duplicidad antes de guardar

### 4.7. Validaciones del Módulo de Clientes

- **RUC**: Debe ser único en el sistema (no se permite duplicados)
- **Formato de RUC**: 11 dígitos numéricos
- **Correo Electrónico**: Validación de formato válido (ejemplo@dominio.com)
- **Campos Obligatorios**: El sistema no debe permitir guardar si faltan campos obligatorios
- **CECO**: Campo obligatorio para poder generar el Código de Cliente

### 4.8. Funcionalidades de Búsqueda

El módulo debe contar con las siguientes opciones de búsqueda:

- Búsqueda por RUC (lista desplegable con autocompletado)
- Búsqueda por Razón Social 
- Búsqueda por Código de Cliente
- Búsqueda por Tipo de Cliente (Público/Privado)
- Búsqueda por ubicación
- Filtros combinados

## 5. Modulo de gestion integral de inmuebles

El módulo de gestión de inmuebles permite registrar y administrar las sedes o inmuebles asociados a los clientes. Cada inmueble puede estar vinculado a un cliente específico.

### 5.1. Campos del Formulario de Inmueble/Sede

#### 5.1.1. Información General

**Código de Inmueble o Sede**

- Autogenerado por el sistema
- Formato sugerido: INM-0001, INM-0002, etc.
- Campo de solo lectura
- Único en el sistema

**Nombre del Inmueble o Sede**

- Campo con lista desplegable para búsqueda
- Debe permitir crear o agregar nuevos inmuebles sin salir de la ventana actual
- Funcionalidad de autocompletado
- Al detectar que el inmueble no existe, debe mostrar opción: "¿Desea agregar un nuevo inmueble?"

#### 5.1.2. Ubicación del Inmueble

**Dirección del Inmueble o Sede**

- Campo obligatorio
- Dirección completa del inmueble

**Ubicación**

- Campo con lista desplegable
- Opciones:
  - Lima
  - Provincias

**Zona Geográfica**

- Campo con lista desplegable
- Opciones:
  - Zona Norte
  - Zona Sur
  - Zona Centro
  - Zona Oriente

**Departamento**

- Campo con lista desplegable
- Catálogo de departamentos del Perú
- Debe contar con funcionalidad de búsqueda para facilitar la selección

**Provincia**

- Campo con lista desplegable
- Catálogo de provincias del Perú
- Se debe filtrar según el departamento seleccionado
- Debe contar con funcionalidad de búsqueda

**País**

- Campo con lista desplegable
- Valor por defecto: Perú
- El sistema debe colocar automáticamente "Perú" como país predeterminado
- Campo editable si el inmueble se encuentra en otro país

#### 5.1.3. Fotos del Inmueble

**Fotos del Inmueble o Sede**

- El sistema debe permitir cargar hasta 3 fotos del inmueble
- Formatos permitidos: PNG, JPG
- Tamaño máximo recomendado: 5MB por archivo
- Debe mostrar vista previa de las imágenes cargadas
- Opción para eliminar fotos individuales

### 5.2. Filtros de Búsqueda

El módulo debe contar con filtros de búsqueda avanzados mediante listas desplegables:

- Búsqueda por Código de Inmueble
- Búsqueda por Nombre de Inmueble
- Búsqueda por Ubicación (Lima/Provincias)
- Búsqueda por Zona Geográfica
- Búsqueda por Departamento
- Búsqueda por Provincia
- Búsqueda por Cliente asociado
- Filtros combinados

### 5.3. Validaciones del Módulo de Inmuebles

- **Código de Inmueble**: Único en el sistema, generado automáticamente
- **Fotos**: Máximo 3 archivos, solo formatos PNG y JPG
- **Tamaño de archivos**: No exceder 5MB por imagen
- **Campos obligatorios**: Nombre, Dirección, Ubicación, Departamento, Provincia
- **País por defecto**: El sistema debe asignar "Perú" automáticamente
- **Relación con Departamento-Provincia**: La lista de provincias debe filtrarse según el departamento seleccionado

### 5.4. Relación entre Clientes e Inmuebles

#### 5.4.1. Modelo Relacional

- Un cliente puede tener múltiples inmuebles (relación 1 a muchos)
- Cada inmueble debe estar asociado a un cliente específico
- El sistema debe permitir visualizar todos los inmuebles asociados a un cliente
- Debe existir un campo o filtro para buscar inmuebles por cliente

#### 5.4.2. Visualización de Inmuebles por Cliente

En la ficha del cliente, debe existir una sección que muestre:

- Lista de inmuebles asociados al cliente
- Código y nombre de cada inmueble
- Dirección y ubicación
- Opciones para agregar, editar o eliminar inmueble

#### 5.4.3. Funcionalidad Especial: Crear Inmueble Sin Salir de Ventana

Cuando el usuario está registrando información del cliente y necesita agregar un nuevo inmueble que no existe en el sistema, debe poder hacerlo sin salir de la ventana actual.

**Flujo:**

1. El usuario comienza a escribir en el campo "Nombre del Inmueble o Sede"
2. Si el sistema no encuentra coincidencias, debe mostrar la opción: **[+ Crear Nuevo Inmueble]**
3. Al hacer clic, se abre un formulario modal o emergente con los campos necesarios
4. El usuario completa los datos del nuevo inmueble
5. Al guardar, el nuevo inmueble queda disponible y seleccionado automáticamente
6. El usuario puede continuar con el registro sin interrupciones

## 6. Gestión de Proveedores

Sistema que permite al Superadministrador registrar y administrar proveedores con código autogenerado (RUC). Incluye datos básicos (RUC, razón social, domicilio fiscal), clasificación (público/privado, nacional/extranjero), información de contacto, zona de cobertura y disponibilidad de servicios de emergencia. Permite registrar múltiples representantes por proveedor. Cuenta con listas desplegables con búsqueda, validación de RUC único, y capacidad de crear proveedores sin salir de la ventana actual. El sistema detecta proveedores cercanos al programar servicios, priorizando por zona de cobertura. Todas las acciones quedan registradas en auditoría.

### 6.1. Datos Generales del Proveedor

#### 6.1.1. Código de Proveedor
- Autogenerado por el sistema
- Formato: RUC
- Ejemplo: 20123456789
- Campo de solo lectura
- Único en el sistema

#### 6.1.2. Nombre Completo / Razón Social
- Campo obligatorio
- Máximo 200 caracteres
- Campo de texto libre
- Cuenta con lista desplegable para facilitar búsqueda
- Funcionalidad de autocompletado

#### 6.1.3. RUC (Registro Único de Contribuyentes)
- Campo obligatorio
- 11 dígitos numéricos
- Debe ser único en el sistema
- Validación automática de formato
- Campo con lista desplegable para búsqueda

#### 6.1.4. Domicilio Fiscal
- Campo obligatorio
- Dirección completa del domicilio fiscal del proveedor

#### 6.1.5. Tipo de Proveedor
- Campo con lista desplegable
- Opciones:
  - Público
  - Privado

#### 6.1.6. Nacional / Extranjero
- Campo con lista desplegable
- Opciones: Nacional, Extranjero

#### 6.1.7. País
- Campo con lista desplegable
- Catálogo completo de países
- Campo obligatorio

### 6.2. Información de Ubicación y Contacto

#### 6.2.1. Dirección del Proveedor
- Campo obligatorio
- Dirección completa de oficinas o sede principal

#### 6.2.2. Ubicación
- Campo con lista desplegable
- Opciones:
  - Lima
  - Provincias

#### 6.2.3. Departamento
- Campo con lista desplegable
- Catálogo de departamentos del Perú
- Ubicación de las oficinas del proveedor
- Debe contar con funcionalidad de búsqueda

#### 6.2.4. Email
- Campo obligatorio
- Validación de formato de correo electrónico
- Correo electrónico corporativo del proveedor

#### 6.2.5. Teléfono
- Campo obligatorio
- Formato numérico
- Número de contacto principal del proveedor

#### 6.2.6. WhatsApp
- Campo opcional
- Formato numérico
- Número de WhatsApp para contacto

### 6.3. Representante(s) del Proveedor

El sistema debe permitir registrar uno o más representantes del proveedor. Cada representante debe contar con los siguientes datos:

#### Campos del Representante:

- **Nombre Completo** (obligatorio)
  - Campo de texto libre
  - Nombre completo del representante

- **Correo Electrónico** (obligatorio)
  - Validación de formato de correo electrónico
  - Debe cumplir con estructura estándar de email

- **Celular** (obligatorio)
  - Formato numérico
  - Campo para número de contacto del representante

- **Cargo** (obligatorio)
  - Campo de texto libre
  - Cargo o posición del representante en la organización

#### Funcionalidades:

- Agregar representante
- Editar representante
- Eliminar representante

### 6.4. Zona de Cobertura

El sistema permite registrar una o más zonas de cobertura del proveedor:

#### 6.4.1. Departamento
- Campo con lista desplegable
- Catálogo de departamentos del Perú
- Permite seleccionar múltiples departamentos donde el proveedor brinda servicios

#### 6.4.2. Provincia
- Campo con lista desplegable
- Catálogo de provincias del Perú
- Se debe filtrar según el departamento seleccionado
- Permite seleccionar múltiples provincias de cobertura

#### 6.4.3. Distrito
- Campo con lista desplegable
- Catálogo de distritos del Perú
- Se debe filtrar según la provincia seleccionada
- Permite seleccionar múltiples distritos de cobertura

### 6.5. Servicios de Emergencia

#### 6.5.1. Atienden servicios de emergencia 24 x 7
- Campo tipo checkbox
- Opciones: Sí / No
- Esta información es utilizada por el sistema para priorizar proveedores en servicios de emergencia

### 6.6. Funcionalidades de Búsqueda

El módulo debe contar con las siguientes opciones de búsqueda:

- Búsqueda por RUC
- Búsqueda por Razón Social
- Búsqueda por Código de Proveedor
- Búsqueda por Tipo de Proveedor (Público/Privado)
- Búsqueda por Ubicación (Lima/Provincias)
- Búsqueda por Departamento
- Búsqueda por Zona de Cobertura
- Búsqueda por disponibilidad 24x7
- Filtros combinados

### 6.7. Validaciones del Módulo de Proveedores

- **RUC**: Debe ser único en el sistema (no se permite duplicados)
- **Formato de RUC**: 11 dígitos numéricos
- **Correo Electrónico**: Validación de formato válido (ejemplo@dominio.com)
- **Campos Obligatorios**: El sistema no debe permitir guardar si faltan campos obligatorios
- **Código de Proveedor**: Único en el sistema, generado automáticamente

## 7. Gestión de Equipos

**Propósito**: Gestionar equipos instalados en sedes/inmuebles que requieren mantenimiento preventivo y correctivo.

Sistema que permite gestionar una base de datos completa de equipos con código autogenerado basado en categoría y subcategoría. Incluye información técnica (marca, modelo, serie), ubicación geográfica, integración con códigos QR, información financiera (precio con cálculo automático de IGV), y capacidad de almacenar fotografías. Cuenta con filtros de búsqueda avanzados por todas las variables del equipo.

### 7.1. Datos Generales del Equipo

#### 7.1.1. Código de Equipo
- Autogenerado por el sistema
- Formato: [Abreviatura Categoría] + [Número Subcategoría] + [Secuencial]
- Ejemplo: HV001 (HVAC + Ventiladores + 001)
- Campo de solo lectura
- Único en el sistema

#### 7.1.2. Descripción del Equipo
- Campo obligatorio
- Detalle completo del equipo
- Campo de texto libre

#### 7.1.3. Tipo de Equipo
- Campo con lista desplegable
- Opciones:
  - Equipos Mayores
  - Equipos Menores

#### 7.1.4. Marca del Equipo
- Campo obligatorio
- Campo de texto libre o lista desplegable

#### 7.1.5. Modelo del Equipo
- Campo obligatorio
- Campo alfanumérico
- Modelo específico del equipo

#### 7.1.6. Número de Serie
- Campo alfanumérico
- Identificador único del fabricante

### 7.2. Categorización del Equipo

#### 7.2.1. Categoría
El sistema cuenta con las siguientes categorías predefinidas:

| Categoría | Abreviatura |
|-----------|-------------|
| HVAC | HV |
| Sistema Eléctrico | SE |
| SACI | SA |
| Equipos de Sastrería | ES |
| Audio y Video | AV |

#### 7.2.2. Subcategoría
El sistema cuenta con subcategorías numeradas:

| Subcategoría | Código (3 dígitos) |
|--------------|-------------------|
| Ventiladores | 001 |
| Tablero | 002 |
| Panel de alarmas | 003 |
| Vaporizador | 004 |
| Proyector | 005 |
| Detectores | 006 |
| Máquina de coser | 007 |

#### 7.2.3. Equipo Asociado
- Campo opcional
- Permite vincular el equipo con otro equipo relacionado
- Lista desplegable con búsqueda

### 7.3. Ubicación del Equipo

#### 7.3.1. Ubicación
- Campo con lista desplegable
- Opciones:
  - Lima
  - Provincias

#### 7.3.2. Ubicación por Sede
- Campo con lista desplegable
- Muestra las sedes registradas en el sistema
- Vinculado con el módulo de Inmuebles

#### 7.3.3. Departamento
- Campo con lista desplegable
- Catálogo de departamentos del Perú
- Debe contar con funcionalidad de búsqueda

#### 7.3.4. Provincia
- Campo con lista desplegable
- Catálogo de provincias del Perú
- Se debe filtrar según el departamento seleccionado
- Debe contar con funcionalidad de búsqueda

#### 7.3.5. País
- Campo con lista desplegable
- Valor por defecto: Perú
- Campo editable si el equipo se encuentra en otro país

### 7.4. Información Administrativa

#### 7.4.1. Centro de Costo (CECO)
- Campo obligatorio
- Código alfanumérico
- Asociado al cliente o área responsable

#### 7.4.2. Código QR
- Campo para ingresar código QR del equipo
- Permite vincular el equipo con sistema de identificación por QR
- Campo alfanumérico

### 7.5. Información Financiera

#### 7.5.1. Precio del Equipo
- Campo obligatorio
- Formato numérico decimal
- Precio base del equipo (sin IGV)

#### 7.5.2. IGV
- Calculado automáticamente por el sistema
- Fórmula: Precio del Equipo × 18%
- Campo de solo lectura

#### 7.5.3. Precio Total (Incluido IGV)
- Calculado automáticamente por el sistema
- Fórmula: Precio del Equipo + IGV
- Campo de solo lectura

### 7.6. Fotografías del Equipo

#### 7.6.1. Fotos del Equipo
- El sistema debe permitir cargar hasta 3 fotos del equipo
- Formatos permitidos: PNG, JPG
- Tamaño máximo recomendado: 5MB por archivo
- Debe mostrar vista previa de las imágenes cargadas
- Opción para eliminar fotos individuales

### 7.7. Lógica de Generación del Código de Equipo

El sistema debe generar automáticamente el Código de Equipo mediante la siguiente estructura:

#### Fórmula:
```
Código de Equipo = [Abreviatura Categoría] + [Código Subcategoría] + [Número Secuencial]
```

#### Ejemplo:
- Categoría seleccionada: HVAC (Abreviatura: HV)
- Subcategoría seleccionada: Ventiladores (Código: 001)
- Número secuencial: Próximo disponible en el sistema
- Código generado: **HV001**

#### Reglas:
- El código se genera automáticamente al guardar el registro del equipo
- El campo es de solo lectura
- El código debe ser único en el sistema
- El número secuencial se incrementa automáticamente por cada nuevo equipo de la misma categoría y subcategoría

### 7.8. Funcionalidades de Búsqueda

El módulo debe contar con filtros de búsqueda por todas las variables:

- Búsqueda por Código de Equipo
- Búsqueda por Descripción
- Búsqueda por Tipo de Equipo (Mayores/Menores)
- Búsqueda por Marca
- Búsqueda por Modelo
- Búsqueda por Número de Serie
- Búsqueda por Categoría
- Búsqueda por Subcategoría
- Búsqueda por Ubicación (Lima/Provincias)
- Búsqueda por Sede
- Búsqueda por Departamento
- Búsqueda por Provincia
- Búsqueda por Centro de Costo
- Búsqueda por Código QR
- Búsqueda por rango de precio
- Filtros combinados

### 7.9. Validaciones del Módulo de Equipos

- **Código de Equipo**: Único en el sistema, generado automáticamente
- **Fotos**: Máximo 3 archivos, solo formatos PNG y JPG
- **Tamaño de archivos**: No exceder 5MB por imagen
- **Campos obligatorios**: Código, Descripción, Tipo, Marca, Modelo, Ubicación, Centro de Costo, Precio
- **Precio**: Debe ser un valor numérico positivo
- **IGV**: Cálculo automático, no editable manualmente
- **Código QR**: Debe ser único en el sistema
- **Relación Departamento-Provincia**: La lista de provincias debe filtrarse según el departamento seleccionado

## 8. Gestión de Herramientas

**Propósito**: Gestionar herramientas de trabajo asignadas a técnicos o almacenadas en inventario.

Sistema que permite gestionar una base de datos completa de herramientas, instrumentos y suministros con código autogenerado. Incluye información técnica (marca, serie), asignación a técnicos o almacenes, ubicación geográfica, integración con códigos QR, información financiera (precio con cálculo automático de IGV), y capacidad de almacenar fotografías. Cuenta con filtros de búsqueda avanzados por todas las variables.

### 8.1. Clasificación de Herramientas

El sistema cuenta con tres tipos principales:

| Código | Tipo | Ejemplo |
|--------|------|---------|
| H | Herramienta | Set de Alicates, Wincha, Martillo |
| I | Instrumento | Pinza Amperimétrica, Pirómetro, Taladro |
| S | Suministros | Cinta aislante, Cintillos, Tarugos |

### 8.2. Datos Generales de Herramientas

**Código de Herramienta**
- Autogenerado por el sistema
- Formato: [Tipo] + [Número Secuencial]
- Ejemplos: H01, I02, S03
- Campo de solo lectura
- Único en el sistema

**Descripción**
- Campo obligatorio
- Detalle completo de la herramienta o suministro
- Campo de texto libre

**Tipo de Herramienta**
- Campo con lista desplegable
- Opciones: Herramienta, Instrumento, Suministros
- Determina el prefijo del código

**Marca**
- Campo obligatorio
- Marca del fabricante
- Ejemplos: Stanley, Bosch, 3M, Fluker

**Número de Serie**
- Campo alfanumérico
- Identificador único del fabricante (cuando aplique)

**Unidad de Medida**
- Campo con lista desplegable
- Opciones: Und (Unidad), Pqt (Paquete), Set, etc.

**Cantidad**
- Campo numérico
- Cantidad de unidades disponibles

### 8.3. Asignación

**Asignado a**
- Campo con lista desplegable
- Opciones:
  - Técnico (nombre del técnico)
  - Almacén (ubicación del almacén)
- Permite rastrear la ubicación actual de la herramienta

**Ubicación**
- Cliente asociado
- Sede asociada
- Ubicación específica dentro de la sede

### 8.4. Información Administrativa

**Fecha de Compra**
- Campo con selector de fecha (lista desplegable)
- Formato: DD/MM/AAAA
- Campo obligatorio

**Centro de Costo (CECO)**
- Campo obligatorio
- Código alfanumérico
- Las herramientas deben estar asignadas a un centro de costo

**Código QR**
- Campo alfanumérico
- Permite vincular la herramienta con sistema de identificación por QR
- Debe ser único en el sistema

### 8.5. Ubicación Geográfica

**Departamento**
- Campo con lista desplegable
- Catálogo de departamentos del Perú

**Distrito**
- Campo con lista desplegable
- Catálogo de distritos del Perú
- Se filtra según departamento seleccionado

**País**
- Campo con lista desplegable
- Valor por defecto: Perú

### 8.6. Información Financiera

**Precio sin IGV**
- Campo obligatorio
- Formato numérico decimal
- Precio unitario de la herramienta

**IGV**
- Calculado automáticamente por el sistema
- Fórmula: Precio sin IGV × 18%
- Campo de solo lectura

**Precio con IGV**
- Calculado automáticamente por el sistema
- Fórmula: Precio sin IGV + IGV
- Campo de solo lectura

### 8.7. Fotografías

**Fotos de Herramienta**
- El sistema debe permitir cargar hasta 3 fotos
- Formatos permitidos: PNG, JPG, PDF
- Tamaño máximo recomendado: 5MB por archivo
- Debe mostrar vista previa de las imágenes cargadas
- Opción para eliminar fotos individuales

### 8.8. Catálogo de Herramientas Predefinidas

El sistema incluye un catálogo inicial de herramientas comunes:

| Código | Tipo | Descripción | Marca | Asignación | Unidad | Cantidad |
|--------|------|-------------|-------|------------|--------|----------|
| H01 | Herramienta | Set de Alicates dieléctricos | Stanley | Técnico | Und | 1 |
| H02 | Herramienta | Set de alicates dieléctricos Universal, punta, corte | Stanley | Técnico | Und | 1 |
| H03 | Herramienta | Wincha métrica | Stanley | Técnico | Und | 1 |
| H04 | Herramienta | Martillo mango de goma | Stanley | Técnico | Und | 1 |
| H05 | Herramienta | Llave francesa de 8" | Stanley | Técnico | Und | 1 |
| H06 | Herramienta | Llave stilson de 10" | Stanley | Técnico | Und | 1 |
| H07 | Herramienta | Set de brocas para madera | Stanley | Técnico | Und | 1 |
| H08 | Herramienta | Set de brocas para fierro | Stanley | Técnico | Und | 1 |
| H09 | Herramienta | Set de brocas para concreto | Stanley | Técnico | Und | 1 |
| H10 | Herramienta | Nivel profesional | Stanley | Técnico | Und | 1 |
| H11 | Herramienta | Cúter retráctil con seguro | Stanley | Técnico | Und | 1 |
| I01 | Instrumento | Pinza amperimétrica de 1000 Vac | Fluker | Técnico | Und | 1 |
| I02 | Instrumento | Pirómetro digital láser | Kusites | Técnico | Und | 1 |
| I03 | Instrumento | Taladro eléctrico | Bosch | Técnico | Und | 1 |
| I04 | Instrumento | Taladro atornillador con batería | Bosch | Técnico | Und | 1 |
| S01 | Suministros | Cinta aislante | 3M | Técnico | Und | 1 |
| S02 | Suministros | Paquete de cintillos | Nacional | Técnico | Pqt | 1 |
| S03 | Suministros | Tarugos de PVC | Nacional | Técnico | Pqt | 1 |

### 8.9. Funcionalidades de Búsqueda

Filtros de búsqueda por todas las variables:

- Búsqueda por Código de Herramienta
- Búsqueda por Descripción
- Búsqueda por Tipo (Herramienta/Instrumento/Suministros)
- Búsqueda por Marca
- Búsqueda por Número de Serie
- Búsqueda por Asignado a (Técnico/Almacén)
- Búsqueda por Cliente
- Búsqueda por Sede
- Búsqueda por Departamento
- Búsqueda por Distrito
- Búsqueda por Centro de Costo
- Búsqueda por Código QR
- Búsqueda por fecha de compra
- Búsqueda por rango de precio
- Filtros combinados

### 8.10. Validaciones

- **Código de Herramienta**: Único en el sistema, generado automáticamente
- **Fotos**: Máximo 3 archivos, formatos PNG, JPG, PDF permitidos
- **Tamaño de archivos**: No exceder 5MB por imagen
- **Campos obligatorios**: Código, Descripción, Tipo, Marca, Asignado a, Fecha de Compra, Centro de Costo, Precio
- **Precio**: Debe ser un valor numérico positivo
- **IGV**: Cálculo automático, no editable manualmente
- **Código QR**: Debe ser único en el sistema
- **Cantidad**: Debe ser un valor numérico positivo mayor a cero

## 9. Gestión de Contratos

**Propósito**: Gestionar el ciclo completo de contratos con clientes, desde la solicitud inicial hasta la firma electrónica y envío al cliente, incluyendo revisiones, observaciones y aprobaciones.

Sistema que permite gestionar el flujo de contratos de manera colaborativa entre FM, Cliente, Legal y Gerente General. Incluye carga de documentos, gestión de versiones, registro de observaciones, notificaciones automáticas, firma electrónica y auditoría completa. El sistema maneja dualidad de moneda (S/. y $), tipo de cambio automático desde SUNAT, gestión de IGV y cálculo de FEE.

**IMPORTANTE - Arquitectura de Dos Frentes:**

El módulo de Gestión de Contratos está diseñado con **dos interfaces separadas e independientes**:

1. **Módulo FM (Interno)** - Sección 9.1 a 9.10
   - Interface administrativa completa para usuarios internos
   - Roles: Superadministrador, Gerente General, Gerente de FM, Facility Manager, etc.
   - Gestión completa del ciclo de contratos
   - Configuración de FEE, IGV, documentos, estados
   - Auditoría y reportes avanzados

2. **Portal de Clientes (Externo)** - Sección 9.11
   - Interface exclusiva y simplificada para clientes
   - Acceso mediante credenciales propias
   - Vista limitada solo a información del cliente
   - Funcionalidades específicas: consulta, descarga, carga de contrapropuestas, firma
   - Dashboard personalizado por cliente

Ambos frentes comparten la misma base de datos pero tienen interfaces, permisos y funcionalidades diferenciadas según el tipo de usuario.

### 9.1. Estados del Contrato

El sistema debe manejar los siguientes estados del contrato:

| Estado | Descripción |
|--------|-------------|
| Recibido | Contrato inicial cargado al sistema (primer estado) |
| En Revisión | FM está revisando el contrato |
| Con Observaciones | FM registró observaciones al contrato |
| Observaciones Enviadas | Sistema notificó observaciones al cliente |
| Contrapropuesta Recibida | Cliente envió contrapropuesta (cargada al sistema) |
| En Revisión Legal | Contrato enviado a Legal para revisión |
| Legal con Observaciones | Legal envió observaciones y correcciones |
| Propuesta Enviada | FM envió 2da propuesta al cliente |
| Aceptado | Cliente aceptó la propuesta |
| En Firma | Habilitado para firma electrónica |
| Firmado | Contrato firmado por todas las partes |
| Finalizado | Contrato enviado al cliente y archivado |

### 9.2. Datos Generales del Contrato

#### 9.2.1. Código de Contrato
- Autogenerado por el sistema
- Formato: CTR-AAAA-NNNN (Ejemplo: CTR-2026-0001)
- Campo de solo lectura
- Único en el sistema

#### 9.2.2. Cliente
- Campo con lista desplegable
- Vinculado al módulo de Gestión de Clientes
- Campo obligatorio

#### 9.2.3. Tipo de Cliente
- Se obtiene automáticamente del cliente seleccionado
- Opciones: Interno / Externo
- Determina el cálculo del FEE

#### 9.2.4. Fecha de Solicitud
- Campo con selector de fecha
- Fecha en que FM solicita el contrato
- Se registra automáticamente al crear la solicitud

#### 9.2.5. Fecha de Vigencia
- Fecha de inicio de vigencia del contrato
- Campo obligatorio

#### 9.2.6. Fecha de Vencimiento
- Fecha de fin de vigencia del contrato
- Campo obligatorio

#### 9.2.7. Moneda
- Campo con lista desplegable
- Opciones: Soles (S/.) / Dólares ($)
- Campo obligatorio

### 9.3. Gestión de Documentos del Contrato

#### 9.3.1. Carga de Contrato Inicial
- El Gerente de FM debe cargar el contrato recibido del cliente
- Formatos permitidos: PDF, DOCX
- Tamaño máximo: 10MB
- El sistema debe registrar:
  - Fecha y hora de carga
  - Usuario que cargó el documento
  - Versión del documento (se inicia en v1.0)

#### 9.3.2. Versionado de Documentos
- El sistema debe mantener historial completo de versiones
- Cada nueva carga incrementa la versión
- Formato de versión: v1.0, v1.1, v2.0, etc.
- Se debe permitir descargar versiones anteriores
- No se pueden eliminar versiones anteriores

#### 9.3.3. Carga de Contrapropuestas
- Cuando el cliente envía contrapropuesta (por correo), FM debe cargarla al sistema
- El sistema genera nueva versión automáticamente
- Se notifica a los usuarios correspondientes

#### 9.3.4. Documentos de Legal
- Cuando Legal envía observaciones (por correo), FM debe cargarlas al sistema
- Formatos permitidos: PDF, DOCX
- Se vincula con el contrato principal

### 9.4. Gestión de Observaciones

#### 9.4.1. Registro de Observaciones por FM
- FM puede registrar observaciones al contrato
- Campos:
  - Descripción de la observación (obligatorio)
  - Tipo: Modificación / Aclaración / Rechazo
  - Prioridad: Alta / Media / Baja
  - Fecha de registro (automático)

#### 9.4.2. Envío de Observaciones
- FM envía observaciones al cliente desde el sistema
- El sistema genera notificación automática al cliente
- Se envía correo electrónico al cliente con las observaciones
- Estado del contrato cambia a "Observaciones Enviadas"

#### 9.4.3. Observaciones de Legal
- Legal envía observaciones por correo (proceso manual)
- FM debe registrar las observaciones de Legal en el sistema
- Se vinculan con el contrato

### 9.5. Sistema de Notificaciones

#### 9.5.1. Notificaciones Automáticas por Email

El sistema debe enviar notificaciones automáticas por correo electrónico en los siguientes casos:

| Evento | Destinatario | Contenido |
|--------|--------------|-----------|
| Contrato cargado al sistema | FM | Notificación de contrato disponible |
| Observaciones registradas | Gerente de FM | Notificación de observaciones pendientes |
| Observaciones enviadas al cliente | Cliente | Email con observaciones detalladas |
| Contrapropuesta cargada | FM | Notificación de nueva versión disponible |
| Contrato enviado a Legal | Legal | Notificación de contrato para revisión |
| Propuesta aceptada | Gerente de FM | Notificación de aceptación del cliente |
| Habilitado para firma | FM | Notificación para gestionar firmas |
| Contrato firmado | Gerente General | Notificación de contrato firmado |

#### 9.5.2. Notificaciones Internas del Sistema

- El sistema debe mostrar notificaciones internas para los usuarios
- Panel de notificaciones visible en el dashboard
- Contador de notificaciones pendientes
- Historial de notificaciones

### 9.6. Gestión de Firma Electrónica

#### 9.6.1. Habilitación de Firma
- Cuando el cliente acepta la propuesta (proceso manual), FM actualiza el estado en el sistema
- El sistema habilita automáticamente la opción de firma electrónica
- Se notifica a FM para gestionar las firmas

#### 9.6.2. Proceso de Firmas
- FM gestiona el proceso de firmas electrónicas
- El sistema debe registrar:
  - Firmantes requeridos (nombre, cargo, email)
  - Fecha y hora de cada firma
  - IP y ubicación de cada firma
  - Certificado digital de firma

#### 9.6.3. Validación de Firmas
- Todas las firmas requeridas deben completarse
- El sistema valida la autenticidad de cada firma
- Una vez firmado por todas las partes, el estado cambia a "Firmado"

#### 9.6.4. Notificación de Contrato Firmado
- El sistema notifica automáticamente al Gerente General
- Se genera versión final del contrato con todas las firmas
- El documento queda bloqueado para edición

### 9.7. Gestión de Moneda

- El sistema maneja dualidad de moneda (S/. y $)
- Todos los costos y ventas pueden registrarse en cualquiera de las dos monedas
- El sistema convierte automáticamente usando el tipo de cambio configurado en el módulo de **Datos Maestros** (Módulo 10)
- El tipo de cambio usado queda registrado en el contrato
- En reportes se muestra ambas monedas

### 9.8. Aplicación de IGV

- El sistema calcula automáticamente el IGV en cotizaciones
- Fórmula: Monto Base × IGV%
- Total con IGV = Monto Base + IGV
- El porcentaje de IGV se obtiene del módulo de **Datos Maestros** (Módulo 10)

### 9.9. Gestión y Cálculo del FEE

#### 9.9.1. Configuración del FEE
- Campo editable solo por **FM** y **Gerente de FM**
- Se edita durante el proceso de cotización formal
- Valor expresado en porcentaje (Ejemplo: 15%, 20%)
- El FEE queda registrado en el contrato

#### 9.9.2. Cálculo del FEE según Tipo de Cliente

**Para Cliente Externo:**
```
Precio de Venta = Costo del Servicio / (1 - FEE)
```

**Ejemplo Cliente Externo:**
- Costo del Servicio: S/. 1,000
- FEE: 20% (0.20)
- Precio de Venta = 1,000 / (1 - 0.20) = 1,000 / 0.80 = S/. 1,250

**Para Cliente Interno:**
```
Precio de Venta = Costo del Servicio × (1 + FEE)
```

**Ejemplo Cliente Interno:**
- Costo del Servicio: S/. 1,000
- FEE: 15% (0.15)
- Precio de Venta = 1,000 × (1 + 0.15) = 1,000 × 1.15 = S/. 1,150

#### 9.9.3. Visualización del FEE
- El sistema debe mostrar claramente:
  - Costo del Servicio
  - FEE aplicado (%)
  - Cálculo del FEE (monto en moneda)
  - Precio de Venta Final
  - IGV
  - Total con IGV

### 9.10. Flujo del Proceso de Contrato

#### Paso 1: Solicitud de Contrato (Proceso Manual - Fuera del Sistema)
- **Actor**: FM
- **Acción**: FM solicita contrato al cliente por correo electrónico o comunicación directa
- **Sistema**: NO se registra en el sistema. Este paso es completamente manual
- **Estado**: No aplica (proceso externo al sistema)

#### Paso 2: Inicio del Registro - Inicio del Registro - Recepción de Contrato
- **Actor**: Cliente
- **Acción**: Después de la solicitud manual (Paso 1), el cliente tiene dos opciones:
  - **Opción A (Manual)**: Cliente envía contrato por correo → Gerente de FM crea el registro en el sistema y carga el contrato
  - **Opción B (Portal)**: Cliente crea el registro y carga el contrato directamente desde el Portal de Clientes
- **Sistema**: 
  - El contrato se registra por primera vez en el sistema (independientemente de la opción)
  - El Gerente de FM o el Cliente ingresan los datos generales del contrato (código, fechas, moneda, etc.)
  - Se genera el código de contrato automáticamente
  - Se carga el documento inicial
- **Notificación**: Sistema notifica a FM y Gerente de FM
- **Estado**: Recibido (primer estado en el sistema)

#### Paso 3: Revisión y Observaciones
- **Actor**: FM
- **Acción**: FM revisa el contrato y registra observaciones en el sistema
- **Sistema**: FM coloca observaciones en el sistema
- **Estado**: En Revisión → Con Observaciones

#### Paso 4: Envío de Observaciones al Cliente
- **Actor**: FM
- **Acción**: FM envía observaciones desde el sistema
- **Sistema**: 
  - Sistema envía email al cliente con las observaciones
  - Sistema notifica al cliente (email/sistema)
- **Estado**: Observaciones Enviadas

#### Paso 5: Recepción de Contrapropuesta
- **Actor**: Cliente
- **Acción**: Cliente tiene dos opciones:
  - **Opción A (Manual)**: Cliente envía contrapropuesta por correo → FM carga la contrapropuesta al sistema
  - **Opción B (Portal)**: Cliente carga la contrapropuesta directamente desde el Portal de Clientes
- **Sistema**: La contrapropuesta queda registrada en el sistema (independientemente de la opción)
- **Notificación**: Sistema notifica automáticamente a FM
- **Estado**: Contrapropuesta Recibida

#### Paso 6: Envío a Legal
- **Actor**: FM
- **Acción**: FM envía contrato a Legal (proceso manual - correo)
- **Sistema**: FM actualiza estado en el sistema
- **Notificación**: Sistema notifica a Legal
- **Estado**: En Revisión Legal

#### Paso 7: Observaciones de Legal
- **Actor**: Legal
- **Acción**: Legal envía observaciones y correcciones por correo (proceso manual)
- **Sistema**: FM registra las observaciones de Legal en el sistema
- **Estado**: Legal con Observaciones

#### Paso 8: Segunda Propuesta
- **Actor**: FM
- **Acción**: FM envía 2da propuesta al cliente
- **Sistema**: FM carga nueva versión del contrato
- **Notificación**: Sistema notifica al cliente
- **Estado**: Propuesta Enviada

#### Paso 9: Aceptación del Cliente
- **Actor**: Cliente
- **Acción**: Cliente acepta propuesta (proceso manual)
- **Sistema**: FM actualiza el estado en el sistema
- **Notificación**: Sistema notifica a Gerente de FM
- **Estado**: Aceptado

#### Paso 10: Habilitación de Firma Electrónica
- **Actor**: Sistema
- **Acción**: Sistema habilita automáticamente opción de firma electrónica
- **Notificación**: Sistema notifica a FM
- **Estado**: En Firma

#### Paso 11: Gestión de Firmas
- **Actor**: FM
- **Acción**: FM gestiona el proceso de firmas electrónicas
- **Sistema**: Sistema registra cada firma con validadores del sistema
- **Estado**: En Firma

#### Paso 12: Contrato Firmado
- **Actor**: Sistema
- **Acción**: Sistema valida que todas las firmas estén completadas
- **Notificación**: Sistema notifica a Gerente General
- **Estado**: Firmado

#### Paso 13: Envío Final al Cliente
- **Actor**: FM
- **Acción**: FM envía contrato firmado al cliente
- **Sistema**: Sistema archiva el contrato
- **Estado**: Finalizado

### 9.11. Portal de Clientes - Bandeja de Contratos

**Propósito**: Proporcionar un portal web exclusivo para clientes con interfaz dedicada donde puedan visualizar, consultar y descargar sus contratos, así como responder a observaciones y gestionar el proceso de contrapropuestas de manera autónoma.

**NOTA IMPORTANTE:** Esta es una interfaz completamente separada del módulo administrativo de FM. El portal de clientes debe tener:
- URL dedicada (Ejemplo: clientes.sistemaFM.com o portal.sistemaFM.com)
- Diseño y branding diferenciado
- Login independiente con credenciales de cliente
- Seguridad reforzada para acceso externo
- Responsive design para acceso desde móviles y tablets

#### 9.11.1. Acceso al Portal de Clientes

**Autenticación:**
- El cliente accede mediante URL exclusiva del portal
- Login con correo electrónico y contraseña
- Validación con token (5 minutos de vigencia) al crear/restablecer contraseña
- Opción "Recordar sesión" por 30 días
- Autenticación de dos factores (opcional, configurable por Gerente FM)

**Permisos:**
- El rol **Cliente** tiene acceso a su propia bandeja de contratos
- Cada cliente solo puede ver los contratos asociados a su empresa
- Los usuarios del cliente pueden ver todos los contratos de su organización

**Acceso:**
- Menú principal: "Mis Contratos" o "Bandeja de Contratos"
- Dashboard con resumen de contratos activos, pendientes y finalizados

#### 9.11.2. Vista Principal de la Bandeja

La bandeja debe mostrar una lista de contratos con la siguiente información:

**Columnas Visibles:**
- Código de Contrato
- Fecha de Solicitud
- Estado del Contrato (con indicador visual de color)
- Fecha de Vigencia
- Fecha de Vencimiento
- Moneda (S/. o $)
- Versión del Documento
- Acciones Disponibles

**Indicadores Visuales por Estado:**
- **Solicitado**: Azul (información)
- **Con Observaciones / Observaciones Enviadas**: Amarillo (atención requerida)
- **Propuesta Enviada**: Naranja (acción requerida)
- **Aceptado / En Firma**: Verde claro (en proceso)
- **Firmado / Finalizado**: Verde (completado)

#### 9.11.3. Funcionalidades Disponibles para el Cliente

**Inicio de Contrato - Carga de Documento Inicial:**
- El cliente puede iniciar el registro de un nuevo contrato desde su portal
- Después de recibir la solicitud de FM por correo (proceso manual), el cliente accede al portal
- Botón "Nuevo Contrato" o "Cargar Contrato"
- El sistema solicita:
  - Cliente (autocompletado según el usuario logueado)
  - Fecha de Vigencia (obligatorio)
  - Fecha de Vencimiento (obligatorio)
  - Moneda (S/. o $) (obligatorio)
  - Documento de contrato inicial (PDF, DOCX, máximo 10MB)
  - Comentarios o notas adicionales (opcional)
- Al cargar el contrato inicial, el sistema:
  - Genera automáticamente el código de contrato (CTR-AAAA-NNNN)
  - Notifica automáticamente a FM y Gerente de FM
  - Crea el registro con estado "Recibido"
  - Genera versión inicial del documento (v1.0)
  - Registra fecha, hora y usuario que cargó el documento

**Visualización de Contratos:****
- Ver detalles completos del contrato
- Descargar versión actual del documento (PDF/DOCX)
- Descargar versiones anteriores del documento
- Ver historial de cambios y versiones

**Gestión de Observaciones:**
- Ver observaciones enviadas por FM
- Ver observaciones de Legal (cuando aplique)
- Botón "Descargar Observaciones" para exportar en PDF

**Carga de Contrapropuestas:**
- Cuando el estado es "Observaciones Enviadas", el cliente puede:
  - Cargar documento de contrapropuesta
  - Formatos permitidos: PDF, DOCX
  - Tamaño máximo: 10MB
  - Agregar comentarios o notas
- Al cargar contrapropuesta, el sistema:
  - Notifica automáticamente a FM
  - Cambia el estado a "Contrapropuesta Recibida"
  - Genera nueva versión del documento

**Aceptación de Propuestas:**
- Cuando el estado es "Propuesta Enviada", el cliente puede:
  - Botón "Aceptar Propuesta"
  - Botón "Enviar Observaciones Adicionales"
- Al aceptar propuesta:
  - El cliente debe confirmar la aceptación
  - El sistema cambia el estado a "Aceptado"
  - Se notifica automáticamente a FM y Gerente General

**Firma Electrónica:**
- Cuando el estado es "En Firma", el cliente puede:
  - Acceder al módulo de firma electrónica
  - Ver representantes habilitados para firmar
  - Firmar electrónicamente el contrato
- El sistema valida:
  - Identidad del firmante
  - Certificado digital
  - Registro de IP y ubicación

**Descarga de Contrato Firmado:**
- Cuando el estado es "Firmado" o "Finalizado":
  - Descargar contrato con todas las firmas electrónicas
  - Exportar certificado de firmas
  - Versión final con sello de "FIRMADO"

#### 9.11.4. Notificaciones para Clientes

El cliente recibe notificaciones automáticas por email y en el sistema en los siguientes casos:

| Evento | Contenido de la Notificación |
|--------|------------------------------|
| Contrato cargado por el cliente | "Su contrato [código] ha sido recibido y está en revisión" |
| Observaciones enviadas por FM | "Tiene observaciones pendientes en contrato [código]" |
| Propuesta enviada por FM | "Nueva propuesta disponible para contrato [código]" |
| Contrato habilitado para firma | "Contrato [código] listo para firma electrónica" |
| Contrato firmado completamente | "Contrato [código] ha sido firmado por todas las partes" |
| Contrato finalizado | "Contrato [código] ha sido enviado y archivado" |

#### 9.11.5. Panel de Resumen (Dashboard del Cliente)

**Indicadores Principales:**
- Total de contratos activos
- Contratos pendientes de acción del cliente
- Contratos en proceso de firma
- Contratos firmados este año
- Próximos vencimientos (contratos que vencen en los próximos 30 días)

**Gráficos Visuales:**
- Estados de contratos (gráfico de barras o circular)
- Línea de tiempo de contratos por mes
- Alertas de contratos por vencer

#### 9.11.6. Filtros de Búsqueda para Clientes

- Búsqueda por Código de Contrato
- Búsqueda por Estado
- Búsqueda por Fecha de Solicitud (rango)
- Búsqueda por Fecha de Vigencia (rango)
- Búsqueda por Fecha de Vencimiento (rango)
- Búsqueda por Moneda (S/. / $)
- Búsqueda por Versión del documento
- Filtro: "Requieren mi acción" (contratos con observaciones o pendientes de aceptación)
- Filtro: "Próximos a vencer" (en los próximos 30/60/90 días)
- Filtros combinados

#### 9.11.7. Validaciones en la Bandeja del Cliente

- El cliente solo puede ver contratos de su propia empresa
- Solo puede cargar contrapropuestas cuando el estado lo permite
- Solo puede aceptar propuestas cuando el estado es "Propuesta Enviada"
- La carga de documentos está limitada a formatos permitidos (PDF, DOCX)
- Tamaño máximo de archivo: 10MB
- Solo representantes autorizados pueden firmar electrónicamente

#### 9.11.8. Historial y Trazabilidad para el Cliente

El cliente puede ver:
- Historial completo del contrato
- Todas las versiones del documento
- Fecha y hora de cada acción
- Usuario que realizó cada acción (tanto del lado del cliente como de FM)
- Observaciones históricas
- Registro de notificaciones enviadas

#### 9.11.9. Exportación de Información

El cliente puede exportar:
- Lista de contratos a Excel/PDF
- Documento del contrato (cualquier versión)
- Observaciones en PDF
- Certificado de firmas electrónicas
- Reporte de contratos por período

#### 9.11.10. Características Técnicas del Portal de Clientes

**Infraestructura Separada:**
- URL independiente para el portal (subdominio o dominio propio)
- Hosting separado del sistema administrativo
- Base de datos compartida con permisos de solo lectura/escritura limitados
- API REST para comunicación con el sistema principal
- Certificado SSL/HTTPS obligatorio para seguridad

**Diseño de Interface:**
- Diseño responsive (compatible con móviles, tablets y desktop)
- Branding personalizable según configuración de FM
- Interface simplificada y amigable para usuarios no técnicos
- Menú reducido con solo las opciones relevantes para clientes
- Dashboard visual con gráficos y métricas claras
 

### 9.12. Funcionalidades de Búsqueda y Filtros (Módulo FM - Vista Interna)

El módulo debe contar con filtros de búsqueda para roles internos (FM, Gerente FM, etc.):

- Búsqueda por Código de Contrato
- Búsqueda por Cliente
- Búsqueda por Estado
- Búsqueda por Fecha de Solicitud (rango)
- Búsqueda por Fecha de Vigencia (rango)
- Búsqueda por Moneda (S/. / $)
- Búsqueda por Usuario que cargó el documento
- Búsqueda por Versión del documento
- Filtros combinados

### 9.13. Auditoría y Trazabilidad

El sistema debe registrar en auditoría:

- Todas las cargas de documentos (quién, cuándo, qué versión)
- Todos los cambios de estado del contrato
- Registro de observaciones (autor, fecha, tipo)
- Envío de notificaciones (destinatario, fecha, contenido)
- Firmas electrónicas (firmante, fecha, hora, IP, ubicación)
- Cambios en el FEE (usuario, valor anterior, valor nuevo, fecha)
- Cambios en el IGV (usuario, valor anterior, valor nuevo, fecha)
- Consultas de tipo de cambio (fecha, valor obtenido de SUNAT)
- Acciones del cliente en la bandeja (visualización, descarga, aceptación, carga de documentos)
- Acceso a la bandeja de contratos (cliente, fecha, hora, IP)

### 9.14. Validaciones del Módulo de Contratos

- **Código de Contrato**: Único en el sistema, generado automáticamente
- **Documentos**: Solo formatos PDF y DOCX permitidos
- **Tamaño de archivos**: No exceder 10MB
- **Campos obligatorios**: Cliente, Fecha de Vigencia, Fecha de Vencimiento, Moneda
- **FEE**: Debe ser un valor numérico entre 0% y 100%
- **IGV**: Solo editable por Gerente de FM (configurado en Datos Maestros)
- **Estados**: Solo pueden cambiar siguiendo el flujo establecido
- **Firmas**: Todas las firmas requeridas deben estar completas antes de marcar como "Firmado"
- **Tipo de Cambio**: Debe actualizarse diariamente desde SUNAT (configurado en Datos Maestros)

## 10. Datos Maestros del Sistema

**Propósito**: Centralizar la configuración de parámetros maestros del sistema que son utilizados de manera transversal en todos los módulos. Este módulo permite mantener la información base actualizada y garantiza la consistencia de datos en todo el sistema.

### 10.1. Tipo de Cambio (SUNAT)

Gestionar el tipo de cambio oficial del dólar estadounidense (USD) respecto al sol peruano (PEN), obtenido automáticamente desde SUNAT para ser utilizado en todas las transacciones del sistema.

#### 10.1.1. Actualización Automática del Tipo de Cambio

**Proceso Automático:**
- El sistema debe extraer el tipo de cambio desde la API de SUNAT diariamente
- Valor del Dólar ($) por cada unidad de Sol (S/.)
- Proceso automático ejecutado a las 00:00 hrs (medianoche)
- En caso de error en la consulta, el sistema debe:
  - Reintentar la consulta cada hora hasta obtener respuesta
  - Notificar al Superadministrador si no se obtiene respuesta en 24 horas
  - Utilizar el último tipo de cambio registrado hasta obtener actualización

**Campos del Registro:**
- **Fecha**: Fecha del tipo de cambio (automático)
- **Tipo de Cambio Compra**: Valor de compra del dólar (automático desde SUNAT)
- **Tipo de Cambio Venta**: Valor de venta del dólar (automático desde SUNAT)
- **Fuente**: SUNAT (automático)
- **Fecha y Hora de Actualización**: Timestamp de la última actualización (automático)
- **Estado**: Activo / Inactivo

#### 10.1.2. Consulta Manual del Tipo de Cambio

**Permisos:**
- Solo el **Superadministrador** puede ejecutar consulta manual

**Funcionalidad:**
- Botón "Consultar SUNAT" disponible en la pantalla de configuración
- Al presionar, el sistema consulta inmediatamente el tipo de cambio actual
- El sistema actualiza la tabla con el nuevo valor
- Se registra en auditoría la consulta manual (usuario, fecha, hora)

#### 10.1.3. Historial de Tipos de Cambio

**Registro Histórico:**
- El sistema debe mantener historial completo de todos los tipos de cambio
- No se pueden eliminar registros históricos
- Se debe poder consultar el tipo de cambio de cualquier fecha pasada
- Útil para auditorías y recálculos

**Campos de Búsqueda:**
- Búsqueda por fecha (rango)
- Búsqueda por mes/año
- Exportación del historial a Excel

#### 10.1.4. Aplicación del Tipo de Cambio en el Sistema

**Uso Transversal:**
- El tipo de cambio se utiliza en todos los módulos que manejan valores monetarios:
  - Gestión de Equipos (precio con IGV)
  - Gestión de Herramientas (precio con IGV)
  - Gestión de Contratos (costos, FEE, totales)
  - Cotizaciones
  - Órdenes de Servicio
  - Reportes financieros

**Reglas de Aplicación:**
- Para conversiones de Soles a Dólares: se usa el **Tipo de Cambio Venta**
- Para conversiones de Dólares a Soles: se usa el **Tipo de Cambio Compra**
- El tipo de cambio usado en una transacción queda registrado en el documento
- Los documentos mantienen el tipo de cambio del día de su creación

#### 10.1.5. Validaciones y Alertas

**Validaciones:**
- El tipo de cambio debe ser un valor numérico positivo mayor a cero
- Compra debe ser menor o igual a Venta
- El sistema debe validar variaciones extremas (ej: más de 10% de diferencia con el día anterior)

**Alertas:**
- Si el tipo de cambio varía más del 5% respecto al día anterior, notificar a:
  - Gerente de FM
  - Gerente General
- Si no se actualiza por más de 48 horas, notificar a Superadministrador

### 10.2. Gestión de IGV (Impuesto General a las Ventas)

**Propósito**: Centralizar la configuración del porcentaje de IGV aplicable a todas las transacciones del sistema, permitiendo su actualización cuando existan cambios en la legislación tributaria.

#### 10.2.1. Configuración del IGV

**Parámetros:**
- **Porcentaje de IGV**: Campo numérico decimal
- **Valor por Defecto**: 18% (0.18)
- **Fecha de Vigencia**: Fecha desde la cual aplica el porcentaje
- **Estado**: Activo / Inactivo
- **Observaciones**: Campo de texto libre para justificar cambios

**Permisos de Edición:**
- Solo editable por el rol **Gerente de FM**
- El Superadministrador puede ver pero no editar (para mantener trazabilidad)

#### 10.2.2. Proceso de Modificación del IGV

**Flujo de Cambio:**
1. El **Gerente de FM** accede al módulo de Datos Maestros
2. Selecciona la opción "Modificar IGV"
3. El sistema muestra el valor actual y solicita:
   - Nuevo porcentaje de IGV
   - Fecha de vigencia del cambio
   - Observaciones (obligatorio)

**Importante:**
- El cambio de IGV NO afecta documentos ya creados
- Los documentos nuevos utilizarán el IGV vigente a su fecha de creación
- Se mantiene historial completo de cambios de IGV


#### 10.2.4. Aplicación del IGV en el Sistema

**Uso Transversal:**
- El IGV se aplica automáticamente en:
  - Gestión de Equipos (cálculo de precio con IGV)
  - Gestión de Herramientas (cálculo de precio con IGV)
  - Gestión de Contratos (cotizaciones, totales)
  - Órdenes de Servicio
  - Facturación
  - Reportes financieros

**Fórmulas de Cálculo:**
- **IGV = Monto Base × Porcentaje IGV**
- **Total con IGV = Monto Base + IGV**
- **Monto Base desde Total = Total con IGV / (1 + Porcentaje IGV)**

**Reglas de Aplicación:**
- El IGV se calcula automáticamente en todos los campos de precio
- El usuario ve tanto el precio sin IGV como el precio con IGV
- El IGV usado en una transacción queda registrado en el documento
- Los documentos mantienen el IGV vigente al momento de su creación
:

**Posibles Adiciones Futuras:**
- Catálogo de Departamentos/Provincias/Distritos
- Catálogo de Países
- Catálogo de Zonas Geográficas
- Días festivos y no laborables
- Horarios de operación
- Tarifas y costos estándar
- Categorías de equipos y subcategorías
- Tipos de mantenimiento
- Plantillas de documentos
- Configuración de firma electrónica
