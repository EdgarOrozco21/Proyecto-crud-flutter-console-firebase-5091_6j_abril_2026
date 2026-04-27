Va, te dejo un ejemplo bien armado como si fuera una empresa tipo la que quieres (*Financorp* 👀), usando **MongoDB** (porque hablas de colecciones y documentos).

---

# 🏦 Base de datos: `financorp_db`

Esta base de datos va a tener varias **colecciones** clave:

* clientes
* cuentas
* transacciones
* empleados
* inversiones

---

# 📁 Colección: `clientes`

Cada documento representa un cliente.

### 📄 Ejemplo de documento:

```json
{
  "_id": ObjectId("661f1a2b3c4d5e6f789001"),
  "nombre": "Edgar Orozco",
  "correo": "edgar@gmail.com",
  "telefono": "6561234567",
  "direccion": {
    "calle": "Av. Tecnológico",
    "ciudad": "Ciudad Juárez",
    "estado": "Chihuahua",
    "cp": "32500"
  },
  "fecha_registro": ISODate("2026-04-27"),
  "activo": true
}
```

### 🧠 Tipos de datos:

* `_id`: ObjectId
* `nombre`: String
* `correo`: String
* `telefono`: String
* `direccion`: Object
* `fecha_registro`: Date
* `activo`: Boolean

---

# 💳 Colección: `cuentas`

Relacionada con clientes.

### 📄 Ejemplo:

```json
{
  "_id": ObjectId("661f1a2b3c4d5e6f789002"),
  "id_cliente": ObjectId("661f1a2b3c4d5e6f789001"),
  "tipo_cuenta": "ahorro",
  "saldo": 15000.50,
  "moneda": "MXN",
  "fecha_apertura": ISODate("2026-01-15")
}
```

### 🧠 Tipos:

* `id_cliente`: ObjectId (relación)
* `tipo_cuenta`: String
* `saldo`: Double
* `moneda`: String
* `fecha_apertura`: Date

---

# 💸 Colección: `transacciones`

Aquí se guarda TODO el movimiento del dinero.

### 📄 Ejemplo:

```json
{
  "_id": ObjectId("661f1a2b3c4d5e6f789003"),
  "id_cuenta": ObjectId("661f1a2b3c4d5e6f789002"),
  "tipo": "deposito",
  "monto": 5000,
  "fecha": ISODate("2026-04-20"),
  "descripcion": "Depósito inicial"
}
```

### 🧠 Tipos:

* `id_cuenta`: ObjectId
* `tipo`: String (deposito, retiro, transferencia)
* `monto`: Number
* `fecha`: Date
* `descripcion`: String

---

# 👨‍💼 Colección: `empleados`

Para manejar el personal.

### 📄 Ejemplo:

```json
{
  "_id": ObjectId("661f1a2b3c4d5e6f789004"),
  "nombre": "Alex Ramírez",
  "puesto": "Asesor Financiero",
  "salario": 12000,
  "correo": "alex@financorp.com",
  "telefono": "6569876543",
  "fecha_contratacion": ISODate("2025-08-10")
}
```

### 🧠 Tipos:

* `nombre`: String
* `puesto`: String
* `salario`: Number
* `correo`: String
* `telefono`: String
* `fecha_contratacion`: Date

---

# 📈 Colección: `inversiones`

Para manejar inversiones de clientes.

### 📄 Ejemplo:

```json
{
  "_id": ObjectId("661f1a2b3c4d5e6f789005"),
  "id_cliente": ObjectId("661f1a2b3c4d5e6f789001"),
  "tipo_inversion": "bienes_raices",
  "monto_invertido": 50000,
  "rendimiento": 8.5,
  "fecha_inicio": ISODate("2026-02-01"),
  "plazo_meses": 12
}
```

### 🧠 Tipos:

* `id_cliente`: ObjectId
* `tipo_inversion`: String
* `monto_invertido`: Number
* `rendimiento`: Number (%)
* `fecha_inicio`: Date
* `plazo_meses`: Number

---

# 🔗 Relación entre colecciones (clave para tu proyecto)

* `clientes` → `cuentas` (1 a muchos)
* `cuentas` → `transacciones` (1 a muchos)
* `clientes` → `inversiones` (1 a muchos)

---

# 🚀 Ejemplo de creación en MongoDB

```js
use financorp_db

db.clientes.insertOne({
  nombre: "Edgar Orozco",
  correo: "edgar@gmail.com",
  telefono: "6561234567",
  fecha_registro: new Date(),
  activo: true
})
```

---

# 💡 Tip pro (para que saques 10)

* Usa **subdocumentos** (como dirección) → se ve más profesional
* Usa **ObjectId para relaciones** → como base de datos real
* Evita `null` → mejor datos inventados (como te piden en tu clase)
* Mantén consistencia en nombres (`id_cliente`, `id_cuenta`, etc.)

---

Si quieres, en el siguiente paso te hago:
✅ Inserts completos (como 10 registros por colección)
✅ Consultas tipo examen (find, aggregate, joins con `$lookup`)
✅ O te lo adapto EXACTO a lo que te pide tu profe 👀
