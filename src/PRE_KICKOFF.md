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

<br/>

### Gestión de Riesgos

A continuación se detallan los riesgos identificados para la implementación de RestoFlow.

| N° | Causa | Riesgo | Consecuencia | Calificación | Nivel | Urgencia |
| :-- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Dependencia de conexión a internet para sincronización en tiempo real con Firestore. | Interrupción en la comunicación entre salón, cocina y administración. | Retraso en pedidos, descoordinación operativa y posible pérdida de ventas. | 4.2 | 🔴 | Alta |
| 2 | Resistencia al cambio tecnológico por parte del personal del restaurante. | Adopción lenta o incorrecta de la herramienta RestoFlow. | Baja eficiencia inicial, frustración del personal y errores en la toma de pedidos. | 3.5 | 🟡 | Media |
| 3 | Falla de hardware (tablets, móviles) en el punto de venta o cocina. | Incapacidad de acceder al sistema para registrar o visualizar pedidos. | Paralización del servicio en mesas específicas o retrasos críticos en la producción. | 3.8 | 🟡 | Media |
| 4 | Gestión inadecuada de la seguridad de los PIN de acceso de los empleados. | Acceso no autorizado a funciones críticas (ej. caja o administración). | Fuga de información sensible o manipulación indebida de registros de ventas. | 4.5 | 🔴 | Alta |
| 5 | Cambios inesperados en los costos o políticas de los servicios cloud (Firebase/Vercel). | Aumento en el presupuesto operativo o necesidad de migración técnica. | Impacto en la rentabilidad del proyecto o interrupción del servicio por falta de pago. | 2.5 | 🟢 | Baja |

<br/>

### Propuesta de Ambientes para el Proyecto RestoFlow

Para el proyecto RestoFlow, y siguiendo las mejores prácticas para una arquitectura moderna con Vercel y Firebase, se definen dos ambientes principales en el ciclo de despliegue: **Pruebas (TEST / QA)** y **Producción**. Esta estructura simplificada y eficiente garantiza que podamos probar nuevas funcionalidades de forma segura sin afectar nunca la operación real del restaurante.

---

## Ambiente de Pruebas (TEST)

El objetivo de este ambiente es ser una réplica exacta del sistema de producción, donde se validará exhaustivamente cada nueva funcionalidad o corrección antes de que sea utilizada en la operación real del restaurante.

*   **Plataforma y Despliegue:** Despliegues de "Preview" en Vercel. URL única por cambio.
*   **Base de Datos:** Proyecto de Firebase para Pruebas independiente con datos ficticios.
*   **Funcionalidades a Validar:** Todas las descritas en el alcance (Admin, Camarero, Cocina, Cajero).

---

## Ambiente de Producción (PRODUCCIÓN)

Este es el ambiente final, estable y seguro que el personal del restaurante utilizará en su operación diaria.

*   **Plataforma y Despliegue:** URL principal definitiva en Vercel.
*   **Base de Datos:** Proyecto de Firebase para Producción con datos críticos y reales.
*   **Funcionalidades Operativas:** Todas las funcionalidades validadas y estables.

---

### Detalle de Entregables e Infraestructura por Ambiente

| Ambientes Involucrados | Detalle de entregables - tecnologías - infraestructura - desarrollo                                                                                                                                                                                                                                                                                                                       |
| :------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **TEST (QA)**        | **Entregable:** Versión funcional y aislada de RestoFlow para validación interna y del cliente.<br/>**Tecnologías:** Next.js, React, Tailwind CSS, Firebase Firestore.<br/>**Infraestructura:** Despliegue en **Vercel** como "Preview Deployment". Base de datos en un **proyecto de Firebase separado para pruebas**.<br/>**Desarrollo:** Validación continua antes de pasar a producción. |
| **Producción**       | **Entregable:** Versión estable y final de RestoFlow para uso diario del restaurante.<br/>**Tecnologías:** Next.js, React, Tailwind CSS, Firebase Firestore.<br/>**Infraestructura:** Despliegue en **Vercel** como "Production Deployment". Base de datos en un **proyecto de Firebase dedicado a producción**.<br/>**Desarrollo:** Código validado en TEST. |

<br/>

### Hitos y Entregables del Proyecto

| HITO / ENTREGABLE                  | ENTREGABLE CLAVE                                                                                               | PORCENTAJE | VALOR |
| :--------------------------------- | :------------------------------------------------------------------------------------------------------------- | :--------- | :---- |
| **Inception & Discovery (Análisis)** | Documentación de análisis (Pre-Kickoff, PESTEL, Diccionario de Datos), prototipo inicial y arquitectura definida.  |            |       |
| **Sprint Zero & Core Development**   | Prototipo funcional con todos los módulos clave desarrollados (Admin, Camarero, Cocina, Cajero).             |            |       |
| **Integración y QA (Certificación)** | Ciclo de pruebas completo en el ambiente de TEST. Corrección de errores y validación del cliente (UAT).          |            |       |
| **Go-Live & Marcha Blanca**        | Despliegue en Producción, capacitación del personal, carga de datos reales y soporte durante los primeros días. |            |       |
| **TOTAL**                          |                                                                                                                | **100%**   |       |
