# 2. Alternativas y estudio de viabilidad

## 2.1. Criterios
Se comparan alternativas teniendo en cuenta coste aproximado, facilidad de administración, seguridad, posibilidad de ampliación y conocimientos necesarios. Los importes son estimaciones iniciales, no presupuestos cerrados.

## 2.2. Comparación de alternativas

| Necesidad | Alternativa A | Alternativa B | Solución seleccionada |
|---|---|---|---|
| Archivos | NAS local, 365–850 € según modelo y capacidad | Almacenamiento cloud, aproximadamente 5–15 €/usuario/mes | NAS local para documentos y copia externa cifrada. |
| Servidores | Tres equipos físicos independientes | Dos hosts físicos con virtualización y un NAS para copias | Dos hosts virtualizables y NAS; servicios separados en máquinas virtuales. |
| Red | Switches no gestionables, económicos | Switches gestionables con VLAN y monitorización | Switches gestionables para separar usuarios, servidores, invitados y DMZ. |
| Seguridad | Router doméstico con funciones básicas | Firewall empresarial o dedicado | Firewall con VLAN, reglas, VPN y registro de eventos. |
| Web | Alojamiento externo | Servidor propio en DMZ | Alojamiento externo inicialmente por menor mantenimiento; DMZ preparada para el futuro. |
| Ofimática | Licencias comerciales por usuario | Suite libre como LibreOffice | Suite libre para reducir gastos, comprobando compatibilidad. |

## 2.3. Ventajas, limitaciones y requisitos

### Almacenamiento local y cloud
- **NAS local:** control de los datos y carpetas compartidas; requiere compra, mantenimiento y copia en otra ubicación.
- **Cloud:** acceso desde fuera y menor mantenimiento local; genera cuotas recurrentes y depende de Internet.
- **Decisión:** almacenamiento local con permisos y copia externa cifrada.

### Servidores físicos y virtualización
- **Equipos físicos separados:** sencillos de entender, pero aumentan coste, consumo y espacio.
- **Virtualización:** permite ejecutar servicios separados en dos equipos físicos; requiere conocimientos, copias de máquinas virtuales y hardware suficiente.
- **Decisión:** dos hosts físicos con virtualización y un NAS para copias. Las funciones de archivos, copias y pruebas/gestión siguen diferenciadas, pero no requieren necesariamente un servidor físico cada una.

### Red y seguridad
- **Switch no gestionable:** menor precio y configuración sencilla, pero no permite segmentar mediante VLAN.
- **Switch gestionable:** permite VLAN, controles y diagnóstico; necesita configuración y documentación.
- **Decisión:** switches gestionables y firewall con reglas entre redes.

### Web corporativa
- **Alojamiento externo:** menor trabajo de mantenimiento, a cambio de una cuota.
- **Servidor propio en DMZ:** mayor control, pero exige actualizaciones, monitorización y protección constante.
- **Decisión:** alojamiento externo al principio. La DMZ queda diseñada para un futuro servidor propio.

## 2.4. Aspecto innovador
La propuesta incorpora virtualización y segmentación mediante VLAN. La virtualización permite crear entornos de pruebas aislados para validar cambios antes de aplicarlos. Las VLAN separan usuarios, servidores, administración, impresoras, invitados y DMZ. Esto facilita la gestión y mejora el control de acceso.

## 2.5. Viabilidad

| Aspecto | Valoración | Justificación |
|---|---|---|
| Espacio físico | Viable, pendiente de comprobación | Servidores y red en armario o zona ventilada y restringida. |
| Conocimientos | Viable con formación | Sistemas y Redes cuenta con 3 personas; deben conocer VLAN, IP, virtualización, copias y firewall. |
| Equipamiento | Viable | Aprovecha los 12 puestos definidos y añade infraestructura de red y almacenamiento. |
| Económica | Condicionada | Requiere aprobación de Dirección, comparar proveedores y comprar por fases. |
| Mantenimiento | Viable | Se asignan actualizaciones, revisión de copias, monitorización y documentación. |

## 2.6. Conclusión
Se selecciona una solución híbrida y escalable: red gestionable segmentada, firewall, dos hosts de virtualización, NAS con copia externa y alojamiento web externo inicialmente. Es equilibrada para 12 personas si se confirma el presupuesto y se asigna tiempo de mantenimiento.

## 2.7. Fuentes
- [QNAP TS-464 – catálogo y precio de referencia en Senetic](https://www.senetic.es/).
- [TP-Link Omada – catálogo de switches en Mauser](https://mauser.es/informatica-y-telecomunicaciones/redes/tp-link-omada).
- [VirtualBox – documentación oficial](https://www.virtualbox.org/wiki/Documentation).
- [Proxmox VE – documentación oficial](https://pve.proxmox.com/pve-docs/).
