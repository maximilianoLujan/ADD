---
status: "proposed"
date: 2024-11-16
decision-makers: ["Lujan Maximiliano - ASS", "Ciano Ignacio - ASJ", "Lujan Nicolas - ASC"]
---

# Sistema de monitoreo y trazabilidad

## Context and Problem Statement

La compañía de productos alimenticios maneja información altamente sensible, incluyendo datos personales de los clientes y transacciones financieras. Además, las operaciones críticas, como la gestión de pedidos y pagos, requieren un funcionamiento preciso y confiable para garantizar la satisfacción del cliente y la continuidad del negocio. Por ello, es imperativo contar con un sistema de monitoreo robusto que permita detectar errores o anomalías en tiempo real, habilitando una respuesta rápida y eficiente para minimizar riesgos y tiempos de inactividad.

## Decision Drivers

* El sistema debe permitir identificar fallos y anomalías en tiempo real, minimizando el tiempo de diagnóstico y respuesta.
* La protección de datos personales y financieros es prioritaria, lo que exige un sistema de monitoreo que cumpla con estándares de seguridad
* La arquitectura debe manejar un alto volumen de datos de monitoreo (logs, métricas y trazas) sin impactar el rendimiento del sistema principal.

## Considered Options

* Opción 1: Usar Prometheus para la recolección de métricas del sistema (uso de CPU, memoria, latencia, etc.) y Grafana para visualizar esas métricas en dashboards.
* Opción 2: Utilizar servicio AWS CloudWatch (servicio en la nube de AWS).
* Opción 3: Utilizar ELK Stack para centralizar todos los logs generados por los microservicios en un único lugar, permitiendo la visualización y análisis en tiempo real.

## Decision Outcome

Chosen option: Opción 2: Utilizar servicio AWS CloudWatch (servicio en la nube de AWS). Amazon web services es una plataforma segura, escalable y completamente gestionada que cumple con estándares de seguridad internacionales y proporciona herramientas avanzadas para proteger datos sensibles del sistema.

### Consequences

* Good: AWS ofrece herramientas de seguridad robustas y cumplimiento con estándares globales, protegiendo los datos sensibles de los clientes.
* Good: Las herramientas que ofrece AWS son facilmente integrables.
* Good: Es un proveedor de confianza y de renombre, por lo que contariamos con soporte en todo momento.
* Bad: El uso de AWS puede volverse costoso dependiendo del uso de recursos, especialmente si la infraestructura no está bien gestionada.
* Bad: Dependemos de un proveedor, si se corrumpe informacion en su sistema puede perjudicar directamente al nuestro.

### Confirmation

* Soporte Continuo y Flexibilidad: La amplia documentación y el soporte técnico 24/7 de AWS proporcionarán la asistencia necesaria para la gestión eficiente de nuestros servicios de monitoreo y trazabilidad.
* Cumplimiento con Requisitos de Seguridad: AWS ofrece una sólida infraestructura de seguridad que cumple con los estándares internacionales, lo cual es crucial para el manejo de datos sensibles de clientes.

## Pros and Cons of the Options

### Opción 1: Usar Prometheus para la recolección de métricas del sistema (uso de CPU, memoria, latencia, etc.) y Grafana para visualizar esas métricas en dashboards.

* Good: gratuito, de codigo abierto y con una comunidad muy activa.
* Bad: Requiere más trabajo de configuración y mantenimiento.
* Bad: Al no ser gestionado, necesitamos contar con un equipo tecnico capacitado para manejarlo.

### Opción 2: Utilizar servicio AWS CloudWatch (servicio en la nube de AWS).

* Good: AWS ofrece herramientas de seguridad robustas y cumplimiento con estándares globales, protegiendo los datos sensibles de los clientes.
* Good: Las herramientas que ofrece AWS son facilmente integrables.
* Good: Es un proveedor de confianza y de renombre, por lo que contariamos con soporte en todo momento.
* Bad: El uso de AWS puede volverse costoso dependiendo del uso de recursos, especialmente si la infraestructura no está bien gestionada.
* Bad: Dependemos de un proveedor, si se corrumpe informacion en su sistema puede perjudicar directamente al nuestro.

### Opción 3: Utilizar ELK Stack para centralizar todos los logs generados por los microservicios en un único lugar, permitiendo la visualización y análisis en tiempo real.

* Good: Ofrece dashboards interactivos y análisis detallado con Kibana.
* Bad: Requiere un conocimiento avanzado para configurarlo y optimizarlo.

## More Information

Las metricas a analizar son tiempos de respuesta de los microservicios, uso de CPU/memoria y tasa de errores (codigos HTTP 5xx)