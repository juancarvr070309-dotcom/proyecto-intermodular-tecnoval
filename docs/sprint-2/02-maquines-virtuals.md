# 2. Creación de las máquinas virtuales e instalación

## 2.1. Criterio

El laboratorio sigue la estructura mínima del PDF: cinco máquinas virtuales en total, de las cuales solo dos son clientes de prueba. No se creará una máquina para cada uno de los 12 trabajadores de TecnoVal.

Se utilizará Ubuntu Server 26.04.1 LTS en los dos servidores Linux (`TV-COMMS` y `TV-DMZ`). Para el cliente Linux se propone Debian 13 con el entorno gráfico XFCE: es ligero, funciona bien con 2 GB de RAM y permite practicar los comandos de Linux sin cargar demasiado el ordenador anfitrión. La versión de Windows Server y las imágenes ISO deben confirmarse con el profesorado antes de la instalación.

## 2.2. Inventario de máquinas

Los valores de RAM, CPU y disco son una propuesta inicial. Hay que anotar los valores reales de VirtualBox después de crear cada máquina.

| Nombre de la VM | Función | Sistema propuesto | RAM | CPU | Disco | Anfitrión |
|---|---|---|---:|---:|---:|---|
| `TV-COMMS` | Enrutamiento LAN/DMZ y DHCP | Ubuntu Server 26.04.1 LTS | 2 GB | 2 | 20 GB | Ordenador de laboratorio acordado |
| `TV-SRVINT` | Servidor interno, preparado para el Sprint 3 | Windows Server 22 | 4 GB | 2 | 60 GB | Mismo anfitrión |
| `TV-CLIENT-WIN` | Cliente Windows de pruebas | Windows 11 Pro | 4 GB | 2 | 64 GB | Mismo anfitrión |
| `TV-CLIENT-LINUX` | Cliente Linux de pruebas | Debian 13 con XFCE | 2 GB | 2 | 25 GB | Mismo anfitrión |
| `TV-DMZ` | Servidor Linux situado en la DMZ | Ubuntu Server 26.04.1 LTS | 1–2 GB | 1 | 20 GB | Mismo anfitrión |

**RAM total orientativa:** 13–14 GB (según la RAM asignada a TV-DMZ). Si el ordenador no dispone de suficiente RAM, no se deben iniciar las cinco máquinas al mismo tiempo: se pueden iniciar por fases, manteniendo activos el servidor de comunicaciones y los equipos necesarios para cada prueba. No se debe asignar a las VM toda la RAM física del anfitrión.

## 2.3. Decisiones de instalación

- Utilizar discos virtuales dinámicos para no ocupar inmediatamente toda la capacidad máxima.
- Asignar nombres de equipo únicos, tal como aparecen en la tabla.
- Instalar solo los componentes necesarios para las pruebas.
- No instalar Active Directory ni unir los clientes a un dominio en este sprint; corresponde al Sprint 3.
- No instalar servicios públicos en la DMZ; solo dejar el servidor instalado y conectado a la red DMZ.
- Crear una instantánea después de completar la instalación básica.

## 2.4. Comprobaciones de instalación

En cada máquina, comprobar que arranca, permite iniciar sesión y muestra el nombre correcto.

**Windows:**
```powershell
hostname
whoami
```

**Linux (Ubuntu Server y Debian):**
```bash
hostname
whoami
hostnamectl
```

## 2.5. Evidencias que se deben añadir

Guardar las capturas reales en `img/sprint-2/` con nombres claros:

| Captura | Qué debe mostrar |
|---|---|
| `01-tv-comms-login.png` | Sesión iniciada y nombre TV-COMMS |
| `02-tv-srvint-login.png` | Sesión iniciada y nombre TV-SRVINT |
| `03-tv-client-win-login.png` | Sesión iniciada y nombre TV-CLIENT-WIN |
| `04-tv-client-linux-login.png` | Sesión iniciada y nombre TV-CLIENT-LINUX |
| `05-tv-dmz-login.png` | Sesión iniciada y nombre TV-DMZ |
| `06-virtualbox-resum-vm.png` | Configuración de RAM, CPU y disco de las máquinas |

> **Pendiente de completar:** insertar las capturas reales cuando las cinco máquinas estén instaladas. No se han añadido capturas ficticias.

## 2.6. Clonación

Si se clona alguna máquina, hay que generar una nueva dirección MAC para cada adaptador y cambiar el nombre del equipo antes de conectarla a la red. No se deben dejar dos máquinas con el mismo nombre o MAC.

## 2.7. Resultado

Este apartado quedará completo cuando las cinco máquinas arranquen correctamente, permitan iniciar sesión y las capturas muestren los nombres y recursos reales. El servidor interno Windows quedará preparado para el Sprint 3, sin Active Directory ni unión al dominio.
