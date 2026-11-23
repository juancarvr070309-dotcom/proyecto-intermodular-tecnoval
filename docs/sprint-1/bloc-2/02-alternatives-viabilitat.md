# 2. Alternativas y estudio de viabilidad

## 2.1. Criterios de selección

Se comparan las alternativas según coste inicial y recurrente, seguridad, mantenimiento, posibilidad de ampliación y conocimientos necesarios. Una solución se considera seleccionada solo cuando el equipo confirma la decisión y se comprueban los requisitos técnicos y económicos.

## 2.2. Comparación de alternativas

| Necesidad | Alternativa A | Alternativa B | Decisión propuesta |
|---|---|---|---|
| Archivos compartidos | NAS local: inversión inicial y mantenimiento propio | Almacenamiento cloud: cuota por usuario y dependencia de Internet | NAS local para datos de trabajo, con copia externa independiente. |
| Servidores | Tres equipos físicos separados | Dos hosts físicos con virtualización | Dos hosts, siempre que el dimensionamiento y la compatibilidad se verifiquen antes de comprar. |
| Red | Switches no gestionables | Dos switches gestionables con VLAN | Dos switches gestionables de 24 puertos, con enlaces troncales 802.1Q. |
| Seguridad perimetral | Router básico | Firewall/router con VLAN, reglas, VPN y registros | Firewall dedicado o solución integrada que cumpla los requisitos y tenga actualizaciones. |
| Web corporativa | Servidor propio publicado desde la DMZ | Alojamiento web externo | **Alojamiento externo en la primera fase. No se instalará ni publicará un servidor web propio en la DMZ.** |
| Ofimática | Licencias comerciales por usuario | Suite libre | LibreOffice como opción inicial, validando compatibilidad con los documentos de clientes. |
| Correo | Servidor de correo propio | Servicio de correo gestionado | Correo gestionado externo con dominio propio y MFA; no se alojará correo en la DMZ. |

## 2.3. Decisión sobre la web y consenso del equipo

Para eliminar la contradicción entre documentos, la propuesta única para la primera fase es **contratar alojamiento web externo**. El proveedor alojará la web pública y gestionará la infraestructura del servicio. La empresa mantendrá el dominio y el contenido, revisará las cuentas de administración y activará HTTPS y MFA cuando el proveedor lo permita.

La DMZ queda reservada en el diseño para una posible ampliación futura, pero en la primera fase no tendrá un servidor web público propio. No se redirigirán puertos de Internet hacia un servidor web interno.

Esta decisión evita que el equipo de Sistemas y Redes tenga que mantener desde el inicio un servidor web expuesto, aplicar sus actualizaciones y vigilar sus registros. La opción propia en DMZ se podrá reconsiderar si existen necesidades de control, presupuesto y personal técnico para mantenerla.

**Registro de consenso (no marcar como aprobado hasta hablarlo entre los dos integrantes):**

| Punto que debe acordar el equipo | Propuesta | Juan Carlos | Isaac | Fecha / evidencia |
|---|---|---|---|---|
| Web de primera fase | Alojamiento externo; sin servidor web propio en DMZ | Pendiente de confirmar | Pendiente de confirmar | Añadir fecha y enlace/captura del acuerdo |
| Dos switches gestionables | Mantener dos unidades de 24 puertos | Pendiente de confirmar | Pendiente de confirmar | Añadir fecha y enlace/captura del acuerdo |
| NAS con cuatro discos | QNAP TS-464-8G + 4 discos NAS compatibles, sujeto a cotización | Pendiente de confirmar | Pendiente de confirmar | Añadir fecha y enlace/captura del acuerdo |

La tabla evidencia la decisión propuesta y permite documentar el consenso real. No se afirma que haya existido una votación o aprobación si no se ha realizado.

## 2.4. Ventajas, limitaciones y requisitos

### Almacenamiento local y cloud
- **NAS local:** control de los datos y carpetas compartidas; requiere discos, mantenimiento, protección eléctrica y copias fuera del propio NAS.
- **Cloud:** facilita el acceso remoto y reduce el mantenimiento local; genera cuotas recurrentes y depende de Internet.
- **Decisión propuesta:** NAS local para los datos de trabajo y copia adicional cifrada en una ubicación distinta. RAID no sustituye una copia de seguridad.

