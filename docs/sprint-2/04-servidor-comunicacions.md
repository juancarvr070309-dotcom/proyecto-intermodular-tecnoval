# 4. Servidor de comunicacions i encaminament

## 4.1. Funció

`TV-COMMS` és una màquina virtual amb Ubuntu Server 24.04 LTS que actua com a encaminador entre la LAN (`192.168.10.0/24`) i la DMZ (`192.168.30.0/24`). També proporciona l'eixida a Internet mitjançant l'adaptador NAT de VirtualBox i allotjarà el servei DHCP de la LAN.

## 4.2. Interfícies

La màquina ha de tindre tres adaptadors. Els noms Linux poden variar; no s'ha de copiar un nom d'interfície sense comprovar-lo.

| Funció | Xarxa VirtualBox | IP prevista |
|---|---|---|
| Exterior | NAT | Automàtica |
| LAN | TecnoVal-LAN | 192.168.10.1/24 |
| DMZ | TecnoVal-DMZ | 192.168.30.1/24 |

Identificar les interfícies amb:
```bash
ip -br link
ip -br address
```

Anotar quin nom correspon a NAT, LAN i DMZ abans de modificar cap fitxer de xarxa.

## 4.3. Configurar les IP internes

Configurar les interfícies LAN i DMZ amb IP fixes amb Netplan, que és l'eina habitual d'Ubuntu Server. Abans d'editar, identificar les interfícies i revisar la configuració existent de `/etc/netplan/`. No s'han de configurar dos gestors alhora per a les mateixes interfícies.

Valors:
- Interfície LAN: `192.168.10.1/24`.
- Interfície DMZ: `192.168.30.1/24`.
- Interfície exterior: DHCP de VirtualBox NAT.

Després, comprovar:
```bash
ip -br address
ip route
```

La ruta per defecte ha d'eixir per la interfície exterior. Les xarxes connectades `192.168.10.0/24` i `192.168.30.0/24` han d'aparéixer com a rutes directament connectades.

## 4.4. Activar el reenviament IPv4 de manera persistent

Crear el fitxer `/etc/sysctl.d/99-tecnoval-router.conf` amb aquest contingut:

```ini
net.ipv4.ip_forward=1
```

Aplicar i comprovar:
```bash
sudo sysctl --system
sysctl net.ipv4.ip_forward
```

El resultat esperat és `net.ipv4.ip_forward = 1`. Després de reiniciar, tornar a executar l'ordre per comprovar que continua activat.

## 4.5. Eixida a Internet mitjançant NAT

Perquè la LAN i la DMZ puguen eixir a Internet a través de TV-COMMS, cal configurar encaminament i traducció d'adreces (masquerade) des de les xarxes internes cap a la interfície exterior. La configuració concreta de les regles dependrà del sistema de tallafoc autoritzat pel professorat. Documentar les regles aplicades i no desactivar el tallafoc com a solució general.

Abans de configurar-les, identificar la interfície exterior real amb `ip route`. No inventar-ne el nom.

## 4.6. Proves

Des de TV-COMMS:
```bash
ip -br address
ip route
sysctl net.ipv4.ip_forward
ping -c 4 192.168.10.10
ping -c 4 192.168.30.10
```

Les dues últimes proves es faran quan els servidors corresponents estiguen configurats i responguen a ICMP. També comprovar la passarel·la exterior assignada per VirtualBox:
```bash
ip route show default
```

Després de reiniciar TV-COMMS, repetir les comprovacions d'interfícies, rutes i reenviament.

## 4.7. Evidències necessàries

Guardar captures reals en `img/sprint-2/`:
- `07-comms-interficies.png`: `ip -br address`.
- `08-comms-rutes.png`: `ip route`.
- `09-comms-forwarding.png`: valor 1 de `net.ipv4.ip_forward`.
- `10-comms-reinici.png`: comprovació després de reiniciar.

Afegir ací les captures quan es realitzen. No s'afirma que l'encaminament estiga operatiu fins que les proves donen el resultat esperat.
