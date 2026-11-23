# 5. Instalación y configuración del servicio DHCP

## 5.1. Objetivo

El servidor de comunicaciones `TV-COMMS` asignará automáticamente la configuración IP a los dos clientes de la LAN: `TV-CLIENT-WIN` y `TV-CLIENT-LINUX`.

DHCP solo escuchará en la interfaz LAN. No se activará en el adaptador exterior ni en la DMZ. Los servidores conservarán direcciones fijas.

## 5.2. Parámetros del servicio

| Parámetro | Valor |
|---|---|
| Red | 192.168.10.0/24 |
| Máscara | 255.255.255.0 |
| Rango dinámico | 192.168.10.100–192.168.10.150 |
| Puerta de enlace | 192.168.10.1 |
| IP fijas reservadas | 192.168.10.1 (TV-COMMS), 192.168.10.10 (TV-SRVINT) |
| Tiempo de concesión | 12 horas |
| Interfaz de escucha | Interfaz LAN de TV-COMMS |
| DNS anunciado | Ninguno en este sprint; el DNS corporativo se configura en el Sprint 3 |

El rango DHCP no incluye las IP fijas. Para los dos clientes hay suficientes direcciones disponibles.

## 5.3. Servicio propuesto

En Ubuntu Server 26.04.1 LTS se propone `dnsmasq` utilizado solo como servidor DHCP, con la función DNS desactivada. Antes de instalarlo, comprobar que el nombre de la interfaz LAN es correcto.

Ejemplo de configuración orientativa para `/etc/dnsmasq.d/tecnoval-dhcp.conf` (sustituir `INTERFICIE_LAN` por el nombre real):

```ini
port=0
interface=INTERFICIE_LAN
bind-interfaces
dhcp-authoritative
dhcp-range=192.168.10.100,192.168.10.150,255.255.255.0,12h
dhcp-option=option:router,192.168.10.1
dhcp-leasefile=/var/lib/misc/dnsmasq.leases
```

La configuración no anuncia DNS porque en este sprint no se ha desplegado el DNS corporativo y el PDF indica que no se exige la resolución de nombres. Si el profesorado solicita un DNS accesible, hay que acordar cuál se utilizará antes de añadir la opción correspondiente.

Después de instalar y configurar el servicio, comprobar la sintaxis y el estado con los comandos adecuados a la versión instalada. No dejar el servicio escuchando en el exterior ni en la DMZ.

## 5.4. Configuración de los clientes

**Windows (TV-CLIENT-WIN):**
1. Abrir las propiedades del adaptador Ethernet.
2. Seleccionar la obtención automática de la dirección IP.
3. Seleccionar la obtención automática de DNS (no se espera DNS corporativo en este sprint).
4. Abrir el terminal y ejecutar:

```powershell
ipconfig /release
ipconfig /renew
ipconfig /all
```

**Linux (TV-CLIENT-LINUX):**
1. Configurar la conexión cableada para que IPv4 utilice DHCP automáticamente.
2. Desconectar y volver a conectar la conexión o renovarla desde el gestor de red.
3. Consultar:

```bash
ip -br address
ip route
nmcli device show
```

Los dos clientes deben recibir una IP entre `192.168.10.100` y `192.168.10.150`, máscara /24 y puerta de enlace `192.168.10.1`.

## 5.5. Revisión de concesiones

Consultar el archivo de concesiones configurado en dnsmasq:
```bash
sudo cat /var/lib/misc/dnsmasq.leases
```

Deben aparecer las concesiones de los dos clientes con su IP y MAC. Si el archivo no existe o está vacío, comprobar que los clientes han solicitado DHCP y que el servicio escucha en la interfaz LAN correcta.

## 5.6. Evidencias

Guardar capturas reales:
- `11-dhcp-config.png`: archivo de configuración sin datos sensibles.
- `12-dhcp-status.png`: estado del servicio.
- `13-dhcp-leases.png`: concesiones de los dos clientes.
- `14-client-win-dhcp.png`: `ipconfig /all` del cliente Windows.
- `15-client-linux-dhcp.png`: `ip -br address` e `ip route` del cliente Linux.

No se debe dar por completado DHCP hasta que los dos clientes obtengan los datos correctos y aparezcan sus concesiones en el servidor.
