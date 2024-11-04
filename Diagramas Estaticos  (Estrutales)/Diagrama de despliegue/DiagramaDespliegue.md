# Documentación del Diagrama de Despliegue para el Sistema de Carrito de Compras

El proyecto del sistema de carrito de compras consiste en desarrollar una base de datos con roles de administrador y comprador, donde se realizarán consultas SQL entre varias entidades. Este documento describe la distribución física de los nodos y artefactos que se ejecutan en el sistema.

---

## Diagrama de Despliegue

```plantuml
@startuml
@startuml
node "Cliente (Navegador)" {
  [Interfaz Angular]
}

node "Servidor Web" {
  [API de Autenticación] as AuthAPI
  [API de Carrito de Compras] as CartAPI
  [API de Facturación] as BillingAPI

  AuthAPI --> CartAPI : "Envía información de usuario"
  CartAPI --> BillingAPI : "Envía datos del carrito"

  [Interfaz Angular] --> AuthAPI : "Autenticación de usuarios"
  [Interfaz Angular] --> CartAPI : "Operaciones CRUD del carrito"
  [Interfaz Angular] --> BillingAPI : "Consulta de facturas"

  CartAPI --> "Servidor de Base de Datos" : "Consultas SQL (JOINs)"
  BillingAPI --> "Servidor de Base de Datos" : "Consultas SQL (JOINs)"
}

node "Servidor de Base de Datos" {
  [MySQL]
}

AuthAPI --> [MySQL] : "Consulta de autenticación"
CartAPI --> [MySQL] : "Consulta y actualización de inventario"
BillingAPI --> [MySQL] : "Generación y almacenamiento de facturas"
@enduml
```
## Imagen de referncia
![Diagrama de Despliegue](diagramaDespliegue.png)