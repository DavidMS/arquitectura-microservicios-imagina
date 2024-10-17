# Ejercicio: Creación de un Microservicio desde Cero con Arquitectura Hexagonal en un Contexto de Ecommerce

En este ejercicio, desarrollarás un microservicio desde cero utilizando **Spring Boot** y aplicando los principios de la **Arquitectura Hexagonal**. El objetivo será construir un microservicio que gestione el inventario de productos de un ecommerce, permitiendo actualizar las existencias de productos.

## Requisitos

### 1. Domain Object (Producto)
Cada producto debe tener los siguientes atributos:
- `id` (Identificador único, autogenerado)
- `name` (Nombre del producto, cadena de texto)
- `stock` (Cantidad disponible en el inventario, entero positivo)
- `price` (Precio del producto, número decimal)

### 2. Agregado (Producto como Agregado Raíz)
- El **Producto** será el agregado raíz del sistema.
- Reglas de negocio a implementar:
    - No se puede actualizar el stock a un valor negativo.
    - El precio debe ser mayor a cero.

### 3. Caso de Uso (Actualizar Inventario)
Implementa un caso de uso que permita:
- Actualizar el stock de un producto existente.
- Validar las reglas de negocio antes de persistir cualquier cambio.

### 4. Infraestructura
- Utiliza una base de datos **H2 en memoria** para almacenar los productos.
- Proporciona un script SQL que cargue algunos productos iniciales al iniciar la aplicación.

### 5. Puertos y Adaptadores
- Implementa los **puertos de entrada** (interfaces de casos de uso) y los **puertos de salida** (repositorios) en la arquitectura hexagonal.
- Proporciona un **adaptador web** mediante un controlador REST que exponga los siguientes endpoints:
    - `GET /products` - Listar todos los productos.
    - `PUT /products/{id}/stock` - Actualizar el stock de un producto.

### 6. Script SQL Inicial (base de datos H2)
```sql
INSERT INTO product (id, name, stock, price) VALUES (1, 'Laptop', 50, 1200.00);
INSERT INTO product (id, name, stock, price) VALUES (2, 'Headphones', 200, 150.00);
INSERT INTO product (id, name, stock, price) VALUES (3, 'Keyboard', 100, 75.00);
