# 6. Presupuesto estimado

## 6.1. Criterios
El presupuesto es una estimación académica basada en precios consultados en tiendas y catálogos online. Los importes pueden cambiar según disponibilidad, configuración, envío y proveedor. Para los equipos sin precio público comparable se indica que es una estimación pendiente de presupuesto formal.

Se muestran importes con IVA incluido cuando la fuente lo indica. Para partidas estimadas se aplica un IVA del 21% como hipótesis de cálculo para una compra ordinaria en la península; se debe confirmar el tratamiento fiscal en la factura del proveedor.

## 6.2. Hardware y red

| Elemento | Cantidad | Precio unitario (IVA incl.) | Subtotal (IVA incl.) | Fuente / observación |
|---|---:|---:|---:|---|
| PC profesional NTT ProDesk i5, 16 GB RAM, SSD 512 GB, Windows 11 Pro | 12 | 798,02 € | 9.576,24 € | [DistriNode](https://distrinode.es/ntt-prodesk-ordenador-de-sobremesa-intel-core-i5-14400-16gb-ram-512gb-ssd-wi-fi-windows-11-pro-zko-i5h610ddr5-h01p). Precio consultado. |
| Portátil profesional de reserva | 1 | 850,00 € | 850,00 € | Estimación; solicitar presupuesto. |
| Host físico para virtualización | 2 | 1.700,00 € | 3.400,00 € | Estimación para equipo ampliable con 32–64 GB RAM; solicitar presupuesto. |
| NAS QNAP TS-464-8G | 1 | 841,28 € | 841,28 € | [Senetic](https://www.senetic.es/). Precio de referencia mostrado con IVA. |
| Switch TP-Link TL-SG3428 gestionable | 2 | 239,70 € | 479,40 € | [Mauser](https://mauser.es/informatica-y-telecomunicaciones/redes/tp-link-omada). Precio consultado. |
| Firewall/router empresarial | 1 | 450,00 € | 450,00 € | Estimación; solicitar presupuesto. |
| Punto de acceso Wi-Fi 6 | 2 | 110,00 € | 220,00 € | Estimación por unidad; confirmar modelo. |
| Impresora multifunción de red | 1 | 250,00 € | 250,00 € | Estimación; confirmar consumibles. |
| Discos externos para copia | 2 | 130,00 € | 260,00 € | Estimación por unidad, capacidad orientativa 4 TB. |
| SAI para equipos críticos | 2 | 220,00 € | 440,00 € | Estimación; dimensionar según consumo. |
| Cableado, paneles, tomas y accesorios | 1 lote | 400,00 € | 400,00 € | Estimación; requiere medir oficina y pedir instalación. |
| **Subtotal hardware** | | | **17.166,92 €** | |

## 6.3. Software y servicios

| Elemento | Cantidad | Precio unitario | Subtotal | Fuente / observación |
|---|---:|---:|---:|---|
| LibreOffice | 12 usuarios | 0,00 € | 0,00 € | Software libre; comprobar compatibilidad. |
| Proxmox VE, edición sin suscripción | 1 plataforma | 0,00 € | 0,00 € | [Proxmox](https://www.proxmox.com/en/proxmox-virtual-environment/pricing). Valorar soporte si se necesita. |
| Sistema de incidencias y soporte remoto | 1 solución inicial | 0,00 € | 0,00 € | Se estudiará herramienta libre; cotizar licencias comerciales si fueran necesarias. |
| Dominio y alojamiento web | 1 año | 150,00 € | 150,00 € | Estimación anual, pendiente de proveedor. |
| Correo corporativo | 12 cuentas | 0,00 € | 0,00 € | Se supone incluido en solución existente o libre; añadir cuota si se contrata servicio comercial. |
| **Subtotal software y servicios** | | | **150,00 €** | |

## 6.4. Resumen económico

| Concepto | Importe |
|---|---:|
| Subtotal hardware | 17.166,92 € |
| Subtotal software y servicios | 150,00 € |
| **Subtotal antes de contingencia** | **17.316,92 €** |
| Reserva para imprevistos (10%) | 1.731,69 € |
| **TOTAL ESTIMADO** | **19.048,61 €** |

Los precios publicados ya incluyen IVA cuando la tienda lo especifica. Las partidas estimadas se han expresado como importes finales orientativos con IVA incluido para facilitar la comparación. Antes de comprar se debe solicitar presupuesto desglosado con base imponible, IVA, transporte, instalación y garantía.

## 6.5. Justificación económica y viabilidad por fases
El total de 19.048,61 € es una estimación de inversión inicial, no una compra aprobada. La empresa ficticia tiene 12 trabajadores, pero no se ha definido una facturación, beneficio ni tesorería real; por tanto, no sería correcto afirmar que puede pagar todo el importe de una sola vez. La viabilidad económica queda condicionada a la aprobación de Dirección, a comparar ofertas y a confirmar el presupuesto disponible.

Se propone implantar por fases para repartir la inversión y priorizar la continuidad del negocio:

1. **Fase prioritaria:** firewall/router, switches gestionables, cableado esencial y puestos que realmente necesiten renovación. Confirmar primero el inventario del Bloque 1 para evitar comprar ordenadores duplicados.
2. **Fase de servicios y protección:** hosts de virtualización, NAS, SAI y solución de copias; realizar pruebas de restauración antes de considerar el servicio operativo.
3. **Fase de ampliación:** puntos de acceso, equipo de reserva, mejoras de seguridad y servicios opcionales, según necesidad y presupuesto aprobado.

La compra por fases puede reducir el desembolso inmediato, pero no reduce por sí misma el coste total estimado. Cada fase debe contar con financiación y revisión de precios.

- Los 12 ordenadores corresponden a los 12 trabajadores definidos en el Bloque 1.
- El portátil adicional es de reserva y no sustituye ningún puesto fijo.
- Los dos hosts permiten virtualizar archivos, pruebas y gestión; el NAS se dedica a copias.
- Los dos switches permiten conectar puestos y servidores y crear VLAN.
- El firewall controla el tráfico entre Internet, red interna y DMZ.
- Los puntos de acceso y la impresora son recursos compartidos.
- Se prioriza software libre para reducir gastos recurrentes.
- La reserva del 10% cubre variaciones de precio, accesorios o necesidades detectadas.

## 6.6. Límites
No se incluye personal, electricidad, mantenimiento anual, contratación de Internet, licencias comerciales opcionales, ampliación de discos del NAS ni instalación profesional del cableado. Tampoco se ha recibido una oferta formal para hosts, firewall, puntos de acceso, impresora, SAI y accesorios. El total sirve para valorar la viabilidad, no como orden de compra.

## 6.7. Fuentes de precios
- [DistriNode – NTT ProDesk i5 16 GB / 512 GB / Windows 11 Pro](https://distrinode.es/ntt-prodesk-ordenador-de-sobremesa-intel-core-i5-14400-16gb-ram-512gb-ssd-wi-fi-windows-11-pro-zko-i5h610ddr5-h01p).
- [Senetic – catálogo de NAS QNAP y Synology](https://www.senetic.es/).
- [Mauser – catálogo TP-Link Omada y switches gestionables](https://mauser.es/informatica-y-telecomunicaciones/redes/tp-link-omada).
- [Proxmox VE – opciones de suscripción](https://www.proxmox.com/en/proxmox-virtual-environment/pricing).
- [LibreOffice – descarga y licencias](https://www.libreoffice.org/).
