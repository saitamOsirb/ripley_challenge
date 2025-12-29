# Challenge Técnico — NestJS CRUD de Productos

Hola 👋  
Gracias por tu interés en este challenge técnico.  
El objetivo de esta prueba es conocer cómo estructuras una API, cómo trabajas con NestJS y cómo tomas decisiones técnicas simples pero correctas.

No buscamos una solución perfecta, sino **clara, funcional y bien pensada**.

---

## 🎯 Objetivo

Construir una **API REST en NestJS** para gestionar **productos**, utilizando un **archivo JSON local** como almacenamiento de datos (no se debe usar base de datos).

La API debe permitir:
- Crear productos
- Obtener productos
- (Deseable) Modificar productos
- (Deseable) Eliminar productos

Usando correctamente los métodos HTTP **GET, POST, PUT y DELETE** junto con sus **status codes**.

---

## 📌 Reglas importantes

- ✅ Puedes buscar soluciones solo en **Google**
- ❌ Está **prohibido el uso de IA**
- ❌ No se permite usar bases de datos
- ✅ Los datos deben guardarse en un archivo JSON dentro del proyecto
- ✅ La entrega debe realizarse mediante un **Pull Request**

---

## 🧱 Modelo de Producto

Cada producto debe tener la siguiente estructura:

```json
{
  "codigo": "SKU-123",
  "nombre": "Polera Básica",
  "precio": 19990,
  "cantidadDisponibles": 20,
  "atributos": {
    "talla": "M",
    "coloresDisponibles": ["rojo", "negro"]
  }
}
```

### Reglas del modelo
- `codigo` es obligatorio y **único**
- Todos los campos son obligatorios
- `precio` y `cantidadDisponibles` deben ser valores numéricos válidos

---

## 🚀 Endpoints

### Crear producto (OBLIGATORIO)
**POST** `/products`

- Guarda el producto en el archivo JSON
- No debe permitir productos con el mismo `codigo`

**Status esperados**
- `201 Created` → producto creado correctamente
- `409 Conflict` → el código ya existe
- `400 Bad Request` → error de validación

---

### Obtener productos (OBLIGATORIO)
**GET** `/products`

- Retorna la lista de productos desde el JSON

**Status esperado**
- `200 OK`

---

### Obtener productos por talla (OBLIGATORIO)
**GET** `/products/size/:talla`

- Retorna todos los productos cuya `atributos.talla` coincida con el parámetro `talla`
- La búsqueda debe ser exacta (ej: `M`, `L`, `XL`)

**Status esperado**
- `200 OK`

---

### Obtener productos por color (DESEABLE)
**GET** `/products/color/:color`

- Retorna todos los productos que tengan el color indicado dentro de `atributos.coloresDisponibles`
- La búsqueda debe ser exacta (ej: `rojo`, `negro`)

**Status esperado**
- `200 OK`

---

### Actualizar producto (DESEABLE)
**PUT** `/products/:codigo`

- Permite modificar cualquier atributo del producto
- La búsqueda debe ser solo por `codigo`

**Status esperados**
- `200 OK`
- `404 Not Found` si el producto no existe

---

### Eliminar producto (DESEABLE)
**DELETE** `/products/:codigo`

- Elimina el producto usando el `codigo`

**Status esperados**
- `204 No Content`
- `404 Not Found` si no existe

---

## 💾 Persistencia

- Los productos deben guardarse en un archivo JSON dentro del proyecto  
  (por ejemplo: `data/products.json`)
- Puedes usar el módulo `fs` de Node.js para leer y escribir datos

---

## 🛠️ Levantar el proyecto desde cero

1. Instalar Nest CLI:
   ```
   npm i -g @nestjs/cli
   ```

2. Crear el proyecto:
   ```
   nest new products-api
   ```

3. Levantar el proyecto:
   ```
   npm run start:dev
   ```

---

## 📦 Entrega

1. Crea una rama con tu solución
2. Sube los cambios a tu repositorio
3. Abre un **Pull Request** hacia la rama principal
4. En el PR incluye:
   - Una breve explicación de tu solución
   - Pasos para ejecutar el proyecto

---

## 🧠 ¿Qué evaluamos?

- Uso correcto de NestJS (controllers, services, DTOs)
- Manejo de archivos JSON como persistencia
- Validaciones y manejo de errores
- Correcto uso de métodos HTTP y status codes
- Código limpio, ordenado y fácil de entender

---

Gracias por tu tiempo y ¡mucho éxito! 🚀
