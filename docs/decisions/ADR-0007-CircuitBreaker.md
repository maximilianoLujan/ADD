---
status: "accepted"
date: 2024-11-26
decision-makers: ["Lujan Maximiliano - ASS", "Ciano Ignacio - ASJ", "Lujan Nicolas - ASC"]
---

# Implementación del patrón Circuit Breaker en la comunicación entre microservicios críticos

## Context and Problem Statement

En la arquitectura basada en microservicios, la comunicación entre servicios es esencial. Sin embargo, el microservicio de pagos tiene interacciones críticas con sistemas externos y entre ellos. Estos sistemas externos y microservicios pueden experimentar fallos, lo que podría comprometer la estabilidad de todo el sistema.

Para evitar que un fallo en un servicio crítico genere un efecto en cascada que impacte en otros microservicios, es necesario implementar un mecanismo que permita identificar y manejar estos fallos de manera controlada.

## Decision Drivers

* Tolerancia a fallos: Asegurar que los fallos en un servicio no afecten a otros componentes del sistema.
* Disponibilidad: Mantener la funcionalidad del sistema incluso cuando ciertos servicios están inactivos o sobrecargados.
* Rendimiento: Reducir los tiempos de espera innecesarios durante fallos repetidos o temporales.

## Considered Options

1. Implementar el patrón Circuit Breaker en las llamadas HTTP entre microservicios.
2. Gestionar los fallos mediante simples reintentos configurados en el cliente HTTP.
3. Dejar las llamadas síncronas sin un manejo explícito de fallos, confiando en la estabilidad de los servicios.

## Decision Outcome

**Chosen Option:** Implementar el patrón Circuit Breaker en las llamadas HTTP entre microservicios críticos.  

El patrón Circuit Breaker monitorea las conexiones a servicios externos (como Mercado Libre) y entre microservicios internos, como Pagos y Pedidos. Si nota muchos errores en poco tiempo, detiene temporalmente las conexiones, evitando más problemas y permitiendo que el sistema reduzca sus funciones de forma controlada.

### Consequences

#### Good
- Se reduce el impacto de los fallos en cascada en el sistema, protegiendo la estabilidad general.
- Al evitar llamadas a servicios en fallos recurrentes, se optimizan los recursos del sistema.
- Permite degradar la funcionalidad del sistema de manera planificada, ofreciendo respuestas rápidas a los usuarios.

#### Bad
- Aumenta la complejidad del sistema al requerir herramientas adicionales como Hystrix o Resilience4j.
- Al abrirse el circuito, algunos servicios pueden experimentar retrasos adicionales mientras se reintentan las conexiones.

## Pros and Cons of the Options

### Opción 1: Implementar el patrón Circuit Breaker
- **Good:** Manejo eficiente de fallos intermitentes o temporales.
- **Good:** Mejora la resiliencia del sistema completo.
- **Bad:** Introduce complejidad adicional en la configuración y monitoreo.

### Opción 2: Gestionar fallos mediante reintentos
- **Good:** Sencillo de implementar y suficiente para servicios con baja criticidad.
- **Bad:** Puede aumentar la carga del sistema si los reintentos no están optimizados.

### Opción 3: Sin manejo explícito de fallos
- **Good:** Configuración más simple y rápida.
- **Bad:** Alta vulnerabilidad a fallos en cascada, comprometiendo la estabilidad del sistema.

## More Information

Se usará "Resilience4j" para implementar el Circuit Breaker en las llamadas HTTP entre microservicios. Este patrón se aplicará inicialmente en las interacciones entre los servicios de Pagos, Clientes y la pasarela externa de Mercado Libre, evaluando su impacto mediante pruebas de carga y simulación de fallos.
