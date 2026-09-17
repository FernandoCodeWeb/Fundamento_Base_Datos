# Diagrama Entidad-Relación: Conexión Desde el Usuario Hasta la Forma de Pago

## 📋 Descripción

Modelo Entidad-Relación para un sistema de gestión de colegiaturas y pagos. El diagrama traza el recorrido completo de datos desde el registro del usuario hasta el detalle de su forma de pago, incluyendo la clasificación por tipo de usuario, su ubicación, el registro de colegiatura por semestre y la especialización del método de pago (transferencia electrónica o depósito en efectivo).

## 🧩 Entidades principales

| Entidad | Llave primaria | Descripción |
|---|---|---|
| **Usuario** | id_Usuario | Alumno registrado en el sistema (nombre, apellidos, email, password). |
| **Tipo_Usuario** | id_tipoUsuario | Define el rol o permisos del usuario. |
| **Estado** | id_Estado | Entidad geográfica de residencia del usuario. |
| **Municipio** | id_Municipio | Subdivisión del Estado. |
| **Colegiatura** | id_Colegiatura | Registro del pago (fecha_Pago, cantidad, matricula), vinculado al usuario mediante id_Usuario como llave foránea. |
| **Semestre** | id_Semestre | Periodo académico al que corresponde la colegiatura. |
| **Forma_Pago** | id_FormaPago | Entidad generalizada del método de pago utilizado. |
| **Transferencia_Electronica** | id_FormaPago (heredada) | Especialización de Forma_Pago — SPEI_Rastreo, Banco_Origen. |
| **Deposito_Efectivo** | id_FormaPago (heredada) | Especialización de Forma_Pago — Numero_Folio, Numero_Comprobante. |

## 🔗 Recorrido del modelo

`Usuario` → **Tiene** → `Tipo_Usuario`
`Usuario` → **Vive en** → `Estado` → **Del** → `Municipio`
`Usuario` → **Paga** → `Colegiatura` → **Corresponde a** → `Semestre`
`Colegiatura` → **Utiliza** → `Forma_Pago` → **Es_Un** → `Transferencia_Electronica` | `Deposito_Efectivo`

La relación **Es_Un** representa una generalización-especialización: ambos subtipos de pago heredan `id_FormaPago` como llave primaria, manteniendo un rastreo completo y sin duplicar datos desde la identidad del alumno hasta el detalle de su transacción.

## 🛠️ Herramienta utilizada

**draw.io** — elaboración del diagrama Entidad-Relación.

## 📎 Contenido de esta carpeta

- `Practica_01.png` — diagrama Entidad-Relación completo.
- `Usuario_Hasta_la_Forma_de_Pago.pdf` — documento con el desarrollo escrito y la justificación técnica del diseño (llaves foráneas, relaciones y su propósito).

## 👤 Datos del entregable

- **Alumno:** Fernando Ivan Barrios Espinosa
- **Profesor:** Chávez Gómez José Luis
- **Grupo:** SCO4MA116
- **Materia:** Fundamentos de Base de Datos
