# 5. Recursos necesarios

## 5.1. Hardware

Las cantidades se ajustan a los 12 trabajadores y a los servicios definidos. Los modelos indicados son propuestas para comparar, no equipos comprados ni compatibilidad ya certificada.

| Recurso | Cantidad | Requisitos de diseño y propuesta | Justificación / comprobación |
|---|---:|---|---|
| Ordenadores profesionales | 12 | CPU actual de oficina, 16 GB RAM, SSD 512 GB, Ethernet Gigabit | Uno por trabajador. Revisar inventario antes de comprar para no duplicar equipos que ya existan. |
| Portátil de reserva | 1 | 16 GB RAM, SSD 512 GB y Wi-Fi | Sustitución temporal y movilidad. |
| Hosts de virtualización | 2 | Cada host: CPU x86-64 multinúcleo con Intel VT-x/VT-d o AMD-V/IOMMU; 32 GB RAM como mínimo de diseño (64 GB recomendado); almacenamiento SSD redundante; dos interfaces de red Gigabit como mínimo | Ejecutar máquinas virtuales separadas y permitir mantenimiento. Antes de elegir, comprobar modelo de CPU, RAM máxima/tipo, ranuras, controladora, discos, NIC, fuente, garantía y compatibilidad con Proxmox VE. |
| Hipervisor | 1 plataforma | Proxmox VE, versión compatible con el hardware seleccionado | La compatibilidad de CPU, NIC y almacenamiento debe comprobarse en el equipo real. |
| NAS | 1 | QNAP TS-464-8G propuesto: 4 bahías SATA de 3,5", 8 GB DDR4 y dos puertos 2,5GbE | El fabricante indica que se entrega sin discos. Es imprescindible presupuestar las unidades internas por separado. |
| Discos internos NAS | 4 | Propuesta: 4 × Seagate IronWolf 8 TB SATA (modelo ST8000VN004), solo si aparece en la lista de compatibilidad vigente de QNAP | RAID 6: capacidad nominal útil aproximada de 16 TB decimales antes de formato y sobrecarga (dos discos equivalentes se destinan a paridad). Confirmar compatibilidad exacta, precio y disponibilidad. |
| Switch gestionable principal | 1 | TP-Link TL-SG3428 propuesto; 24 puertos Gigabit y gestión VLAN 802.1Q | Conecta firewall, hosts, NAS y switch de acceso. Verificar versión de hardware/firmware y uplinks. |
| Switch gestionable de acceso | 1 | Segundo TP-Link TL-SG3428 propuesto | Conecta puestos, impresora y puntos de acceso. Los enlaces entre switches transportarán las VLAN necesarias. |
| Firewall/router | 1 | Solución con VLAN, NAT, reglas entre zonas, VPN, registros y actualizaciones | Seleccionar modelo exacto y verificar rendimiento con las funciones de seguridad activadas, soporte y coste de licencias. |
| Punto de acceso Wi-Fi | 2 | Wi-Fi 6, SSID corporativo e invitados y asignación a VLAN | Comprobar si requieren PoE. El TL-SG3428 propuesto no debe darse por supuesto como PoE; presupuestar inyectores o alimentación si son necesarios. |
| Impresora multifunción | 1 | Ethernet e impresión en red | Recurso compartido; comprobar coste de tóner/tinta y mantenimiento. |
| Discos externos | 2 | Unidades cifrables, capacidad dimensionada según los datos protegidos | Copia adicional desconectada/rotatoria. No mantener siempre conectadas ambas copias. |
| SAI | 2 | Propuesta de comparar unidades de 1500 VA; potencia en W, autonomía y comunicación USB/SNMP según carga real | Medir consumo de cada grupo (host, NAS, switches y firewall). Elegir SAI con potencia en W superior a la carga medida y autonomía suficiente para apagado ordenado. No comprar solo por el valor VA. |
| Cableado y accesorios | 1 lote | Cat 6, panel de parcheo, tomas, latiguillos, etiquetado y transceptores si fueran necesarios | Requiere plano, medición de distancias y presupuesto de instalación. |

### Capacidad y protección del NAS

El QNAP TS-464 dispone de cuatro bahías SATA y se comercializa sin discos. La propuesta de cuatro discos de 8 TB en RAID 6 ofrece aproximadamente 16 TB decimales antes de formato y espacio reservado. La capacidad final visible será inferior. RAID mejora la tolerancia a fallos de discos, pero **no sustituye** una copia de seguridad externa.

