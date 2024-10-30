código WSD de caso de uso
------------------------------------------
-@startuml  
actor Usuario  
-actor Administrador  
rectangle "carrito de compras" as Carrito{  
usecase "Registrar Usuario" as UC1  
usecase "Iniciar Sesión" as UC2  
usecase "Agregar Producto" as UC3  
usecase "Actualizar Stock" as UC4  
usecase "Generar Factura" as UC5  
usecase "Consultar Inventario" as UC6  
}

--Usuario --> UC1  
--Usuario --> UC2  
Usuario --> UC5  
-Usuario --> UC6  
-Administrador --> UC3  
-Administrador --> UC4

@enduml
----------------------------------------

**diagrama** 


![caso-uso](c:\Users\USUARIO\Desktop\uml\dinamico\caso-de-uso\@startuml\@startuml.png)

------------------------------------------------------------

explicacion   
-este diagrama se basa en en el caso de uso con respecto a un carrito de compras, dondetenemos 2 actores que son el usuario y el administrador y unas cuantas entidades que tienen acceso ambos actores dentro de una base de datos llamada carrito. 
