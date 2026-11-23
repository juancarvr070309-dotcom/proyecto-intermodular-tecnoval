# 7. Planificación del proyecto

## 7.1. Fases del proyecto

| Fase | Actividades | Resultado esperado |
|---|---|---|
| 1. Análisis | Revisar empresa, departamentos, usuarios, servicios y necesidades TIC. | Necesidades documentadas. |
| 2. Diseño | Comparar alternativas, acordar decisiones, validar compatibilidad, diseñar red, direccionamiento, recursos y presupuesto. | Diseño técnico, acta de decisiones y presupuesto contrastado. |
| 3. Preparación | Comprobar inventario, equipos, licencias, permisos y recursos antes de comprar o instalar. | Lista de requisitos y compras aprobada. |
| 4. Implantación | Instalar y configurar los servicios aprobados por fases. | Infraestructura configurada. |
| 5. Pruebas | Verificar conectividad, permisos, segmentación, copias y restauración. | Registro de pruebas e incidencias. |
| 6. Documentación | Actualizar diagramas, inventario, IP, procedimientos y conclusiones. | Documentación final revisada. |

La documentación del proyecto y el laboratorio virtual no equivalen a una implantación de producción. Los servicios se marcarán como implantados solo cuando existan pruebas y evidencias reales.

## 7.2. Metodología Scrum

El equipo está formado por Juan Carlos Vasconez Rojas e Isaac Matias Beltran Moreno. Se trabajará por bloques y revisiones cortas: seleccionar tareas, asignar responsables, realizar el trabajo, revisar la evidencia y actualizar el estado en Trello.

## 7.3. Reparto de responsabilidades propuesto

| Integrante | Responsabilidad principal | Revisión cruzada |
|---|---|---|
| Juan Carlos Vasconez Rojas | Coordinación del calendario, documentación, inventario de evidencias, pruebas de aceptación y seguimiento de Trello | Revisar con Isaac las decisiones técnicas y el presupuesto |
| Isaac Matias Beltran Moreno | Diseño/configuración de red, hosts, virtualización, servidores y servicios de infraestructura | Revisar con Juan Carlos documentación, pruebas y evidencias |
| Ambos | Acordar alternativas, confirmar decisiones, revisar compatibilidad y cotizaciones, aprobar cambios y preparar la entrega | Ambos deben confirmar las decisiones importantes |

Este reparto es una propuesta de organización. Para que exista evidencia de consenso, ambos integrantes deben confirmar el reparto y asignarse las tarjetas en Trello. No se atribuyen tareas como aceptadas por el otro integrante sin su confirmación.

## 7.4. Organización y revisión del tablero Trello

**Tablero:** [Proyecto Intermodular — TecnoVal Assistència IT](https://trello.com/b/PPo2BEAZ/proyecto-intermodular-tecnoval-assistencia-it-juan-carlos-isaac-beltran).

El equipo debe comprobar las listas del tablero y utilizar estos criterios:

- **Por hacer:** trabajo que todavía no se ha iniciado.
- **En curso:** trabajo que se está realizando.
- **Revisión:** trabajo terminado por su responsable, pero pendiente de comprobación.
- **Realizadas:** trabajo revisado, con evidencia y aceptación del equipo.

Si el tablero utiliza nombres de listas diferentes, se mantendrán los nombres reales y se aplicará el mismo criterio. Una tarjeta no se moverá a «Realizadas» solo porque exista un documento en GitHub: debe comprobarse su contenido y adjuntarse la evidencia.

### Estado documental del Bloque 2

| Tarea | Evidencia que ya existe en GitHub | Estado correcto antes de la revisión |
|---|---|---|
| Identificar necesidades y comparar alternativas | 01-necessitats.md y 02-alternatives-viabilitat.md | Documentación redactada; falta confirmar consenso y revisar la decisión web. |
| Diseñar red y direccionamiento | 03-disseny-xarxa.md, 04-adrecament-ip.md y diagrama | Diseño documentado; falta validar equipos, conexiones, puertos y compatibilidad. |
| Seleccionar recursos y presupuesto | 05-recursos.md y 06-pressupost.md | Inventario propuesto; faltan modelos/cotizaciones, discos NAS, cálculo de SAI y costes de mantenimiento. |
| Planificar con Scrum y Trello | Este documento y el tablero | Plan redactado; falta asignar responsables y sincronizar estados reales. |
| Integrar documentación y README | Archivos del repositorio | Revisar enlaces, coherencia entre documentos y evidencias. |
| Guardar avances y preparar entrega | Commits y tablero | Pendiente de revisión final y confirmación del acceso del profesorado. |

**Importante:** estos estados describen el estado documental conocido, no el estado actual de las tarjetas de Trello. Antes de entregar, consultar Trello y corregir las listas para que no haya tarjetas «Realizadas» que sigan pendientes de pruebas, consenso o cotizaciones.

## 7.5. Registro de acuerdos del equipo

Completar esta tabla durante una reunión o revisión conjunta. Añadir fecha y enlace a la tarjeta, comentario o captura de Trello que demuestre el acuerdo.

| Decisión | Propuesta que se debe confirmar | Confirmación de Juan Carlos | Confirmación de Isaac | Fecha y evidencia |
|---|---|---|---|---|
| Alojamiento web | Externo en la primera fase; sin servidor web propio en DMZ | Pendiente | Pendiente | Pendiente |
| Hardware de virtualización | Dos hosts; modelos sujetos a comprobación de compatibilidad | Pendiente | Pendiente | Pendiente |
| NAS | QNAP TS-464-8G + cuatro discos NAS compatibles, pendiente de cotización | Pendiente | Pendiente | Pendiente |
| Red | Dos switches gestionables de 24 puertos | Pendiente | Pendiente | Pendiente |
| Reparto de tareas | Juan Carlos coordina/documenta/prueba; Isaac coordina infraestructura; ambos revisan | Pendiente | Pendiente | Pendiente |

No rellenar las confirmaciones ni las fechas hasta que los dos integrantes hayan participado.

## 7.6. Evidencia del tablero

**Enlace:** [Abrir Trello](https://trello.com/b/PPo2BEAZ/proyecto-intermodular-tecnoval-assistencia-it-juan-carlos-isaac-beltran).

Añadir una captura actualizada donde se vean las listas, las tarjetas del Bloque 2, las personas asignadas y las tareas que permanecen en revisión. La captura antigua no demuestra el estado actual si las tarjetas han cambiado.

## 7.7. Criterio de finalización

La planificación se considerará revisada cuando:
- Las decisiones principales estén confirmadas por ambos integrantes.
- Las tarjetas tengan responsables y estados que coincidan con el trabajo real.
- Las tareas pendientes de comprobación permanezcan en revisión y no aparezcan como finalizadas.
- Las evidencias estén enlazadas en las tarjetas.
- El presupuesto incluya hardware completo, servicios del primer año, instalación y mantenimiento.
- El repositorio, el diagrama y los documentos sean coherentes.
