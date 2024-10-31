# Proyecto de Base de Datos para Carrito de Compras

## Descripción del Proyecto
Este proyecto tiene como objetivo desarrollar un sistema de carrito de compras en el que se manejen dos roles: **Administrador** y **Comprador**. La base de datos debe incluir consultas SQL usando `JOIN` entre las siguientes entidades:

- **Usuario**
- **Producto**
- **Inventario**
- **Factura**
- **Detalle Factura**

## Diagrama de Objetos

### ¿Qué es un Diagrama de Objetos?
Un Diagrama de Objetos representa un instante específico de como se relacionan las clases en un momento dado. En este caso, muestra ejemplos de cómo un **Usuario** (como cliente) realiza una compra de **Productos**, generando una **Factura** y actualizando el **Inventario**.

### Ejemplo de Diagrama de Objetos en PlantUML

```plantuml
@startuml
object Usuario {
  id: 1
  nombre: "Juan Pérez"
  rol: "Comprador"
}

object Producto1 {
  id: 101
  nombre: "Laptop"
  precio: 1200.00
  stock: 5
}

object Producto2 {
  id: 102
  nombre: "Mouse"
  precio: 20.00
  stock: 15
}

object Inventario {
  producto_id: 101
  stock_actual: 5
}

object Factura {
  id: 5001
  fecha: "2024-10-30"
  total: 1240.00
}

object DetalleFactura1 {
  factura_id: 5001
  producto_id: 101
  cantidad: 1
  subtotal: 1200.00
}

object DetalleFactura2 {
  factura_id: 5001
  producto_id: 102
  cantidad: 2
  subtotal: 40.00
}

Usuario --> Factura : "genera"
Factura --> DetalleFactura1 : "contiene"
Factura --> DetalleFactura2 : "contiene"
DetalleFactura1 --> Producto1 : "compra"
DetalleFactura2 --> Producto2 : "compra"
Producto1 --> Inventario : "actualiza stock"
Producto2 --> Inventario : "actualiza stock"
@enduml
```
## Imagen del diagrama

![Diagrama de Objeto](DiagramObjeto.png)
