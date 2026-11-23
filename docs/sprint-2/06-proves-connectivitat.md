# 6. Pruebas de conectividad y validación

## 6.1. Objetivo

Comprobar que las cinco máquinas arrancan, que las IP coinciden con el plan, que los clientes reciben DHCP y que TV-COMMS enruta el tráfico entre la LAN y la DMZ. Las pruebas se realizan por IP porque el DNS corporativo corresponde al Sprint 3.

## 6.2. Tabla de pruebas

Los resultados obtenidos y los enlaces a las capturas deben completarse después de realizar cada prueba. No se han inventado resultados.

| Núm. | Origen / equipo | Destino o comprobación | Procedimiento | Resultado esperado | Resultado obtenido | Evidencia |
|---:|---|---|---|---|---|---|
| 1 | Las cinco VM | Arranque e inicio de sesión | `hostname` y `whoami` (Linux/Windows) | Todas arrancan y muestran el nombre correcto | Pendiente | `img/sprint-2/` |
| 2 | TV-COMMS | Interfaces y rutas | `ip -br address` y `ip route` | Tres interfaces; rutas LAN/DMZ y ruta predeterminada exterior | Pendiente | `07-comms-interficies.png`, `08-comms-rutes.png` |
| 3 | TV-COMMS | Reenvío IPv4 | `sysctl net.ipv4.ip_forward` | Valor 1, también después de reiniciar | Pendiente | `09-comms-forwarding.png` |
| 4 | TV-CLIENT-WIN | DHCP | `ipconfig /release`, `ipconfig /renew`, `ipconfig /all` | IP del rango, máscara /24 y puerta de enlace .1 | Pendiente | `14-client-win-dhcp.png` |
| 5 | TV-CLIENT-LINUX | DHCP | `ip -br address`, `ip route`, `nmcli device show` | IP del rango, máscara /24 y puerta de enlace .1 | Pendiente | `15-client-linux-dhcp.png` |
| 6 | TV-COMMS | Concesiones DHCP | Consultar `/var/lib/misc/dnsmasq.leases` | Aparecen los dos clientes con su IP y MAC | Pendiente | `13-dhcp-leases.png` |
| 7 | Cliente LAN | TV-SRVINT (192.168.10.10) | `ping 192.168.10.10` | Respuesta por IP | Pendiente | Captura del ping |
| 8 | Cliente LAN | TV-COMMS LAN (192.168.10.1) | `ping 192.168.10.1` | Respuesta por IP | Pendiente | Captura del ping |
| 9 | TV-DMZ | TV-COMMS DMZ (192.168.30.1) | `ping 192.168.30.1` | Respuesta por IP | Pendiente | Captura del ping |
| 10 | Cliente LAN | TV-DMZ (192.168.30.10) | `ping 192.168.30.10` y, si está disponible, `tracert -d 192.168.30.10` o `tracepath -n 192.168.30.10` | Comunicación por IP a través de TV-COMMS | Pendiente | Captura del ping/tracert |
| 11 | TV-COMMS | Puerta de enlace exterior | `ip route show default` y ping a la puerta de enlace indicada | Ruta predeterminada para NAT y respuesta | Pendiente | Captura de la ruta/ping |
| 12 | Cliente LAN | Internet por IP | Ping a una IP pública autorizada por el profesorado | Conectividad exterior a través de TV-COMMS, si se ha configurado NAT | Pendiente | Captura del ping |

## 6.3. Comandos generales

**Windows:**
```powershell
hostname
whoami
ipconfig /all
route print -4
```

**Linux:**
```bash
hostnamectl
whoami
ip -br address
ip route
```

**Servidor de comunicaciones:**
```bash
ip -br address
ip route
sysctl net.ipv4.ip_forward
```

## 6.4. Si una prueba falla

1. Comprobar que las máquinas están encendidas y conectadas a la red virtual correcta.
2. Revisar las IP, las máscaras y las puertas de enlace.
3. Comprobar que TV-COMMS tiene activado el reenvío IPv4.
4. Comprobar las rutas y las reglas NAT.
5. Revisar el cortafuegos: ICMP puede estar bloqueado aunque el enrutamiento funcione. Autorizar únicamente el tráfico de prueba necesario; no desactivar el cortafuegos como solución general.
6. Registrar la incidencia en `07-seguiment-incidencies.md` y repetir la prueba después de corregirla.

Las pruebas LAN-DMZ solo demuestran el enrutamiento. No demuestran un aislamiento de seguridad avanzado; este se trabajará en el Sprint 5.

## 6.5. Evidencias

Las capturas deben guardarse en `img/sprint-2/`, con el número de prueba y el nombre del equipo. Cada captura debe mostrar el comando ejecutado y el resultado. Evitar que aparezcan contraseñas, claves o información personal.

## 6.6. Conclusión de las pruebas

**Pendiente de completar después de la práctica:** indicar qué pruebas han sido correctas, cuáles han fallado, qué correcciones se han aplicado y qué puntos quedan pendientes. La infraestructura solo se marcará como operativa cuando las pruebas principales se hayan realizado y documentado.
