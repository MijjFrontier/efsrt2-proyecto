# Formulario de Pre-Kickoff (Interno)

A continuación se presenta el checklist de validación para la preparación del proyecto RestoFlow.

### Información General

| Campo             | Valor                                                                                                |
| :---------------- | :--------------------------------------------------------------------------------------------------- |
| **CLIENTE**       | El Restaurante (Usuario final del sistema)                                                           |
| **NOMBRE PROYECTO** | RestoFlow                                                                                            |
| **SPONSOR - PO**  | Dueño del Restaurante / Gerente de Operaciones                                                       |
| **FECHA**         | [Fecha actual]                                                                                       |
| **ESTADO PREKICK OFF** | **APROBADO** (Listo para Kickoff)                                                                    |

<br/>

### Equipo del Proyecto y Roles

| Nombre - Encargados del Proyecto   | Objetivo asignado al proyecto                                                                        |
| :--------------------------------- | :----------------------------------------------------------------------------------------------------- |
| Patricia Chumbimune - Scrum Master | Facilitación de ceremonia, eliminación de bloqueos y aseguramiento de agilidad.                         |
| Mijail Guillem - Backend Developer | Arquitectura de servidores (Node.js), modelado de datos en Firebase y seguridad de API.              |
| Angel Namay - Frontend Developer   | Implementación de interfaces interactivas y consumo de servicios en tiempo real.                       |
| Yori Huallpachoque - UI/UX Designer  | Diseño de sistemas de diseño (Design Systems), prototipado y optimización de flujos de usuario.      |
| Maria C. Malpartida - QA Engineer    | Control de calidad, diseño de planes de prueba (Unitarias/Integración) y gestión de defectos.         |

<br/>

### Preguntas Clave para el Sponsor / Product Owner

A continuación, se presentan preguntas estratégicas dirigidas al Sponsor o Product Owner para alinear la visión del proyecto con las necesidades del negocio.

| N° | Pregunta                                                                 | Respuesta (Propuesta)                                                                                                                                                                                            |
| :- | :----------------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1  | **¿Cuál es el valor principal que `RestoFlow` aporta al negocio?**         | El valor principal es la **optimización de la operación** para reducir errores manuales y agilizar el servicio, lo que se traduce directamente en ahorro de costos (menos platos devueltos) y mayor satisfacción del cliente. |
| 2  | **¿Qué problemas específicos buscamos resolver con esta implementación?** | Buscamos eliminar 3 problemas clave: **1)** Errores en la toma de comandas a mano, **2)** Lentitud en la comunicación entre salón y cocina, y **3)** Dificultad para hacer un cierre de caja rápido y sin descuadres.   |
| 3  | **¿Cómo se alinea `RestoFlow` con los objetivos actuales del restaurante?** | Se alinea directamente con el objetivo de **mejorar la eficiencia operativa** y **elevar la experiencia del cliente**. Un servicio más rápido y preciso aumenta la rotación de mesas y fomenta la lealtad de los comensales. |
| 4  | **¿Cuál es el indicador de éxito más importante para este prototipo (KPI)?** | El KPI principal será la **reducción del tiempo promedio desde que se toma el pedido hasta que el plato se marca como listo** en cocina. Secundariamente, la disminución de notas de crédito por errores en los pedidos. |
| 5  | **Mirando al futuro, ¿qué funcionalidad sería la siguiente gran prioridad?** | La integración con **pasarelas de pago** para procesar tarjetas directamente y un **módulo básico de control de inventario** son las evoluciones más lógicas para seguir optimizando la rentabilidad del restaurante. |

<br/>

### Checklist de Validación de Preparación

| Pregunta                                                                                         | Respuesta | Justificación                                                                                                                                                                                                                                  |
| :----------------------------------------------------------------------------------------------- | :-------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **¿En la propuesta, existe algún problema / desafío técnico no abordado?**                         | **Bajo**    | **NO.** Los desafíos técnicos clave (sincronización en tiempo real, persistencia de datos, arquitectura serverless) se han abordado satisfactoriamente con la selección de Vercel y Firebase, como se detalla en la documentación técnica. |
| **¿El proyecto cuenta con pendientes en el cierre para su ejecución?**                             | **Bajo**    | **NO.** El alcance funcional del prototipo está completo. La carga de datos reales (menú, empleados) y la capacitación son parte de la puesta en marcha (Go-Live), no pendientes que impidan el desarrollo.                                 |
| **¿Existe alguna definición pendiente del producto o servicio?**                                   | **Bajo**    | **NO.** Todas las funcionalidades, roles y entidades de datos para el alcance del prototipo están definidos y documentados en el `DATA_DICTIONARY.md` y `DEVELOPMENT_ANALYSIS.md`.                                                           |
| **¿Existen actividades requeridas no especificadas o faltantes en la propuesta?**                  | **Bajo**    | **NO.** La propuesta cubre el ciclo completo del prototipo funcional. Mejoras futuras (pasarelas de pago, control de inventario) están fuera del alcance inicial y se consideran como evoluciones del producto, no como faltantes.      |
| **¿Existe alguna dependencia del proyecto que ponga en riesgo su capacidad de cumplir con el plazo / alcance?** | **Bajo**    | **NO.** La dependencia principal es sobre los servicios cloud de Vercel y Firebase, que son plataformas de alta disponibilidad y bajo riesgo. No existen dependencias de terceros desconocidas o de alto riesgo que pongan en peligro el alcance actual. |
| **¿Existe algún problema con algún producto, sistema o software que deba ser considerado?**         | **Bajo**    | **NO.** El stack tecnológico (Next.js, React, Firebase) es moderno, estable y está bien documentado. No se han identificado problemas de compatibilidad o limitaciones que afecten los objetivos del proyecto.                                     |

