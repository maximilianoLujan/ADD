---
status: "proposed"
date: 2024-11-20
decision-makers: ["Lujan Maximiliano - ASS", "Ciano Ignacio - ASJ", "Lujan Nicolas - ASC"]
---

# Despliegue de microservicio de clientes

## Context and Problem Statement

El microservicio de Cliente es un componente crítico del sistema, encargado de manejar información personal y sensible de los clientes, así como operaciones relacionadas con su gestión. Dada la naturaleza crítica de este servicio, es necesario definir un enfoque de despliegue que garantice alta disponibilidad, escalabilidad y seguridad. Además, el sistema debe ser capaz de manejar picos de carga sin degradar su rendimiento.

## Decision Drivers

* Seguridad, el despliegue debe incluir medidas robustas de seguridad, tales como cifrado en tránsito y en reposo, autenticación y autorización adecuadas, y auditorías de acceso a los datos.
* Alta disponibilidad: El sistema debe estar siempre accesible para evitar interrupciones.  
* Escalabilidad: El módulo debe poder manejar aumentos en la cantidad de solicitudes durante picos de carga. De ser necesario se debe poder levantar varias instancias para balanceo de carga.

## Considered Options

* Opción 1: Implementar el microservicio en contenedores Docker y desplegarlo en un clúster de Kubernetes gestionado (por ejemplo, EKS, GKE o AKS).
* Opción 2: Implementar el microservicio en contenedores Docker y desplegarlo en instancias EC2 autoadministradas.
* Opción 3: Desplegar el microservicio directamente en máquinas virtuales administradas sin contenerización.

## Decision Outcome

Chosen option: Opción 1: Implementar el microservicio en contenedores Docker y desplegarlo en un clúster de Kubernetes gestionado (por ejemplo, EKS, GKE o AKS).

### Consequences
#### **Good:**  
- Escalabilidad automática para manejar picos de carga.  
- Alta disponibilidad gracias a la replicación de contenedores.  
- Flexibilidad para realizar despliegues independientes del módulo de cliente.
#### **Bad:**  
- Complejidad operativa al necesitar configuraciones adicionales para Kubernetes.  
- Costos iniciales más altos debido a la infraestructura y herramientas necesarias para gestionar el clúster.
- Ninguno del equipo trabajo con estas tecnologias.

### Confirmation

* La elección se validará mediante pruebas de carga en el clúster de Kubernetes y simulaciones de fallos para evaluar la tolerancia a fallos. También se implementarán medidas de seguridad como certificados TLS para proteger los datos en tránsito.

## Pros and Cons of the Options

### Opción 1: Implementar el microservicio en contenedores Docker y desplegarlo en un clúster de Kubernetes gestionado (por ejemplo, EKS, GKE o AKS).

### Consequences
#### **Good:**  
- Escalabilidad automática para manejar picos de carga.  
- Alta disponibilidad gracias a la replicación de contenedores.  
- Flexibilidad para realizar despliegues independientes del módulo de cliente.
#### **Bad:**  
- Complejidad operativa al necesitar configuraciones adicionales para Kubernetes.  
- Costos iniciales más altos debido a la infraestructura y herramientas necesarias para gestionar el clúster.
- Ninguno del equipo trabajo con estas tecnologias.


### Opción 2: Implementar el microservicio en contenedores Docker y desplegarlo en instancias EC2 autoadministradas.

#### **Good:**  
- Simplicidad inicial al no depender de herramientas avanzadas como Kubernetes.
- Mayor control sobre los servidores, permitiendo personalización detallada.
#### **Bad:**  
- Escalabilidad limitada y necesidad de gestionar manualmente el balanceo de carga y las actualizaciones.
- Incremento del esfuerzo operativo en comparación con Kubernetes.
- Ninguno del equipo trabajo con estas tecnologias.


### Opción 3: Desplegar el microservicio directamente en máquinas virtuales administradas sin contenerización.

#### **Good:** 
- El equipo ya tiene experiencia trabajando con maquinas virtuales.
- Bajo costo de infraestructura inicial.
#### **Bad:**  
- Difícil de integrar con herramientas modernas de DevOps y monitoreo.
- Escalabilidad limitada y alto acoplamiento con la infraestructura física

## More Information

Este ADR será revisado después del primer despliegue y validación en producción. Se evaluará si la solución cumple con las expectativas de disponibilidad y rendimiento del microservicio de cliente. Si surgen nuevos requisitos o limitaciones técnicas, este ADR se actualizará en consecuencia.