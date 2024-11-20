---
status: "proposed"  
date: 2024-11-16  
decision-makers: ["Lujan Maximiliano - ASS", "Ciano Ignacio - ASJ", "Lujan Nicolas - ASC"]  
---

# Decisión sobre la Tecnología de la Base de Datos  

## Context and Problem Statement  

El sistema actual enfrenta limitaciones en la escalabilidad debido a su dependencia de dos bases de datos SQL para toda la información. Es necesario seleccionar una tecnología de base de datos que soporte un aumento en la cantidad de usuarios y datos, garantizando al mismo tiempo la integridad y la seguridad.  

## Decision Drivers  

* Manejo eficiente de datos estructurados y semi-estructurados.  
* Necesidad de una solución confiable y bien documentada.  
* Compatibilidad con la tecnología del backend seleccionado.  

## Considered Options  

* Opción 1: Usar MySQL para manejar datos estructurados como clientes y pagos.  
* Opción 2: Usar MongoDB para manejar datos semi-estructurados, ideal para esquemas dinámicos o datos menos críticos.  
* Opción 3: Usar una combinación de MySQL y MongoDB, asignando cada tecnología según el tipo de datos.  

## Decision Outcome  

Chosen option: Usar MySQL como motor de base de datos. 

**Rationale:**  
MySQL es confiable, bien documentado y excelente para manejar datos estructurados y críticos. Se adapta perfectamente a los requerimientos de servicios como clientes y pagos, asegurando consistencia y transacciones seguras.  

### Consequences  

* Good: MySQL ofrece soporte avanzado para transacciones y consistencia en datos críticos.  
* Good: Equipo familiarizado con la tecnología, reduciendo la curva de aprendizaje.  
* Bad: Menos flexible para datos semi-estructurados, lo que puede requerir ajustes adicionales en el diseño de esquemas.  

### Confirmation  

Se validará la elección mediante pruebas de rendimiento y escalabilidad para garantizar que MySQL cumpla con las demandas del sistema bajo escenarios de alta carga.  

## Pros and Cons of the Options  

### Opción 1: Usar MySQL  

* Good: Transacciones seguras y manejo de datos críticos.  
* Good: Amplia documentación y soporte comunitario.  
* Bad: Menos adecuado para datos semi-estructurados.  

### Opción 2: Usar MongoDB  

* Good: Ideal para datos semi-estructurados o esquemas dinámicos.  
* Bad: Limitaciones en la gestión de transacciones complejas.  
* Bad: Equipo menos familiarizado con la tecnología.  

### Opción 3: Usar una combinación de MySQL y MongoDB  

* Good: Balance entre datos estructurados y semi-estructurados.  
* Bad: Mayor complejidad operativa y necesidad de gestionar dos sistemas diferentes.  

## More Information  

Las pruebas incluirán operaciones CRUD intensivas y simulaciones de carga para evaluar el desempeño y la escalabilidad de MySQL en escenarios reales.