Antes de comprar:
1. Comprobar que el modelo exacto de disco figura en la lista oficial de compatibilidad de QNAP.
2. Confirmar que los cuatro discos son del mismo modelo y capacidad.
3. Presupuestar cuatro discos, no solo la carcasa NAS.
4. Definir carpetas, permisos, snapshots y alertas.
5. Mantener una copia cifrada fuera del NAS y probar restauraciones.

## 5.2. Software, seguridad y servicios

| Software o servicio | Cantidad | Función y decisión de primera fase |
|---|---:|---|
| Sistema operativo de escritorio | 12 | Edición profesional con soporte y actualizaciones. |
| Suite ofimática | 12 usuarios | LibreOffice como alternativa sin coste de licencia; validar compatibilidad con formatos de clientes. |
| Plataforma de virtualización | 1 | Proxmox VE; valorar soporte de pago si se necesita asistencia del fabricante. |
| Firewall | 1 solución | Firewall/router con reglas por VLAN, NAT, VPN, registros y actualizaciones. |
| Protección de endpoints | 12 | Solución centralizada antimalware/EDR, políticas, alertas y actualizaciones. No basta con instalar un antivirus sin administración. |
| Gestión de identidades | 12 usuarios | Cuentas individuales, privilegio mínimo y MFA cuando esté disponible; Active Directory queda para una fase posterior. |
| Copias de seguridad | 1 solución | Copias programadas de VM y datos al NAS, copia externa cifrada y pruebas documentadas de restauración. |
| Correo corporativo | 12 cuentas | Servicio gestionado externo con dominio propio, MFA, antispam y protección contra suplantación (SPF, DKIM y DMARC). |
| Alojamiento web y dominio | 1 servicio | Alojamiento externo en primera fase; HTTPS y MFA para administración. No se publica servidor propio en la DMZ. |
| Sistema de incidencias | 7 accesos | Registro, asignación y seguimiento para cinco técnicos y dos personas de administración. |
| Soporte remoto | 5 accesos | Herramienta autorizada, con consentimiento del cliente y registro de las sesiones. |

## 5.3. Equipo de implantación y responsabilidades

El equipo de implantación está formado por los dos integrantes del proyecto; no debe confundirse con los 12 puestos de la empresa ficticia.

| Responsable propuesto | Responsabilidades principales | Evidencia |
|---|---|---|
| Juan Carlos Vasconez Rojas | Coordinación del calendario, documentación, inventario de evidencias, pruebas de aceptación y revisión de Trello | Actualizaciones de documentos, capturas y tarjetas asignadas |
| Isaac Matias Beltran Moreno | Diseño y configuración de red, hosts, virtualización, servidores y servicios de infraestructura | Diagrama, configuraciones, pruebas técnicas y tarjetas asignadas |
| Ambos | Aprobar decisiones, revisar compatibilidad y presupuesto, validar cambios y preparar la entrega | Acuerdo registrado, revisión cruzada y commits |

Este reparto es una propuesta de organización. Cada integrante debe confirmar las responsabilidades y asignarse las tarjetas correspondientes en Trello; no se debe presentar como acuerdo cerrado hasta hacerlo.

## 5.4. Justificación y fuentes técnicas

La selección cubre puestos de trabajo, conectividad, virtualización, almacenamiento, protección eléctrica y servicios. Los modelos concretos deben pasar una revisión de compatibilidad y cotización antes de su compra.

- [QNAP TS-464 – especificaciones oficiales](https://www.qnap.com/es-es/product/ts-464/specs/hardware/1000): CPU, memoria, cuatro bahías y puertos de red; el fabricante indica que los discos se venden por separado.
- [QNAP – lista de compatibilidad de discos](https://www.qnap.com/compatibility/).
- [Seagate IronWolf – gama y modelos NAS](https://www.seagate.com/es/es/support/internal-hard-drives/nas-drives/ironwolf/).
- [TP-Link TL-SG3428 – ficha oficial](https://www.tp-link.com/es/business-networking/omada-switch-smart/tl-sg3428/).
- [Proxmox VE – documentación oficial](https://pve.proxmox.com/pve-docs/).
- [Eaton – documentación de SAI](https://www.eaton.com/).
