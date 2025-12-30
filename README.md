
---

## 🧪 Challenge Técnico — CRUD de Productos con Tallas

Este repositorio contiene un **challenge técnico** para evaluar el desarrollo de una **API REST en NestJS**, el correcto uso de HTTP y buenas prácticas de desarrollo backend.

---

## 🎯 Objetivo

Construir una **API REST** que permita gestionar **productos**, donde cada producto puede tener **múltiples tallas (variantes)**.

Los datos deben persistirse en un **archivo JSON local dentro del proyecto**.  
❌ No se permite usar bases de datos.

---

## 📦 Modelo de Datos

### Producto
```json
{
  "codigo": "SKU-123",
  "nombre": "Polera Básica",
  "variantes": [
    {
      "talla": "M",
      "precio": 19990,
      "cantidadDisponibles": 20,
      "coloresDisponibles": ["rojo", "negro"]
    },
    {
      "talla": "L",
      "precio": 20990,
      "cantidadDisponibles": 10,
      "coloresDisponibles": ["negro"]
    }
  ]
}
```

### Reglas
- `codigo` es **único**
- Un producto puede tener **múltiples tallas**
- No se puede repetir la misma `talla` dentro del mismo producto
- Todos los campos son obligatorios

---

## 🚀 Endpoints Obligatorios

### Crear producto con su primera talla
**POST** `/products`

Crea un producto nuevo con una variante inicial.

**Status**
- `201 Created`
- `409 Conflict` si el `codigo` ya existe
- `400 Bad Request` si hay error de validación

---

### Obtener productos
**GET** `/products`

Retorna todos los productos con sus variantes.

**Status**
- `200 OK`

---

### Obtener productos por talla
**GET** `/products/size/:talla`

Retorna todos los productos que tengan al menos una variante con la talla indicada.

**Status**
- `200 OK`

---

## 🚀 Endpoints Deseables

### Obtener productos por color
**GET** `/products/color/:color`

Retorna productos que tengan al menos una variante con el color indicado.

---

### Agregar una talla a un producto
**POST** `/products/:codigo/variants`

Agrega una nueva variante (talla) a un producto existente.

**Status**
- `201 Created`
- `404 Not Found` si el producto no existe
- `409 Conflict` si la talla ya existe

---

### Actualizar una talla
**PUT** `/products/:codigo/variants/:talla`

Actualiza los datos de una variante específica.

**Status**
- `200 OK`
- `404 Not Found` si el producto o la talla no existen

---

### Eliminar una talla
**DELETE** `/products/:codigo/variants/:talla`

Elimina una variante específica.

**Status**
- `204 No Content`
- `404 Not Found` si no existe

---

## 💾 Persistencia

- Los datos deben almacenarse en un archivo JSON local:
  ```
  /data/products.json
  ```
- El archivo debe crearse automáticamente si no existe
- Se permite usar el módulo `fs` de Node.js

---

## 📦 Entrega

- Crear una rama con la solución
- Subir los cambios
- Abrir un **Pull Request**
- Incluir en el PR:
  - Breve explicación de la solución
  - Pasos para levantar el proyecto

---

## 🧠 Evaluación

- Correcto uso de NestJS
- Uso correcto de métodos HTTP y status codes
- Persistencia correcta en JSON
- Validaciones y manejo de errores
- Código claro y ordenado

---

## Project setup

```bash
$ npm install
```

## Compile and run the project

```bash
# development
$ npm run start

# watch mode
$ npm run start:dev

# production mode
$ npm run start:prod
```

## Run tests

```bash
# unit tests
$ npm run test
```

## License

Nest is [MIT licensed](https://github.com/nestjs/nest/blob/master/LICENSE).
