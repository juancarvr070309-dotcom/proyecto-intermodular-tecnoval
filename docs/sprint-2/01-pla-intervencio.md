# 1. Plan de intervención y organización del trabajo

## 1.1. Objetivo

Implantar una infraestructura de laboratorio para TecnoVal Asistencia IT, basada en el diseño del Sprint 1. Se configurarán una red LAN, una DMZ separada, un servidor Linux de enrutamiento y DHCP, y dos clientes de prueba (Windows y Linux).

**Importante sobre las máquinas:** el PDF establece cinco equipos en total: servidor de comunicaciones Linux, servidor interno Windows, cliente Windows, cliente Linux y servidor Linux de la DMZ. Por tanto, solo dos son clientes. Se mantiene esta estructura mínima indicada por el profesorado, sin crear máquinas para los 12 trabajadores de la empresa.

## 1.2. Secuencia, dependencias y tiempo previsto

| Semana | Tareas | Dependencia | Responsable principal | Colaborador |
|---|---|---|---|---|
| 1 | Revisar IP, versiones, capacidad de los ordenadores y preparar VirtualBox/ISO | Ninguna | Juan Carlos | Isaac |
| 1 | Crear las cinco máquinas e instalar los sistemas | Recursos preparados | Isaac | Juan Carlos |
| 2 | Crear LAN y DMZ virtuales; configurar nombres e IP fijas | Máquinas instaladas | Isaac | Juan Carlos |
| 3 | Configurar enrutamiento IPv4 y conectividad exterior | Interfaces configuradas | Isaac | Juan Carlos |
| 3 | Instalar y configurar DHCP solo para la LAN | Enrutamiento y LAN operativos | Isaac | Juan Carlos |
| 4 | Configurar clientes mediante DHCP y realizar pruebas de conectividad | DHCP operativo | Juan Carlos | Isaac |
| 4 | Corregir incidencias y repetir pruebas | Resultados de las pruebas | Ambos | Ambos |
| 5 | Completar capturas, documentación, diagrama y revisión final | Configuración terminada | Juan Carlos | Isaac |
| 5 | Revisar GitHub, Trello y preparar la entrega | Documentos revisados | Ambos | Ambos |

Los tiempos son una previsión orientativa. Al final de cada sesión se anotará el tiempo real y el trabajo pendiente en Trello y en el documento 07.

## 1.3. Recursos materiales y software

- Ordenador anfitrión con VirtualBox y virtualización activada en BIOS/UEFI.
- Conexión a Internet para descargar actualizaciones e imágenes ISO.
- Imágenes ISO de Ubuntu Server 26.04.1 LTS para los servidores Linux, Debian 13 con XFCE para el cliente Linux y Windows (versiones autorizadas por el profesorado).
- Espacio libre recomendado: al menos 100 GB para las máquinas y las instantáneas.
- Memoria RAM recomendada: 16 GB en el anfitrión para ejecutar las cinco máquinas con comodidad. Si el equipo tiene menos memoria, se iniciarán solo las máquinas necesarias en cada prueba, siempre que se pueda mantener el entorno conectado.
- GitHub, Trello y editor de Markdown.

## 1.4. Distribución de las máquinas

Para simplificar la práctica, la primera opción es alojar las cinco máquinas virtuales en **un mismo ordenador anfitrión**. Así, las redes internas de VirtualBox llamadas `TecnoVal-LAN` y `TecnoVal-DMZ` serán compartidas por todas las máquinas del laboratorio.

Si se reparten entre los dos ordenadores físicos de los integrantes, las redes internas con el mismo nombre no se conectarán automáticamente. En ese caso, habrá que acordar con el profesorado una conexión física común (por ejemplo, adaptadores en modo puente a una red de laboratorio controlada) y comprobar que no se conecta accidentalmente a la red real del aula.

## 1.5. Permisos y autorizaciones

- Utilizar únicamente los ordenadores y las redes autorizados por el profesorado.
- No modificar la configuración de la red física del centro ni del router del aula.
- No conectar la LAN o la DMZ de pruebas a la red real sin autorización.
- Utilizar las ISO y licencias facilitadas o autorizadas por el centro.
- Informar al profesorado si falta algún permiso, recurso o versión de software.

## 1.6. Riesgos y medidas preventivas

| Riesgo | Medida preventiva | Medio de protección o recuperación |
|---|---|---|
| Fatiga por trabajar durante mucho tiempo frente a pantallas | Hacer pausas cortas, ajustar la postura y la iluminación y seguir las normas del aula | Silla y pantalla bien ajustadas |
| Manipulación de cables o conexiones eléctricas | No abrir equipos ni manipular enchufes con las manos húmedas; pedir ayuda al profesorado | Regletas en buen estado y supervisión |
| Pérdida de datos o configuraciones | Crear instantáneas antes de cambios importantes y copias de los archivos de configuración | Instantáneas de VirtualBox y copia de la documentación |
| Cambios de red que afectan a otros equipos | Utilizar redes internas virtuales y no modificar la red física | Aislamiento de VirtualBox y autorización docente |
| Sobrecarga de RAM o disco | Comprobar los recursos antes de iniciar todas las VM | Apagar las VM innecesarias y liberar espacio |

## 1.7. Imprevistos previstos

| Imprevisto | Solución prevista |
|---|---|
| Falta de memoria RAM | Reducir temporalmente la RAM asignada dentro de los límites del sistema, cerrar aplicaciones del anfitrión y ejecutar las pruebas por fases. |
| Espacio de disco insuficiente | Eliminar ISO duplicadas e instantáneas antiguas después de comprobar que no son necesarias; ampliar el espacio con autorización. |
| Una instalación no arranca | Revisar el orden de arranque, la ISO y la configuración de la VM; volver a una instantánea o repetir la instalación. |
| Las dos redes virtuales no se comunican | Revisar el nombre exacto de las redes, los adaptadores y las IP; comprobar que todas las VM están en el mismo anfitrión o en una red física común autorizada. |

## 1.8. Seguimiento

Al final de cada sesión, Juan Carlos e Isaac revisarán las tarjetas de Trello, anotarán el tiempo real, las tareas terminadas, las incidencias y el siguiente paso. Si una desviación pone en riesgo el plazo o cambia el alcance, se informará al profesorado y se registrará el acuerdo en el documento 07.

**Tablero de Trello:** [Proyecto Intermodular — TecnoVal Assistència IT](https://trello.com/b/PPo2BEAZ/proyecto-intermodular-tecnoval-assistencia-it-juan-carlos-isaac-beltran).

## 1.9. Distribución del trabajo

Los dos integrantes participarán en la instalación, las pruebas y la documentación. Como reparto inicial, Isaac coordinará la configuración de red y de los servidores, mientras que Juan Carlos coordinará el registro de pruebas, las capturas y la documentación. Las decisiones y comprobaciones finales se harán conjuntamente. El reparto se podrá ajustar según el trabajo real de cada sesión.
