---
status: "accepted"
date: 2024-11-26
decision-makers: ["Lujan Maximiliano - ASS", "Ciano Ignacio - ASJ", "Lujan Nicolas - ASC"]
---

# Patron Singleton para instancias de bases de datos en el microservicio de Pagos


## Context and Problem Statement

El microservicio de Pagos es crítico dentro de la nueva arquitectura basada en microservicios, ya que gestiona todas las interacciones con la pasarela de pago externa proporcionada por Mercado Libre. Este módulo debe garantizar la seguridad y eficiencia en la gestión de transacciones financieras, asegurando consistencia en las operaciones y cumplimiento con las políticas de la pasarela.

## Decision Drivers

* Seguridad, centralizar la gestión de tokens de autenticación y claves API para evitar el riesgo de exposición o uso indebido.
* Seguridad, reducir la superficie de ataque limitando el acceso a los recursos sensibles a través de una única instancia controlada.

## Decision Outcome

Se decide utilizar el patron de diseño singleton en componentes del microservicio de Pagos que requieran una unica instancia compartida, como:

* Gestores de conexión a bases de datos.
* Proveedores de configuración global.
* Manejo de autenticación y credenciales seguras.

El patrón Singleton garantizará que solo se cree una instancia única de estos componentes y que sea accesible globalmente dentro de cada microservicio.

## Pros and Cons of the Options

* Good, los recursos compartidos se gestionan de manera uniforme y centralizada.
* Good, Al reutilizar instancias existentes, se disminuye el overhead asociado a la creación de múltiples objetos.
* Good, facil de mantener. Los cambios en la configuración o en los recursos compartidos afectan a toda la aplicación de manera inmediata.
* Bad, puede introducir un acoplamiento implícito entre componentes que dependen de la misma instancia.


## More Information

El uso del patrón Singleton se aplicará exclusivamente al microservicio de Pagos, ya que:

* Las pasarelas de pago suelen requerir autenticación, como claves API o tokens de acceso, que necesitan mantenerse actualizados y seguros. Una única instancia centralizada permite gestionar eficientemente estos recursos sensibles.
* Evita la creación repetida de conexiones a la pasarela, lo que reduce la sobrecarga de inicialización y mejora el rendimiento.
