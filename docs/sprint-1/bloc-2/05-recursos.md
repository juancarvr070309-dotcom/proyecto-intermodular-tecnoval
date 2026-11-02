# 5. Recursos necesarios

## 5.1. Hardware

Las cantidades se ajustan a los 12 trabajadores y a los recursos definidos en el Bloque 1. Los tres servicios de servidor se mantienen como funciones diferenciadas, aunque pueden ejecutarse como máquinas virtuales sobre dos hosts físicos y un NAS para copias.

| Recurso | Cantidad | Función | Requisitos principales | Justificación |
|---|---:|---|---|---|
| Ordenadores profesionales | 12 | Puestos de trabajo | CPU de oficina actual, 16 GB RAM, SSD 512 GB, Ethernet Gigabit | Uno por trabajador. |
| Portátil de reserva | 1 | Sustitución y movilidad | 16 GB RAM, SSD 512 GB y Wi-Fi | Sustitución temporal. |
| Hosts de virtualización | 2 | Ejecutar máquinas virtuales | CPU multinúcleo, 32–64 GB RAM ampliables, SSD y red Gigabit | Separar servicios y facilitar recuperación. |
| NAS para copias | 1 | Copias de seguridad | RAID, discos NAS, snapshots y acceso restringido | Centraliza copias. |
| Switch gestionable 24 puertos | 2 | Conectar puestos y servidores | Gigabit, VLAN 802.1Q, QoS y gestión | Segmentación y ampliación. |
| Firewall/router | 1 | Internet y seguridad perimetral | VLAN, reglas, VPN, registros y actualizaciones | Controla el tráfico. |
| Punto de acceso Wi-Fi | 2 | Wi-Fi corporativo e invitados | Wi-Fi 6, VLAN/SSID y WPA2/WPA3 | Cobertura inalámbrica separada. |
| Impresora multifunción | 1 | Impresión y escaneo | Ethernet e impresión en red | Recurso compartido. |
| Discos externos | 2 | Copia adicional | Capacidad adecuada y cifrado | Copia independiente del NAS. |
| SAI | 2 | Protección eléctrica | Capacidad adecuada y apagado controlado | Respuesta ante cortes eléctricos. |
| Cableado y accesorios | Según instalación | Conexión de dispositivos | Cat 6, panel de parcheo y tomas | Instalación ordenada. |

## 5.2. Software y servicios

| Software o servicio | Cantidad | Función | Requisitos / decisión |
|---|---:|---|---|
| Sistema operativo de escritorio | 12 | Uso de los puestos | Edición profesional prevista para los equipos. |
| Suite ofimática | 12 usuarios | Documentos y hojas de cálculo | LibreOffice para reducir costes; comprobar compatibilidad. |
| Plataforma de virtualización | 1 | Ejecutar máquinas virtuales | Proxmox VE como opción, sujeto a formación. |
| Firewall | 1 solución | Filtrado y segmentación | Actualizaciones y soporte. |
| Protección de endpoints | 12 | Protección de los puestos | Solución gestionada y actualizada. |
| Copias de seguridad | 1 solución | Programación y verificación | Copias automáticas y pruebas de restauración. |
| Sistema de incidencias | 7 accesos | Registrar y asignar solicitudes | Cinco técnicos y dos personas de administración. |
| Soporte remoto | 5 accesos | Atender a clientes | Con autorización del cliente y registro. |
| Correo corporativo | 12 cuentas | Comunicación | Dominio de empresa y MFA cuando esté disponible. |
| Alojamiento web y dominio | 1 servicio | Publicar la web | Preferentemente externo al inicio. |

## 5.3. Equipo de implantación y responsabilidades

El equipo de implantación planifica y ejecuta el proyecto. No debe confundirse con toda la plantilla habitual de la empresa.

| Rol | Persona propuesta | Responsabilidades |
|---|---|---|
| Coordinación del proyecto | Juan Carlos Vasconez Rojas | Organizar tareas, revisar entregables, controlar fechas y coordinar. |
| Responsable de redes | Isaac Matias Beltran Moreno | Diseñar topología, VLAN, direccionamiento IP y reglas. |
| Responsable de sistemas | Integrante del equipo técnico | Proponer servidores, virtualización, usuarios y almacenamiento. |
| Responsable de seguridad y pruebas | Integrante del equipo técnico | Revisar permisos, firewall, copias y pruebas. |
| Documentación | Ambos integrantes | Mantener documentos, fuentes, decisiones y evidencias. |

Los roles técnicos adicionales son funciones asignables dentro del equipo del proyecto; no representan nuevas contrataciones ni alteran la plantilla ficticia de 12 empleados.

## 5.4. Justificación
La selección cubre los puestos existentes, conectividad, servicios internos y seguridad. Se priorizan tecnologías gestionables y soluciones ampliables. Las licencias comerciales se contratarán únicamente cuando sean necesarias y se incorporarán al presupuesto definitivo.
