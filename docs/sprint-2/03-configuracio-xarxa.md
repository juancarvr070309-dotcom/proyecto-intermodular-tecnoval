# 3. Configuració de la LAN, la DMZ i l'adreçament

## 3.1. Xarxes virtuals de VirtualBox

Crear dues xarxes de tipus **Xarxa interna** amb aquests noms exactes:

- `TecnoVal-LAN`: xarxa interna dels clients i del servidor intern.
- `TecnoVal-DMZ`: xarxa separada per al servidor de la DMZ.

El servidor de comunicacions tindrà tres adaptadors: NAT exterior, LAN i DMZ. Les altres màquines tindran només l'adaptador de la xarxa que els correspon.

## 3.2. Adaptadors de cada màquina

| Màquina | Adaptador 1 | Adaptador 2 | Adaptador 3 |
|---|---|---|---|
| TV-COMMS | NAT (exterior) | Xarxa interna: TecnoVal-LAN | Xarxa interna: TecnoVal-DMZ |
| TV-SRVINT | Xarxa interna: TecnoVal-LAN | — | — |
| TV-CLIENT-WIN | Xarxa interna: TecnoVal-LAN | — | — |
| TV-CLIENT-LINUX | Xarxa interna: TecnoVal-LAN | — | — |
| TV-DMZ | Xarxa interna: TecnoVal-DMZ | — | — |

No activar NAT propi en els clients ni en els servidors interns: l'eixida exterior s'ha de fer a través de TV-COMMS.

## 3.3. Pla IP adaptat al laboratori

Per a aquest sprint s'utilitzen dues de les xarxes del disseny del Sprint 1. La xarxa de servidors del disseny inicial s'adapta a una LAN de laboratori única per simplificar les proves. Les altres VLAN (gestió, impressores i convidats) continuen sent part del disseny de l'empresa, però no es despleguen en aquest laboratori bàsic.

| Equip | Interfície | Xarxa virtual | Mode VirtualBox | IP | Prefix | Passarel·la | DNS |
|---|---|---|---|---|---|---|---|
| TV-COMMS | Exterior | NAT | NAT | Automàtica | DHCP de VirtualBox | Automàtica | Automàtic |
| TV-COMMS | LAN | TecnoVal-LAN | Xarxa interna | 192.168.10.1 | /24 | — | — |
| TV-COMMS | DMZ | TecnoVal-DMZ | Xarxa interna | 192.168.30.1 | /24 | — | — |
| TV-SRVINT | LAN | TecnoVal-LAN | Xarxa interna | 192.168.10.10 | /24 | 192.168.10.1 | Sense DNS corporatiu en aquest sprint |
| TV-CLIENT-WIN | LAN | TecnoVal-LAN | Xarxa interna | DHCP (192.168.10.100–150) | /24 | 192.168.10.1 | No s'anuncia DNS en aquest sprint |
| TV-CLIENT-LINUX | LAN | TecnoVal-LAN | Xarxa interna | DHCP (192.168.10.100–150) | /24 | 192.168.10.1 | No s'anuncia DNS en aquest sprint |
| TV-DMZ | DMZ | TecnoVal-DMZ | Xarxa interna | 192.168.30.10 | /24 | 192.168.30.1 | Sense DNS corporatiu en aquest sprint |

**Nota:** les IP de la taula són la configuració prevista. Després de configurar les màquines, substituir-les si l'entorn real obliga a utilitzar altres valors i actualitzar aquest document i el diagrama.

## 3.4. Justificació

- LAN: `192.168.10.0/24`, per als clients i el servidor intern.
- DMZ: `192.168.30.0/24`, per al servidor situat en la zona separada.
- Les dues xarxes no se solapen: tenen identificadors de xarxa diferents.
- TV-COMMS utilitza `.1` com a passarel·la de cada xarxa.
- Els servidors mantenen IP fixes; els dos clients obtenen les seues IP per DHCP.
- En aquest sprint no es configura DNS corporatiu; s'implantarà en el Sprint 3. Les proves es faran per adreça IP.

## 3.5. Comprovacions

En Linux:
```bash
hostnamectl
ip -br address
ip route
```

En Windows:
```powershell
hostname
ipconfig /all
route print -4
```

Comprovar que:
1. Els noms coincideixen amb la taula.
2. TV-COMMS té tres interfícies i les IP internes previstes.
3. Els clients només tenen un adaptador LAN.
4. TV-DMZ només té un adaptador DMZ.
5. No hi ha adreces duplicades.

## 3.6. Diagrama actualitzat

![Diagrama del laboratori Sprint 2 de TecnoVal](../../img/sprint-2/topologia-sprint-2.svg)

El diagrama mostra les connexions virtuals i les IP previstes. Cal actualitzar-lo si la configuració real canvia.

## 3.7. Evidències

Guardar en `img/sprint-2/` captures de la configuració d'adaptadors de VirtualBox i de les ordres anteriors. Identificar cada captura amb el nom de la màquina. No s'han d'incloure contrasenyes, claus ni dades personals.
