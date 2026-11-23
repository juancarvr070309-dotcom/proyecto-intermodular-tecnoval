# 7. Seguimiento del sprint y registro de incidencias

## 7.1. Organización del seguimiento

El seguimiento se realizará al final de cada sesión de trabajo. Juan Carlos e Isaac revisarán las tarjetas de Trello y actualizarán este documento con:

- Tareas previstas y tareas realizadas.
- Tiempo utilizado.
- Problemas detectados y soluciones aplicadas.
- Tareas que quedan pendientes.
- Diferencias respecto al plan inicial.

**Tablero de Trello:** [Proyecto Intermodular — TecnoVal Assistència IT](https://trello.com/b/PPo2BEAZ/proyecto-intermodular-tecnoval-assistencia-it-juan-carlos-isaac-beltran).

## 7.2. Registro de sesiones

| Fecha | Tareas previstas | Tareas realizadas | Tiempo utilizado | Problemas o desviaciones | Trabajo pendiente |
|---|---|---|---|---|---|
| Pendiente de completar | Preparar el entorno y revisar los recursos | — | — | — | — |
| Pendiente de completar | Crear máquinas e instalar sistemas | — | — | — | — |
| Pendiente de completar | Configurar LAN, DMZ e IP | — | — | — | — |
| Pendiente de completar | Configurar enrutamiento y DHCP | — | — | — | — |
| Pendiente de completar | Pruebas, correcciones y documentación | — | — | — | — |

No se han añadido fechas ni tiempos ficticios. Completar las filas después de cada sesión.

## 7.3. Registro de incidencias

| Fecha | Equipo o tarea | Problema o desviación | Causa identificada | Intervención y responsable | Comprobación final | Comunicación al profesorado |
|---|---|---|---|---|---|---|
| — | — | Todavía no se ha registrado ninguna incidencia real | — | — | — | No aplica |

Cuando aparezca una incidencia real, añadir una fila con toda la información. Si no hay incidencias, mantenerlo indicado y justificarlo con las pruebas realizadas. No inventar problemas ni soluciones.

## 7.4. Comunicación de desviaciones

Si una incidencia afecta al plazo, los recursos o el alcance de la práctica:
1. Informar al profesorado lo antes posible.
2. Explicar el problema y la tarea afectada.
3. Proponer una alternativa e indicar si cambia el plazo.
4. Registrar la respuesta o el acuerdo en la tabla de incidencias.
5. Actualizar el plan, la tabla IP o el diagrama si el cambio lo requiere.

## 7.5. Revisión final

Completar este apartado cuando se hayan realizado las prácticas:

- **Qué funciona:** pendiente de las pruebas reales.
- **Qué queda pendiente:** pendiente de revisar las tareas y las pruebas.
- **Cambios respecto al Sprint 1:** el laboratorio utiliza dos redes de prueba, LAN `192.168.10.0/24` y DMZ `192.168.30.0/24`, con TV-COMMS como enrutador. Las demás VLAN del diseño empresarial no se despliegan en este laboratorio básico.
- **Aportación de Juan Carlos:** participar en la instalación, las pruebas, las capturas, la documentación y el seguimiento; concretar las tareas realizadas al terminar.
- **Aportación de Isaac:** participar en la instalación, la configuración de red y servidores, las pruebas y la documentación; concretar las tareas realizadas al terminar.

Las aportaciones deben describirse según el trabajo real y los commits de cada integrante, no según un reparto teórico.

## 7.6. Captura final de Trello

Añadir una captura real del tablero cuando las tarjetas estén actualizadas. La captura debe mostrar las listas y el estado de las tareas del Sprint 2.

**Enlace:** [Abrir el tablero de Trello](https://trello.com/b/PPo2BEAZ/proyecto-intermodular-tecnoval-assistencia-it-juan-carlos-isaac-beltran).

> **Pendiente:** insertar la captura final de Trello en `img/sprint-2/`. No se ha inventado ninguna captura.

## 7.7. Criterios de cierre

El Sprint 2 se podrá dar por finalizado cuando:
- Las cinco máquinas requeridas estén instaladas y arranquen.
- LAN y DMZ sean redes virtuales diferentes y no se solapen.
- Las IP fijas, los nombres y el diagrama coincidan con la configuración real.
- TV-COMMS mantenga el enrutamiento después de reiniciar.
- Los dos clientes reciban DHCP correctamente.
- Las pruebas y las incidencias estén documentadas.
- Las capturas reales estén guardadas en `img/sprint-2/`.
- Los siete documentos y el README estén revisados.
- Trello refleje el avance real y el profesorado tenga acceso a los recursos.

## 7.8. Fuentes técnicas

- [VirtualBox User Manual — Networking](https://www.virtualbox.org/manual/ch06.html).
- [Ubuntu Server documentation](https://ubuntu.com/server/docs).
- [Debian Administrator's Handbook](https://debian-handbook.info/) (cliente Linux Debian).
- [dnsmasq — documentación del proyecto](https://thekelleys.org.uk/dnsmasq/doc.html).
- [Linux kernel — IP sysctl](https://docs.kernel.org/networking/ip-sysctl.html).
