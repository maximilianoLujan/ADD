---
status: "proposed"
date: 2024-11-16
decision-makers: ["Lujan Maximiliano - ASS", "Ciano Ignacio - ASJ", "Lujan Nicolas - ASC"]
---

# Decisión sobre las tecnologias a utilizar

## Context and Problem Statement

La escalabilidad del sistema actual es ineficiente ya que no puede manejar eficientemente un aumento en la cantidad de usuarios, pedidos o datos generados. Esto debido a que toda la informacion se encuentra distribuida en unicamente dos bases de datos SQL. El desafio es encontrar tecnologias eficientes y actualizadas para satisfacer las demandas del sistema.

## Decision Drivers

* Los servicios críticos (clientes, pagos, rutas) deben estar disponibles con un tiempo de respuesta cercano a cero.
* Facilitar el desarrollo independiente y la gestión de servicios.
* Es crucial garantizar la confidencialidad y protección de los datos personales de los usuarios (por ejemplo, cuentas de clientes o información de pago). Esto incluye la encriptación de datos en tránsito y en reposo para prevenir accesos no autorizados.

## Considered Options

* Opción 1: Usar Springboot (los modulos de spring web, security, spring framework) para el backend y un motor MySQL para la persistencia de datos.
* Opción 2: Usar Springboot (los modulos de spring web, security, spring framework para el backed) y mongoDB para la persistencia de datos.
* Opción 3: Usar express con javascript para el backend y utilizar mongoDB para almacenar informacion que no necesita estar estructurada y mysql para informacion sensible.

## Decision Outcome

Chosen option: "Opción 1: Usar Springboot (los modulos de spring web, security, spring framework) para el backend y un motor MySQL para la persistencia de datos.", porque java es un lenguaje fuertemenete tipado lo que asegura la robustez de los datos haciendo nuetra aplicacion mas segura. Ademas, por otro lado, mysql es confiable y esta bien documentado (asi como spring) ideal para manejar datos estructurados.

### Consequences

* Good: Escalabilidad y soporte para microservicios con integración avanzada en el ecosistema Java.
* Good: MySQL es confiable y bien documentado, ideal para manejar datos estructurados.
* Good: El equipo de desarrollo conoce y tiene experiencia en dichas tecnologias.
* Bad: Al ser un lenguaje tipado no es tan flexible como un lenguaje no tipado.

### Confirmation

* Pruebas de seguridad: Se realizarán pruebas automatizadas para validar que los datos no se pierden ni se corrompen durante el procesamiento, transmisión o almacenamiento.
* Se utilizará la tactica ping/echo para determinar si el sistema esta disponible y de cuanto es el tiempo de respuesta.

## Pros and Cons of the Options

### Opción 1: Usar Springboot (los modulos de spring web, security, spring framework) para el backend y un motor MySQL para la persistencia de datos

* Good: Escalabilidad y soporte para microservicios con integración avanzada en el ecosistema Java.
* Good: MySQL es confiable y bien documentado, ideal para manejar datos estructurados.
* Good: El equipo de desarrollo conoce y tiene experiencia en dichas tecnologias.
* Bad: Al ser un lenguaje tipado no es tan flexible como un lenguaje no tipado.

### Opción 2: Usar Springboot (los modulos de spring web, security, spring framework para el backed) y mongoDB para la persistencia de datos

* Good, porque Spring Boot simplifica la creación de microservicios y APIs REST con herramientas preconfiguradas y soporte para MongoDB mediante Spring Data.
* Good, porque MongoDB permite manejar datos semi-estructurados, lo que es ideal para sistemas con esquemas dinámicos o cambiantes.
* Bad, porque MongoDB no es ideal para manejar relaciones entre datos, lo que puede resultar en duplicación o inconsistencias.

### Opción 3: Usar express con javascript para el backend y utilizar mongoDB para almacenar informacion que no necesita estar estructurada y mysql para informacion sensible

* Good, variar entre bases de datos NoSql y Sql nos permite usar mysql en datos que necesitamos acceder constantemente y que la informacion este estructurada y mongoDb para almacenar datos que no siguen una estructura determinada.
* Neutral, javascript al ser un lenguaje no tipado, es mas flexible en la estructura de los datos pero mucho mas inseguro que un lenguaje tipado.
* Bad, porque solo una persona del equipo de desarrollo tiene experiencia y conocimiento en el lenguaje.

## More Information

Se va a aprovechar el uso de Spring para implementar tests con 'Spring Test'.