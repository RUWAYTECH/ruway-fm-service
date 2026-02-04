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
