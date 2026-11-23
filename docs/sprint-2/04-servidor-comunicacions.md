# 4. Servidor de comunicaciones y enrutamiento

## 4.1. Función

`TV-COMMS` es una máquina virtual con Ubuntu Server 26.04.1 LTS que actúa como enrutador entre la LAN (`192.168.10.0/24`) y la DMZ (`192.168.30.0/24`). También proporciona salida a Internet mediante el adaptador NAT de VirtualBox y alojará el servicio DHCP de la LAN.

## 4.2. Interfaces

La máquina debe tener tres adaptadores. Los nombres de las interfaces Linux pueden variar; no se debe copiar un nombre de interfaz sin comprobarlo.

| Función | Red VirtualBox | IP prevista |
|---|---|---|
| Exterior | NAT | Automática |
| LAN | TecnoVal-LAN | 192.168.10.1/24 |
| DMZ | TecnoVal-DMZ | 192.168.30.1/24 |

Identificar las interfaces con:
```bash
ip -br link
ip -br address
```

Anotar qué nombre corresponde a NAT, LAN y DMZ antes de modificar ningún archivo de red.

## 4.3. Configurar las IP internas

Configurar las interfaces LAN y DMZ con IP fijas mediante Netplan, que es la herramienta habitual de Ubuntu Server. Antes de editar, identificar las interfaces y revisar la configuración existente de `/etc/netplan/`. No se deben configurar dos gestores a la vez para las mismas interfaces.

Valores:
- Interfaz LAN: `192.168.10.1/24`.
- Interfaz DMZ: `192.168.30.1/24`.
- Interfaz exterior: DHCP de VirtualBox NAT.

Después, comprobar:
```bash
ip -br address
ip route
```

La ruta predeterminada debe salir por la interfaz exterior. Las redes conectadas `192.168.10.0/24` y `192.168.30.0/24` deben aparecer como rutas directamente conectadas.

## 4.4. Activar el reenvío IPv4 de forma persistente

Crear el archivo `/etc/sysctl.d/99-tecnoval-router.conf` con este contenido:

```ini
net.ipv4.ip_forward=1
```

Aplicar y comprobar:
```bash
sudo sysctl --system
sysctl net.ipv4.ip_forward
```

El resultado esperado es `net.ipv4.ip_forward = 1`. Después de reiniciar, volver a ejecutar el comando para comprobar que sigue activado.

## 4.5. Salida a Internet mediante NAT

Para que la LAN y la DMZ puedan salir a Internet a través de TV-COMMS, hay que configurar el enrutamiento y la traducción de direcciones (masquerade) desde las redes internas hacia la interfaz exterior. La configuración concreta de las reglas dependerá del sistema de cortafuegos autorizado por el profesorado. Documentar las reglas aplicadas y no desactivar el cortafuegos como solución general.

Antes de configurarlas, identificar la interfaz exterior real con `ip route`. No inventar su nombre.

## 4.6. Pruebas

Desde TV-COMMS:
```bash
ip -br address
ip route
sysctl net.ipv4.ip_forward
ping -c 4 192.168.10.10
ping -c 4 192.168.30.10
```

Las dos últimas pruebas se realizarán cuando los servidores correspondientes estén configurados y respondan a ICMP. También hay que comprobar la puerta de enlace exterior asignada por VirtualBox:
```bash
ip route show default
```

Después de reiniciar TV-COMMS, repetir las comprobaciones de interfaces, rutas y reenvío.

## 4.7. Evidencias necesarias

Guardar capturas reales en `img/sprint-2/`:
- `07-comms-interficies.png`: `ip -br address`.
- `08-comms-rutes.png`: `ip route`.
- `09-comms-forwarding.png`: valor 1 de `net.ipv4.ip_forward`.
- `10-comms-reinici.png`: comprobación después de reiniciar.

Añadir aquí las capturas cuando se realicen. No se afirmará que el enrutamiento está operativo hasta que las pruebas den el resultado esperado.
