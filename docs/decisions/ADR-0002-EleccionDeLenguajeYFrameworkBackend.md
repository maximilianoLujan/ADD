---
status: "proposed"  
date: 2024-11-16  
decision-makers: ["Lujan Maximiliano - ASS", "Ciano Ignacio - ASJ", "Lujan Nicolas - ASC"]  
---

# Decisión sobre el Lenguaje y Framework para el Backend  

## Context and Problem Statement  

El sistema requiere una tecnología robusta para implementar la lógica de negocio y exponer servicios RESTful. Es necesario elegir un lenguaje y framework que facilite la escalabilidad, seguridad y el desarrollo independiente de los módulos críticos, garantizando la confiabilidad de las operaciones y la protección de los datos.  

## Decision Drivers  

* El lenguaje debe ser seguro y confiable, especialmente para manejar servicios críticos como pagos y clientes.  
* Escalabilidad y soporte para microservicios.  
* Familiaridad del equipo de desarrollo con las herramientas seleccionadas para optimizar el proceso.  

## Considered Options  

*Opción 1: Usar Spring Boot con Java, un lenguaje tipado fuertemente conocido por su robustez y seguridad.  
*Opción 2: Usar Express.js con JavaScript, un lenguaje dinámico y más flexible, pero menos seguro. 
*Opción 3: Usar NestJS con TypeScript, un lenguaje que combina flexibilidad y seguridad con tipos estáticos.

## Decision Outcome  

Chosen option: Usar Spring Boot con Java.

**Rationale:**  
Spring Boot ofrece un ecosistema completo para construir APIs RESTful y microservicios. Java, al ser un lenguaje fuertemente tipado, asegura la robustez de los datos y facilita la escalabilidad. Además, el equipo de desarrollo tiene experiencia previa con estas tecnologías, reduciendo la curva de aprendizaje.  

### Consequences  

* Good: Integración avanzada con microservicios y APIs RESTful en el ecosistema Spring.  
* Good: La robustez de Java mejora la seguridad en servicios críticos como pagos.  
* Good: Familiaridad del equipo con estas tecnologías garantiza un desarrollo eficiente.  
* Bad: Menos flexible que un lenguaje no tipado como JavaScript.  

### Confirmation  

La elección será validada mediante pruebas unitarias y de integración en un entorno controlado, verificando la robustez del manejo de datos y el rendimiento del framework en escenarios reales.  

## Pros and Cons of the Options  

### Opción 1: Usar Spring Boot con Java  

* Good: Ecosistema robusto para construir microservicios.  
* Good: Lenguaje seguro y confiable, ideal para servicios críticos.  
* Good: Equipo familiarizado con las herramientas.  
* Bad: Mayor rigidez comparado con lenguajes dinámicos.  

### Opción 2: Usar Express.js con JavaScript  

* Good: Mayor flexibilidad en la estructura de los datos.  
* Bad: Menor seguridad, ya que JavaScript es un lenguaje no tipado.  
* Bad: Solo una persona del equipo tiene experiencia con esta tecnología.  

### Opción 3: Usar NestJS con TypeScript
* Good: Ofrece las ventajas de un lenguaje tipado, como la detección temprana de errores y un mejor soporte para la mantenibilidad del código.
* Bad: Frameworks como NestJS pueden requerir tiempo para dominarlos.
* Bad: NestJS y su ecosistema no cuentan con la misma solidez y antigüedad que Spring en escenarios empresariales.

## More Information  

Se evaluará la implementación inicial con **Spring Test** para garantizar que los servicios cumplan con los requerimientos de calidad.
