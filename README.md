# Arquitectura monolítica

- Enfoque tradicional y unificado para el desarrollo de software.
- La aplicación es construida como una unidad única y estrechamente integrada.
- Usualmente implica.
  - Client-side.
  - Server-side.
  - Capa de base de datos.

## Beneficios

- Tiene una base de código única.
- Simple para desarrollar.
- Fácil de desplegar porque tenemos todos nuestros dominios como una única unidad.
- Más fácil de hacer debugging.
- Testing simplificado.
- Usualmente implica una sola pila de tecnología, es decir que no necesitamos más de una tecnología en toda la aplicación.

## Retos

- Potencialmente difícil de entender y mantener debido a su tamaño y complejidad.
- Menor autonomía del equipo.
- El tener una sola pila de tecnología.
- Despliegue de pipeline potencialmente lento.
- No hay posibilidad de escalar los subdominios de forma individual.
- Si hay un error en algún subdominio, afectará toda la aplicación.

# Arquitectura de microservicios

Se basa en la construcción de subdominios como servicios separados.

- Estilo de arquitectura que estructura una aplicación como una colección de pequeños servicios independientemente desplegables.
- Cada servicio tendrá acceso a su base de datos específica, no a una base de datos general.
- Es orientada principalmente al backend, aunque el enfoque se utiliza también para el frontend.
- Los servicios se comunican por medio de APIs bien definidas.
- Para la comunicación se utilizan protocoloes tales como HTTP/HTTPS, WebSockets, o protocolo avanzado de colas de mensaje (Advanced Message Queuing Protocol AMQP).
- La comunicación de API puede ser directa entre el cliente-microservicio o con el patrón API gateway.

## Beneficios

- **Escalabilidad:** Permite tener servicios independientes, que pueden ser escalados bajo demanda por separado.
- **Desarrollo más rápido:** Los equipos pueden trabajar en servicios individuales independientemente, haciendo más rápidos los ciclos de desarrollo.
- **Flexibilidad en la tecnología:** Permite a los equipos escoger las mejores herramientas y lenguajes de programación para tareas específicas.
- **Aislamiento de fallos:** Los microservicios son diseñados para ser tolerantes a fallos. Si uno de los servicios falla, no afectará todo el sistema necesariamente.
- **Mantenibilidad mejorada:** Pequeños servicios que son más fáciles de entender, mantener y actualizar.
- **Aislamiento de datos:** Los microservicios pueden tener sus propios datos en soluciones de almacenamiento, lo que puede mejorar el aislamiento de datos y seguridad.
- **Monitoreo:** Cada servicio tiene su propio monitoreo, haciendo más fácil evaluar el rendimiento, problemas, etc.
- **Despliegue más sencillo:** Habilitan los pipelines (CI/CD) para despliegues automatizados.

## Retos

- **Complejidad operacional:** Administrar un gran número de microservicios puede ser operacionalmente complejo en términos de infraestructura, herramientas para desarrollo, monitoreo, etc.
- **Comunicación entre servicios:** Como los microservicios dependen de la comunicación de red, pueden haber problemas de latencia, consistencia de datos entre servicios.
- **Testing:** Probar los microservicios individualmente y hacer una integración adecuada puede ser un reto. Debuggear problemas en múltiples servicios puede ser complejo y demandar mucho tiempo.
- **Seguridad:** Puede ser más retador en ambientes de microservicios, ya que hay un mayor potencial de puntos de entrada para brechas de seguridad.

# Requerimientos funcionales

- Son funcionalidades específicas, comportamientos y capacidades que un sistema debe tener.
- Estos requerimientos describen lo que un sistema debe de hacer.
- Son usualmente definidos en detalle para guiar el proceso de diseño, desarrollo y testing.

# Requerimientos no funcionales

- Describen cómo el sistema debe de funcionar, más que qué debe hacer.
- Son requerimientos que describen cómo funciona el sistema.
- Se enfocan en los atributos de calidad y restricciones que un sistema debe tener.
- Son igual de importantes que los requerimientos funcionales, ya que impactan la experiencia de usuario con el sistema.
- Algunos ejemplos de requerimientos no funcionales son la escalabilidad, disponibilidad, etc.

# Herramientas

- **Elasticsearch:** Base de datos de todos nuestros logs para la aplicación.
- **Kibana:** Dashboard para ver todos nuestros logs en Kibana.
- **RabbitMQ:** Es nuestro Message Queue, lo que permitirá hacer nuestra comunicación asíncrona con los microservicios que creemos.
