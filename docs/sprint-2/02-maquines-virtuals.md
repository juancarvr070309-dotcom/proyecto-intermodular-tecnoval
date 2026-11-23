# 2. Creació de les màquines virtuals i instal·lació

## 2.1. Criteri

El laboratori segueix l'estructura mínima del PDF: cinc màquines virtuals en total, de les quals només dues són clients de prova. No es crearà una màquina per cadascun dels 12 treballadors de TecnoVal.

S'utilitzarà Ubuntu Server 26.04.1 LTS en els dos servidors Linux (`TV-COMMS` i `TV-DMZ`). Per al client Linux es proposa Debian 13 amb l'entorn gràfic XFCE: és lleuger, funciona bé amb 2 GB de RAM i permet practicar les ordres Linux sense carregar massa l'ordinador amfitrió. La versió de Windows Server i les ISO s'han de confirmar amb el professorat abans de la instal·lació.

## 2.2. Inventari de màquines

Els valors de RAM, CPU i disc són una proposta inicial. Cal anotar els valors reals de VirtualBox després de crear cada màquina.

| Nom de la VM | Funció | Sistema proposat | RAM | CPU | Disc | Amfitrió |
|---|---|---|---:|---:|---:|---|
| `TV-COMMS` | Encaminament LAN/DMZ i DHCP | Ubuntu Server 26.04.1 LTS | 2 GB | 2 | 20 GB | Ordinador de laboratori acordat |
| `TV-SRVINT` | Servidor intern, preparat per al Sprint 3 | Windows Server (versió indicada pel professorat) | 4 GB | 2 | 60 GB | Mateix amfitrió |
| `TV-CLIENT-WIN` | Client Windows de proves | Windows 11 Pro | 4 GB | 2 | 64 GB | Mateix amfitrió |
| `TV-CLIENT-LINUX` | Client Linux de proves | Debian 13 amb XFCE | 2 GB | 2 | 25 GB | Mateix amfitrió |
| `TV-DMZ` | Servidor Linux situat en la DMZ | Ubuntu Server 26.04.1 LTS | 1–2 GB | 1 | 20 GB | Mateix amfitrió |

**RAM total orientativa:** 13–14 GB (segons la RAM assignada a TV-DMZ). Si l'ordinador no disposa de prou RAM, no s'han d'arrancar les cinc màquines alhora: es poden iniciar per fases, mantenint actius el servidor de comunicacions i els equips necessaris per a cada prova. No s'ha d'assignar a les VM tota la RAM física de l'amfitrió.

## 2.3. Decisions d'instal·lació

- Utilitzar discs virtuals dinàmics per no ocupar immediatament tota la capacitat màxima.
- Assignar noms d'equip únics, tal com apareixen en la taula.
- Instal·lar només els components necessaris per a les proves.
- No instal·lar Active Directory ni unir els clients a un domini en aquest sprint; correspon al Sprint 3.
- No instal·lar serveis públics en la DMZ; només deixar el servidor instal·lat i connectat a la xarxa DMZ.
- Fer una instantània després de completar la instal·lació bàsica.

## 2.4. Comprovacions d'instal·lació

En cada màquina, comprovar que arranca, permet iniciar sessió i mostra el nom correcte.

**Windows:**
```powershell
hostname
whoami
```

**Linux (Ubuntu Server i Debian):**
```bash
hostname
whoami
hostnamectl
```

## 2.5. Evidències que s'han d'afegir

Guardar les captures reals en `img/sprint-2/` amb noms clars:

| Captura | Què ha de mostrar |
|---|---|
| `01-tv-comms-login.png` | Sessió iniciada i nom TV-COMMS |
| `02-tv-srvint-login.png` | Sessió iniciada i nom TV-SRVINT |
| `03-tv-client-win-login.png` | Sessió iniciada i nom TV-CLIENT-WIN |
| `04-tv-client-linux-login.png` | Sessió iniciada i nom TV-CLIENT-LINUX |
| `05-tv-dmz-login.png` | Sessió iniciada i nom TV-DMZ |
| `06-virtualbox-resum-vm.png` | Configuració de RAM, CPU i disc de les màquines |

> **Pendent de completar:** inserir les captures reals quan les cinc màquines estiguen instal·lades. No s'han afegit captures fictícies.

## 2.6. Clonació

Si es clona alguna màquina, cal generar una nova adreça MAC per a cada adaptador i canviar el nom de l'equip abans de connectar-la a la xarxa. No s'han de deixar dues màquines amb el mateix nom o MAC.

## 2.7. Resultat

Aquest apartat quedarà complet quan les cinc màquines arranquen correctament, permeten iniciar sessió i les captures mostren els noms i recursos reals. El servidor intern Windows quedarà preparat per al Sprint 3, sense Active Directory ni unió al domini.
