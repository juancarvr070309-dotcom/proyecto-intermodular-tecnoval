# 5. Instal·lació i configuració del servei DHCP

## 5.1. Objectiu

El servidor de comunicacions `TV-COMMS` assignarà automàticament la configuració IP als dos clients de la LAN: `TV-CLIENT-WIN` i `TV-CLIENT-LINUX`.

El DHCP només escoltarà en la interfície LAN. No s'activarà en l'adaptador exterior ni en la DMZ. Els servidors conservaran adreces fixes.

## 5.2. Paràmetres del servei

| Paràmetre | Valor |
|---|---|
| Xarxa | 192.168.10.0/24 |
| Màscara | 255.255.255.0 |
| Rang dinàmic | 192.168.10.100–192.168.10.150 |
| Passarel·la | 192.168.10.1 |
| IP fixes reservades | 192.168.10.1 (TV-COMMS), 192.168.10.10 (TV-SRVINT) |
| Temps de concessió | 12 hores |
| Interfície d'escolta | Interfície LAN de TV-COMMS |
| DNS anunciat | Cap en aquest sprint; el DNS corporatiu es configura en el Sprint 3 |

El rang DHCP no inclou les IP fixes. Per als dos clients hi ha prou adreces disponibles.

## 5.3. Servei proposat

En Ubuntu Server 26.04.1 LTS es proposa `dnsmasq` utilitzat només com a servidor DHCP, amb la funció DNS desactivada. Abans d'instal·lar-lo, comprovar que el nom de la interfície LAN és correcte.

Exemple de configuració orientativa per a `/etc/dnsmasq.d/tecnoval-dhcp.conf` (substituir `INTERFICIE_LAN` pel nom real):

```ini
port=0
interface=INTERFICIE_LAN
bind-interfaces
dhcp-authoritative
dhcp-range=192.168.10.100,192.168.10.150,255.255.255.0,12h
dhcp-option=option:router,192.168.10.1
dhcp-leasefile=/var/lib/misc/dnsmasq.leases
```

La configuració no anuncia DNS perquè en aquest sprint no s'ha desplegat el DNS corporatiu i el PDF indica que no s'exigeix la resolució de noms. Si el professorat demana un DNS accessible, cal acordar quin s'utilitzarà abans d'afegir l'opció corresponent.

Després d'instal·lar i configurar el servei, comprovar la sintaxi i l'estat amb les ordres adequades a la versió instal·lada. No deixar el servei escoltant en l'exterior ni en la DMZ.

## 5.4. Configuració dels clients

**Windows (TV-CLIENT-WIN):**
1. Obrir les propietats de l'adaptador Ethernet.
2. Seleccionar obtenció automàtica de l'adreça IP.
3. Seleccionar obtenció automàtica de DNS (no s'espera DNS corporatiu en aquest sprint).
4. Obrir terminal i executar:

```powershell
ipconfig /release
ipconfig /renew
ipconfig /all
```

**Linux (TV-CLIENT-LINUX):**
1. Configurar la connexió cablejada perquè IPv4 utilitze automàticament DHCP.
2. Desconnectar i tornar a connectar la connexió o renovar-la des del gestor de xarxa.
3. Consultar:

```bash
ip -br address
ip route
nmcli device show
```

Els dos clients han de rebre una IP entre `192.168.10.100` i `192.168.10.150`, màscara /24 i passarel·la `192.168.10.1`.

## 5.5. Revisió de concessions

Consultar el fitxer de concessions configurat en dnsmasq:
```bash
sudo cat /var/lib/misc/dnsmasq.leases
```

Han d'aparéixer les concessions dels dos clients amb la seua IP i MAC. Si el fitxer no existeix o està buit, comprovar que els clients han sol·licitat DHCP i que el servei escolta en la interfície LAN correcta.

## 5.6. Evidències

Guardar captures reals:
- `11-dhcp-config.png`: fitxer de configuració sense dades sensibles.
- `12-dhcp-status.png`: estat del servei.
- `13-dhcp-leases.png`: concessions dels dos clients.
- `14-client-win-dhcp.png`: `ipconfig /all` del client Windows.
- `15-client-linux-dhcp.png`: `ip -br address` i `ip route` del client Linux.

No s'ha de donar per complet el DHCP fins que els dos clients obtinguen les dades correctes i apareguen les seues concessions al servidor.