### Servidores físicos y virtualización
- **Equipos físicos separados:** aislamiento sencillo, pero más coste, consumo y espacio.
- **Virtualización:** consolida servicios en dos hosts; exige CPU compatible con virtualización, RAM suficiente, almacenamiento redundante, copias y procedimiento de recuperación.
- **Decisión propuesta:** dos hosts físicos y máquinas virtuales separadas. No se aprobará la compra hasta disponer de modelos y fichas técnicas concretas.

### Red y seguridad
- **Switch no gestionable:** económico, pero no permite crear ni administrar VLAN.
- **Switch gestionable:** permite VLAN 802.1Q, segmentación y diagnóstico; requiere configuración y mantenimiento.
- **Decisión propuesta:** dos switches gestionables, con VLAN y enlaces troncales, sujetos a comprobar puertos, alimentación PoE si fuera necesaria y velocidad de uplinks.

### Web y correo
- **Web:** alojamiento externo en la primera fase; no se desplegará servidor web en la DMZ.
- **Correo:** servicio gestionado externo con dominio propio, MFA y protección antispam. No se instalará un servidor SMTP propio en la primera fase.

## 2.5. Viabilidad técnica: condiciones que deben verificarse

| Elemento | Requisito mínimo de diseño | Verificación pendiente antes de compra |
|---|---|---|
| Cada host de virtualización | CPU x86-64 multinúcleo con Intel VT-x/VT-d o AMD-V/IOMMU; 32 GB RAM ECC si la plataforma lo admite (64 GB recomendado si el presupuesto lo permite); SSD de empresa y dos interfaces de red Gigabit como mínimo | Modelo exacto, CPU, RAM instalada/máxima, tipo de RAM, bahías, controladora, discos, NIC, fuente y garantía |
| Hipervisor | Compatibilidad del modelo de CPU, NIC, almacenamiento y controladora con la versión elegida de Proxmox VE | Consultar la documentación y probar instalación en el hardware exacto |
| NAS | QNAP TS-464-8G propuesto; 4 bahías SATA de 3,5 pulgadas, 8 GB DDR4 y dos puertos 2,5GbE | Confirmar revisión del producto, compatibilidad de los cuatro discos en la lista oficial y cotización de discos |
| Switches | Dos TP-Link TL-SG3428 propuestos, 24 puertos Gigabit y gestión VLAN 802.1Q | Confirmar firmware, funciones L2 necesarias, uplinks, transceptores/cables y presupuesto |
| Firewall | VLAN, NAT, reglas entre zonas, VPN, registros y actualizaciones de seguridad | Modelo exacto, rendimiento con inspección activada, licencias y soporte |
| SAI | Potencia en W superior a la carga medida, margen de crecimiento y autonomía de apagado | Medir consumo real y consultar curva de autonomía del modelo; comprobar USB/SNMP y compatibilidad de apagado |

Los requisitos anteriores son criterios de compra, no características verificadas de equipos ya adquiridos. La compatibilidad definitiva queda pendiente hasta seleccionar modelos exactos.

## 2.6. Viabilidad económica y mantenimiento

La inversión no se considera cerrada. El presupuesto debe incluir los dos hosts, los discos internos del NAS, firewall, switches, puntos de acceso, cableado, SAI, instalación, transporte, garantías y servicios recurrentes. También se debe prever el coste anual de dominio, alojamiento web, correo, soporte, protección de endpoints y mantenimiento.

La implantación se realizará por fases, pero no se dará por viable económicamente hasta obtener ofertas comparables y calcular el coste total del primer año y de los años siguientes.

## 2.7. Conclusión

La solución propuesta para la primera fase es: dos hosts virtualizados, NAS de cuatro bahías con discos NAS, dos switches gestionables, firewall, Wi-Fi separado, correo gestionado y web alojada externamente. La DMZ se mantiene en el diseño para futuras necesidades, pero no alojará una web propia en esta fase. La aprobación final depende del consenso documentado, la comprobación de compatibilidad y las cotizaciones.

## 2.8. Fuentes técnicas

- [QNAP TS-464 – especificaciones oficiales](https://www.qnap.com/es-es/product/ts-464/specs/hardware/1000).
- [QNAP – compatibilidad de discos](https://www.qnap.com/compatibility/).
- [Seagate IronWolf – gama de discos NAS](https://www.seagate.com/es/es/support/internal-hard-drives/nas-drives/ironwolf/).
- [TP-Link TL-SG3428 – ficha del fabricante](https://www.tp-link.com/es/business-networking/omada-switch-smart/tl-sg3428/).
- [Proxmox VE – documentación oficial](https://pve.proxmox.com/pve-docs/).
- [VirtualBox – documentación oficial](https://www.virtualbox.org/wiki/Documentation).
