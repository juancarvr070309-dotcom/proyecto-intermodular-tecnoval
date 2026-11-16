# 6. Proves de connectivitat i validació

## 6.1. Objectiu

Comprovar que les cinc màquines arranquen, que les IP coincideixen amb el pla, que els clients reben DHCP i que TV-COMMS encamina el trànsit entre LAN i DMZ. Les proves es fan per IP perquè el DNS corporatiu correspon al Sprint 3.

## 6.2. Taula de proves

Els resultats obtinguts i els enllaços a les captures s'han d'emplenar després de realitzar cada prova. No s'han inventat resultats.

| Núm. | Origen / equip | Destinació o comprovació | Procediment | Resultat esperat | Resultat obtingut | Evidència |
|---:|---|---|---|---|---|---|
| 1 | Les cinc VM | Arrancada i inici de sessió | `hostname` i `whoami` (Linux/Windows) | Totes arranquen i mostren el nom correcte | Pendent | `img/sprint-2/` |
| 2 | TV-COMMS | Interfícies i rutes | `ip -br address` i `ip route` | Tres interfícies; rutes LAN/DMZ i ruta per defecte exterior | Pendent | `07-comms-interficies.png`, `08-comms-rutes.png` |
| 3 | TV-COMMS | Reenviament IPv4 | `sysctl net.ipv4.ip_forward` | Valor 1, també després de reiniciar | Pendent | `09-comms-forwarding.png` |
| 4 | TV-CLIENT-WIN | DHCP | `ipconfig /release`, `ipconfig /renew`, `ipconfig /all` | IP del rang, màscara /24 i gateway .1 | Pendent | `14-client-win-dhcp.png` |
| 5 | TV-CLIENT-LINUX | DHCP | `ip -br address`, `ip route`, `nmcli device show` | IP del rang, màscara /24 i gateway .1 | Pendent | `15-client-linux-dhcp.png` |
| 6 | TV-COMMS | Concessions DHCP | Consultar `/var/lib/misc/dnsmasq.leases` | Apareixen els dos clients amb IP i MAC | Pendent | `13-dhcp-leases.png` |
| 7 | Client LAN | TV-SRVINT (192.168.10.10) | `ping 192.168.10.10` | Resposta per IP | Pendent | Captura ping |
| 8 | Client LAN | TV-COMMS LAN (192.168.10.1) | `ping 192.168.10.1` | Resposta per IP | Pendent | Captura ping |
| 9 | TV-DMZ | TV-COMMS DMZ (192.168.30.1) | `ping 192.168.30.1` | Resposta per IP | Pendent | Captura ping |
| 10 | Client LAN | TV-DMZ (192.168.30.10) | `ping 192.168.30.10` i, si està disponible, `tracert -d 192.168.30.10` o `tracepath -n 192.168.30.10` | Comunicació per IP a través de TV-COMMS | Pendent | Captura ping/tracert |
| 11 | TV-COMMS | Passarel·la exterior | `ip route show default` i ping a la passarel·la indicada | Ruta per defecte per NAT i resposta | Pendent | Captura ruta/ping |
| 12 | Client LAN | Internet per IP | Ping a una IP pública autoritzada pel professorat | Connectivitat exterior a través de TV-COMMS, si s'ha configurat NAT | Pendent | Captura ping |

## 6.3. Comandes generals

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

**Servidor de comunicacions:**
```bash
ip -br address
ip route
sysctl net.ipv4.ip_forward
```

## 6.4. Si una prova falla

1. Comprovar que les màquines estan enceses i connectades a la xarxa virtual correcta.
2. Revisar les IP, màscares i passarel·les.
3. Comprovar que TV-COMMS té el reenviament IPv4 activat.
4. Comprovar les rutes i les regles NAT.
5. Revisar el tallafoc: ICMP pot estar bloquejat encara que l'encaminament funcione. Autoritzar només el trànsit de prova necessari; no desactivar el tallafoc com a solució general.
6. Registrar la incidència en `07-seguiment-incidencies.md` i repetir la prova després de corregir-la.

Les proves LAN-DMZ només demostren encaminament. No demostren aïllament de seguretat avançat; aquest es treballarà en el Sprint 5.

## 6.5. Evidències

Les captures s'han de guardar en `img/sprint-2/`, amb el número de prova i el nom de l'equip. Cada captura ha de mostrar l'ordre executada i el resultat. Evitar que es vegen contrasenyes, claus o informació personal.

## 6.6. Conclusió de les proves

**Pendent d'emplenar després de la pràctica:** indicar quines proves han sigut correctes, quines han fallat, quines correccions s'han aplicat i quins punts queden pendents. Només es marcarà la infraestructura com a operativa quan les proves principals s'hagen realitzat i documentat.
