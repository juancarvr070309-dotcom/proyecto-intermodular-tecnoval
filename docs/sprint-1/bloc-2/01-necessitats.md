# 1. Análisis de necesidades

## 1.1. Contexto
TecnoVal Asistencia IT es una empresa ficticia de Valencia con 12 trabajadores distribuidos en cinco departamentos. Presta soporte técnico, mantenimiento, instalación y administración de redes a pequeñas y medianas empresas.

## 1.2. Necesidades por departamento

| Departamento | Necesidad detectada | Usuarios afectados | Justificación |
|---|---|---:|---|
| Dirección | Acceso a informes, documentación y aplicaciones de gestión | 1 | Supervisar la actividad y tomar decisiones. |
| Administración y atención al cliente | Internet, correo corporativo, facturación, impresión y gestión documental | 2 | Gestiona clientes, citas, facturas y documentación. |
| Soporte técnico | Internet, soporte remoto, sistema de incidencias y documentación técnica | 5 | Atiende y registra incidencias de clientes. |
| Sistemas y redes | Acceso administrativo a servidores, switches, router, firewall y copias | 3 | Administra la infraestructura y mantiene los servicios. |
| Comercial | Internet, correo, presupuestos y web corporativa | 1 | Comunicarse con clientes y presentar servicios. |
| Toda la empresa | Red interna, Wi-Fi, cuentas individuales y permisos | 12 | Trabajar de forma coordinada y controlar el acceso. |
| Toda la empresa | Seguridad, actualizaciones y copias de seguridad | 12 | Proteger la información y reducir el impacto de incidentes. |

## 1.3. Necesidades generales
1. **Conectividad interna:** los 12 puestos deben comunicarse con servidores y recursos compartidos.
2. **Acceso a Internet:** todos los departamentos necesitan conexión para trabajar y atender a los clientes.
3. **Compartición de archivos:** espacio centralizado con permisos por departamento.
4. **Impresión:** impresora multifunción compartida en red.
5. **Cuentas de usuario:** cada trabajador tendrá una cuenta individual y permisos según sus funciones.
6. **Web corporativa:** página pública para presentar servicios y facilitar el contacto.
7. **Seguridad:** filtrado del tráfico, separación de redes, protección de equipos, actualizaciones y copias.
8. **Wi-Fi:** conexión corporativa y red de invitados separada de los recursos internos.

## 1.4. Fuentes
- Documentación del Bloque 1 de este repositorio: plantilla, departamentos, puestos y recursos TIC.
- Planteamiento de la práctica PI-Q.2.1, que solicita identificar necesidades de conectividad, Internet, archivos, impresión, cuentas, web y seguridad.
- Análisis del funcionamiento de una pequeña empresa de servicios informáticos. Las necesidades adicionales son decisiones de diseño del equipo, no datos de una empresa real.

## 1.5. Prioridades
Las prioridades son disponer de conectividad estable, cuentas individuales, almacenamiento compartido y copias de seguridad. Después se desplegarán la web corporativa en una zona separada y la red Wi-Fi de invitados. La solución debe poder ampliarse sin sustituir toda la infraestructura.
