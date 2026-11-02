# 4. Plan de direccionamiento IP

## 4.1. Criterios
Se utiliza direccionamiento IPv4 privado dentro del rango 192.168.0.0/16. Cada zona dispone de una subred diferente para facilitar la administración y aplicar reglas de seguridad. Las direcciones son una propuesta de diseño, no una configuración ya instalada.

## 4.2. Tabla de subredes

| Zona / equipos | Red | Máscara / prefijo | Gateway | Rango previsto / ejemplos |
|---|---|---|---|---|
| Usuarios y departamentos (VLAN 10) | 192.168.10.0 | 255.255.255.0 (/24) | 192.168.10.1 | DHCP 192.168.10.50–192.168.10.199 |
| Servidores internos (VLAN 20) | 192.168.20.0 | 255.255.255.0 (/24) | 192.168.20.1 | Servidor de comunicaciones 192.168.20.10; VM archivos 192.168.20.11; VM gestión/pruebas 192.168.20.12; otras estáticas 192.168.20.13–192.168.20.49 |
| DMZ (VLAN 30) | 192.168.30.0 | 255.255.255.0 (/24) | 192.168.30.1 | Servidor web 192.168.30.10 |
| Gestión de red (VLAN 40) | 192.168.40.0 | 255.255.255.0 (/24) | 192.168.40.1 | Gestión 192.168.40.10–192.168.40.49 |
| Impresoras (VLAN 50) | 192.168.50.0 | 255.255.255.0 (/24) | 192.168.50.1 | Impresora 192.168.50.10 |
| Wi-Fi invitados (VLAN 60) | 192.168.60.0 | 255.255.255.0 (/24) | 192.168.60.1 | DHCP 192.168.60.50–192.168.60.220 |

## 4.3. Asignación
- Las puertas de enlace terminan en .1 en cada subred.
- Servidores, switches, puntos de acceso e impresora tendrán direcciones reservadas o estáticas fuera de los rangos DHCP. El servidor lógico de comunicaciones se reserva en 192.168.20.10; los servicios adicionales tendrán direcciones documentadas en el inventario.
- La asignación propuesta no implica que los servicios estén instalados todavía; deberá comprobarse antes de desplegarlos.
- Los ordenadores recibirán dirección por DHCP.
- La red de invitados solo tendrá acceso a Internet.
- La DMZ no tendrá acceso libre a las redes internas.
- Los dispositivos de gestión solo serán administrables desde equipos autorizados.

## 4.4. Justificación
La separación entre red interna y DMZ limita el impacto de un problema en un servicio público. La red de servidores protege los recursos compartidos; la red de gestión restringe el acceso administrativo; y la red de invitados evita que dispositivos externos se comuniquen con los equipos de la empresa. La VLAN de impresoras permite limitar quién puede utilizar y administrar el dispositivo.

## 4.5. Comprobación
Las seis redes utilizan /24 y tienen distintos terceros octetos: 10, 20, 30, 40, 50 y 60. Por tanto, no se solapan. La dirección de red termina en .0 y el broadcast en .255; no se asignan a equipos. Las puertas de enlace .1 son diferentes en cada VLAN.

Para evitar duplicados, las direcciones estáticas se documentarán y excluirán de los rangos DHCP. Antes de poner la red en funcionamiento se comprobarán las concesiones DHCP y la conectividad entre VLAN según las reglas definidas.

## 4.6. Fuentes
- [RFC 1918 – Address Allocation for Private Internets](https://www.rfc-editor.org/rfc/rfc1918).
- [RFC 2131 – Dynamic Host Configuration Protocol](https://www.rfc-editor.org/rfc/rfc2131).
