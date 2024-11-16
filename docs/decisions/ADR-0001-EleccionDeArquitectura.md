---
status: "accepted"
date: 2024-11-12
decision-makers: ["Lujan Maximiliano - ASS", "Ciano Ignacio - ASJ", "Lujan Nicolas - ASC"]
---

# Decisión sobre la Arquitectura para la Migración a Microservicios

## Context and Problem Statement

La compañía de productos alimenticios necesita migrar su sistema monolítico a una arquitectura de microservicios para mejorar la flexibilidad y escalabilidad del sistema. La nueva arquitectura debe facilitar el acceso de clientes de escritorio y móvil mediante protocolos HTTP/REST y manejar módulos críticos como clientes, pedidos, reparto y pagos. La migración debe realizarse de manera que se mantenga la confiabilidad y la seguridad de los datos, al tiempo que se minimizan las interrupciones.

## Decision Drivers

* Necesidad de una arquitectura escalable para soportar picos de carga.
* Flexibilidad para permitir desarrollos independientes de cada módulo funcional.
* Capacidad de desacoplamiento de módulos críticos, permitiendo una evolución y mantenimiento sin afectar a todo el sistema.
* Control de seguridad centralizado en los servicios críticos.
* Interoperabilidad entre componentes para soportar clientes de escritorio y móvil.

## Considered Options

* Opción 1: Implementar una arquitectura basada en microservicios con una capa de API Gateway y comunicación RESTful entre los microservicios.
* Opción 2: Mantener la arquitectura monolítica pero modularizar la lógica de negocio en diferentes capas de servicio.
* Opción 3: Adoptar una arquitectura híbrida donde los módulos críticos se desplieguen como microservicios, manteniendo otros módulos en el sistema monolítico.

## Decision Outcome

Chosen option: "Opción 1: Arquitectura de microservicios con API Gateway y comunicación RESTful", porque permite escalabilidad y desacoplamiento, satisfaciendo los requerimientos de flexibilidad y evolución independiente de los módulos.

### Consequences

* Good, porque la arquitectura modular mejora la escalabilidad al permitir que cada servicio crítico (Clientes, Pedidos, Reparto, Pagos) se despliegue y escale independientemente.
* Good, porque incrementa la mantenibilidad y facilita futuras modificaciones, ya que los equipos pueden trabajar en módulos individuales sin afectar el sistema completo.
* Good, porque el uso de API Gateway permite un control centralizado de la seguridad y autenticación, protegiendo los datos de los clientes y los pagos.
* Bad, porque es complejo de implementar comparado con un sistema monolítico.
* Bad, porque puede incrementar la complejidad operativa, ya que gestionar microservicios, registros y monitoreo requiere herramientas adicionales y una infraestructura más compleja.
* Bad, porque la comunicación a través de redes entre servicios puede introducir latencias, especialmente si no se optimizan adecuadamente los puntos de interacción entre microservicios.

### Confirmation

La implementación de esta arquitectura será revisada a través de un proceso de validación que incluirá pruebas de carga para evaluar la escalabilidad, además de revisiones de seguridad sobre los servicios críticos. Se planificarán revisiones de diseño y código para asegurar que el desacoplamiento de los microservicios cumpla con el modelo de arquitectura decidido.

## Pros and Cons of the Options

### Opción 1: Arquitectura de microservicios con API Gateway y comunicación RESTful

* Good, porque facilita la escalabilidad horizontal, permitiendo distribuir la carga y soportar un mayor número de transacciones.
* Good, porque el desacoplamiento entre servicios facilita el desarrollo, implementación y pruebas individuales de cada módulo.
* Good, porque mejora la resiliencia; fallos en un microservicio específico no afectan a los demás, mejorando la confiabilidad general del sistema.
* Neutral, porque la implementación de una infraestructura de monitoreo robusta puede mitigar la complejidad añadida.
* Bad, porque la configuración inicial y el mantenimiento continuo de los microservicios puede requerir herramientas y recursos adicionales.
* Bad, porque la comunicación entre servicios puede introducir latencias que deben ser gestionadas cuidadosamente.

### Opción 2: Mantener la arquitectura monolítica con modularización de la lógica de negocio

* Good, porque es menos costoso y requiere menos cambios en la infraestructura actual.
* Good, porque permite cambios rápidos en la lógica de negocio sin una alta complejidad de gestión.
* Bad, porque limita la escalabilidad y dificulta los despliegues independientes de módulos específicos.
* Bad, porque, aunque modularizada, sigue teniendo un nivel de acoplamiento alto, afectando la flexibilidad para realizar actualizaciones sin interrumpir el servicio.

### Opción 3: Arquitectura híbrida, con microservicios solo para módulos críticos

* Good, porque permite un equilibrio entre desacoplamiento y simplicidad, separando solo los módulos más importantes.
* Good, porque reduce la complejidad operativa, ya que solo los módulos críticos requieren gestión como microservicios.
* Neutral, porque puede ser una solución intermedia válida en cuanto a esfuerzo e impacto.
* Bad, porque puede generar redundancia de esfuerzos, ya que el sistema monolítico y los microservicios requerirían gestión separada.
* Bad, porque los módulos híbridos podrían no lograr el mismo nivel de flexibilidad que en una arquitectura completamente desacoplada.

## More Information

Este documento de decisión arquitectónica puede ser revisado tras la primera iteración de desarrollo de microservicios. La arquitectura elegida también se alineará con el monitoreo y gestión que los equipos de DevOps puedan establecer en la infraestructura. En caso de cambios en los requisitos de escalabilidad o seguridad, este documento puede ser actualizado. 