---

# Propuesta de Ambientes para el Proyecto RestoFlow

Para el proyecto RestoFlow, y siguiendo las mejores prácticas para una arquitectura moderna con Vercel y Firebase, se definen dos ambientes principales en el ciclo de despliegue: **Pruebas (TEST / QA)** y **Producción**. Esta estructura simplificada y eficiente garantiza que podamos probar nuevas funcionalidades de forma segura sin afectar nunca la operación real del restaurante.

A continuación, se detalla la configuración y el propósito de cada ambiente.

---

## Ambiente de Pruebas (TEST)

El objetivo de este ambiente es ser una réplica exacta del sistema de producción, donde se validará exhaustivamente cada nueva funcionalidad o corrección antes de que sea utilizada en la operación real del restaurante. Esto garantiza la máxima estabilidad y minimiza cualquier riesgo.

*   **Plataforma y Despliegue:**
    *   **Despliegues de "Preview" en Vercel:** Por cada cambio propuesto en el código, Vercel crea automáticamente una URL de previsualización única (ej: `restoflow-abc123.vercel.app`). Este entorno aislado nos permite probar los cambios sin afectar a otros desarrolladores ni al sistema en producción.

*   **Base de Datos:**
    *   **Proyecto de Firebase para Pruebas:** Se utilizará un proyecto de Firebase completamente separado (ej: `restoflow-test-db`). Esta base de datos contendrá datos ficticios (mesas, menú, empleados, transacciones de prueba), permitiéndonos simular la operación del restaurante sin generar "basura" en los datos reales.

*   **Funcionalidades a Validar en TEST:**
    Este ambiente debe soportar y permitir la validación de todas las funcionalidades del sistema, entre las cuales se incluyen:
    *   **Autenticación y Roles:**
        *   Inicio de sesión seguro por PIN para los roles: Administrador, Camarero, Cajero y Cocina.
        *   Redirección automática a la interfaz correcta según el rol.
        *   Funcionalidad para que los empleados puedan cambiar su propio PIN.
    *   **Módulo de Administrador:**
        *   **Gestión de Empleados:** Creación, edición y eliminación de personal.
        *   **Gestión de Menú:** Creación, edición y eliminación de productos y categorías.
        *   **Gestión de Mesas:** Creación y eliminación de mesas.
        *   **Visualización de Reportes:** Acceso a reportes de ventas, rendimiento y análisis de datos.
        *   **Cierre de Caja Centralizado:** Capacidad de ver el reporte del turno y realizar el cierre.
    *   **Módulo de Camarero:**
        *   Visualización del plano de mesas con sus estados en tiempo real (Libre, Ocupada, Listo para Servir).
        *   Toma de pedidos, incluyendo la adición de notas especiales por producto.
        *   Envío de comandas a la cocina.
        *   Notificación visual cuando un pedido está listo para ser recogido.
    *   **Módulo de Cocina:**
        *   Recepción de comandas en una pantalla, ordenadas cronológicamente.
        *   Visualización del detalle de cada pedido.
        *   Opción para marcar pedidos como "Listos", notificando al camarero.
    *   **Módulo de Cajero:**
        *   Visualización de mesas pendientes de pago.
        *   Procesamiento de pagos, incluyendo división de cuentas y múltiples métodos de pago (Efectivo, Tarjeta, Yape, Plin).
        *   Generación de recibos.
        *   Cierre del turno de caja y exportación de reporte.

---

## Ambiente de Producción (PRODUCCIÓN)

Este es el ambiente final, estable y seguro que el personal del restaurante utilizará en su operación diaria. Solo se despliega código que ha sido previamente validado y aprobado en el ambiente de TEST.

*   **Plataforma y Despliegue:**
    *   **Despliegue Principal en Vercel:** Es la URL principal y definitiva de la aplicación (ej: `app.restoflow.com`). Este entorno se actualiza de forma controlada solo cuando los cambios son estables y han sido aprobados.

*   **Base de Datos:**
    *   **Proyecto de Firebase para Producción:** Se conectará a un segundo proyecto de Firebase (`restoflow-produccion`), dedicado exclusivamente a la operación real. Esta base de datos contendrá la información crítica del negocio y estará completamente aislada de los datos de prueba.

