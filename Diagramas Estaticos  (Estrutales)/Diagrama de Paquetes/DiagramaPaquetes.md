# Documentación del Diagrama de Paquetes para el Sistema de Carrito de Compras

Este diagrama de paquetes organiza el sistema de carrito de compras en varios módulos o componentes, agrupándolos en paquetes de acuerdo con su funcionalidad en el sistema.

---

## Diagrama de Paquetes

```plantuml
@startuml
package "Carrito de Compras" {
    package "Control de Usuarios" {
        [Usuario]
        [Rol]
        [Autenticación] --> [Usuario] : "Autentica"
        [Usuario] --> [Rol] : "Tiene rol"
    }

    package "Gestión de Productos" {
        [Producto]
        [Inventario]
        [Producto] --> [Inventario] : "Relacionado con"
    }

    package "Gestión de Facturación" {
        [Factura]
        [Detalle_Factura]
        [Factura] --> [Detalle_Factura] : "Contiene"
    }

    package "Servicios API" {
        [API de Autenticación] as AuthAPI
        [API de Carrito] as CartAPI
        [API de Facturación] as BillingAPI
        
        AuthAPI --> [Control de Usuarios] : "Consulta roles y autenticación"
        CartAPI --> [Gestión de Productos] : "Consulta y gestiona productos"
        BillingAPI --> [Gestión de Facturación] : "Genera y gestiona facturas"
    }
}
@enduml
```
## Imagen de referncia
![Diagrama de Paquete](DiagramaPaquete.png)