*   **Funcionalidades Operativas en PRODUCCIÓN:**
    El ambiente de producción ejecuta la versión estable y validada de todas las funcionalidades del sistema, garantizando la continuidad del negocio. Las funcionalidades son idénticas a las probadas en TEST:
    *   **Autenticación y Roles:**
        *   Inicio de sesión seguro por PIN para los roles: Administrador, Camarero, Cajero y Cocina.
        *   Redirección automática a la interfaz correcta según el rol.
        *   Funcionalidad para que los empleados puedan cambiar su propio PIN.
    *   **Módulo de Administrador:**
        *   **Gestión de Empleados:** Creación, edición y eliminación de personal.
        *   **Gestión de Menú:** Creación, edición y eliminación de productos y categorías.
        *   **Gestión de Mesas:** Creación y eliminación de mesas.
        *   **Visualización de Reportes:** Acceso a reportes de ventas, rendimiento y análisis de datos.
        *   **Cierre de Caja Centralizado:** Capacidad de ver el reporte del turno y realizar el cierre.
    *   **Módulo de Camarero:**
        *   Visualización del plano de mesas con sus estados en tiempo real (Libre, Ocupada, Listo para Servir).
        *   Toma de pedidos, incluyendo la adición de notas especiales por producto.
        *   Envío de comandas a la cocina.
        *   Notificación visual cuando un pedido está listo para ser recogido.
    *   **Módulo de Cocina:**
        *   Recepción de comandas en una pantalla, ordenadas cronológicamente.
        *   Visualización del detalle de cada pedido.
        *   Opción para marcar pedidos como "Listos", notificando al camarero.
    *   **Módulo de Cajero:**
        *   Visualización de mesas pendientes de pago.
        *   Procesamiento de pagos, incluyendo división de cuentas y múltiples métodos de pago (Efectivo, Tarjeta, Yape, Plin).
        *   Generación de recibos.
        *   Cierre del turno de caja y exportación de reporte.

*   **Puesta en Marcha (Go-Live):**
    *   **Configuración Inicial (Setup):**
        1.  Carga masiva del menú real del restaurante.
        2.  Creación de todas las cuentas de empleados reales con sus roles y PINs.
        3.  Configuración de las mesas del restaurante.
    *   **Capacitación (Training):** Se realizará con el personal utilizando el sistema en producción.
    *   **Lanzamiento:** Inicio de la operación del restaurante con RestoFlow.

*   **Operación y Monitorización:**
    *   Supervisión continua del rendimiento y respaldos automáticos de la base de datos de producción.

---

### Detalle de Entregables e Infraestructura por Ambiente

| Ambientes Involucrados | Detalle de entregables - tecnologías - infraestructura - desarrollo                                                                                                                                                                                                                                                                                                                       |
| :------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **TEST (QA)**        | **Entregable:** Versión funcional y aislada de RestoFlow para validación interna y del cliente.<br/>**Tecnologías:** Next.js, React, Tailwind CSS, Firebase Firestore.<br/>**Infraestructura:** Despliegue en **Vercel** como "Preview Deployment" con URL temporal. Base de datos en un **proyecto de Firebase separado para pruebas**, con datos ficticios.<br/>**Desarrollo:** Cada nueva funcionalidad o cambio se despliega aquí automáticamente para ser probado antes de pasar a producción. |
| **Producción**       | **Entregable:** Versión estable y final de RestoFlow para uso diario del restaurante.<br/>**Tecnologías:** Next.js, React, Tailwind CSS, Firebase Firestore.<br/>**Infraestructura:** Despliegue en **Vercel** como "Production Deployment" con la URL final (ej: `app.restoflow.com`). Base de datos en un **proyecto de Firebase dedicado a producción**, con datos reales y respaldos automáticos.<br/>**Desarrollo:** Solo se despliega código que ha sido exhaustivamente probado y aprobado en el ambiente de TEST. |

---

### Hitos y Entregables del Proyecto

| HITO / ENTREGABLE                  | ENTREGABLE CLAVE                                                                                               | PORCENTAJE | VALOR |
| :--------------------------------- | :------------------------------------------------------------------------------------------------------------- | :--------- | :---- |
| **Inception & Discovery (Análisis)** | Documentación de análisis (Pre-Kickoff, PESTEL, Diccionario de Datos), prototipo inicial y arquitectura definida.  |            |       |
| **Sprint Zero & Core Development**   | Prototipo funcional con todos los módulos clave desarrollados (Admin, Camarero, Cocina, Cajero).             |            |       |
| **Integración y QA (Certificación)** | Ciclo de pruebas completo en el ambiente de TEST. Corrección de errores y validación del cliente (UAT).          |            |       |
| **Go-Live & Marcha Blanca**        | Despliegue en Producción, capacitación del personal, carga de datos reales y soporte durante los primeros días. |            |       |
| **TOTAL**                          |                                                                                                                | **100%**   |       |
