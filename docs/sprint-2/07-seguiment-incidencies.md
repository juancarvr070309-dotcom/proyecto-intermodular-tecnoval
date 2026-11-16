# 7. Seguiment del sprint i registre d'incidències

## 7.1. Organització del seguiment

El seguiment es farà al final de cada sessió de treball. Juan Carlos i Isaac revisaran les targetes de Trello i actualitzaran aquest document amb:

- Tasques previstes i tasques realitzades.
- Temps utilitzat.
- Problemes detectats i solucions aplicades.
- Tasques que queden pendents.
- Diferències respecte del pla inicial.

**Tauler Trello:** [Proyecto Intermodular — TecnoVal Assistència IT](https://trello.com/b/PPo2BEAZ/proyecto-intermodular-tecnoval-assistencia-it-juan-carlos-isaac-beltran).

## 7.2. Registre de sessions

| Data | Tasques previstes | Tasques realitzades | Temps utilitzat | Problemes o desviacions | Treball pendent |
|---|---|---|---|---|---|
| Pendent d'emplenar | Preparar entorn i revisar recursos | — | — | — | — |
| Pendent d'emplenar | Crear màquines i instal·lar sistemes | — | — | — | — |
| Pendent d'emplenar | Configurar LAN, DMZ i IP | — | — | — | — |
| Pendent d'emplenar | Configurar encaminament i DHCP | — | — | — | — |
| Pendent d'emplenar | Proves, correccions i documentació | — | — | — | — |

No s'han afegit dates ni temps ficticis. Emplenar les files després de cada sessió.

## 7.3. Registre d'incidències

| Data | Equip o tasca | Problema o desviació | Causa identificada | Intervenció i responsable | Comprovació final | Comunicació al professorat |
|---|---|---|---|---|---|---|
| — | — | Cap incidència real registrada encara | — | — | — | No aplica |

Quan aparega una incidència real, afegir una fila amb la informació completa. Si no hi ha incidències, mantindre-ho indicat i justificar-ho amb les proves realitzades. No inventar problemes ni solucions.

## 7.4. Comunicació de desviacions

Si una incidència afecta el termini, els recursos o l'abast de la pràctica:
1. Informar el professorat tan prompte com siga possible.
2. Explicar el problema i la tasca afectada.
3. Proposar una alternativa i indicar si canvia el termini.
4. Registrar la resposta o l'acord en la taula d'incidències.
5. Actualitzar el pla, la taula IP o el diagrama si el canvi ho requereix.

## 7.5. Revisió final

Completar aquest apartat quan s'hagen fet les pràctiques:

- **Què funciona:** pendent de les proves reals.
- **Què queda pendent:** pendent de revisar les tasques i les proves.
- **Canvis respecte del Sprint 1:** el laboratori utilitza dues xarxes de prova, LAN `192.168.10.0/24` i DMZ `192.168.30.0/24`, amb TV-COMMS com a encaminador. Les altres VLAN del disseny empresarial no es despleguen en aquest laboratori bàsic.
- **Aportació de Juan Carlos:** participar en instal·lació, proves, captures, documentació i seguiment; concretar les tasques realitzades en acabar.
- **Aportació d'Isaac:** participar en instal·lació, configuració de xarxa i servidors, proves i documentació; concretar les tasques realitzades en acabar.

Les aportacions s'han de descriure segons el treball real i els commits de cada membre, no segons una distribució teòrica.

## 7.6. Captura final de Trello

Afegir una captura real del tauler quan les targetes estiguen actualitzades. La captura ha de mostrar les llistes i l'estat de les tasques del Sprint 2.

**Enllaç:** [Obrir el tauler de Trello](https://trello.com/b/PPo2BEAZ/proyecto-intermodular-tecnoval-assistencia-it-juan-carlos-isaac-beltran).

> **Pendent:** inserir la captura final de Trello en `img/sprint-2/`. No s'ha inventat cap captura.

## 7.7. Criteris de tancament

El Sprint 2 es podrà donar per finalitzat quan:
- Les cinc màquines requerides estiguen instal·lades i arranquen.
- LAN i DMZ siguen xarxes virtuals diferents i no se solapen.
- Les IP fixes, noms i diagrama coincidisquen amb la configuració real.
- TV-COMMS mantinga l'encaminament després de reiniciar.
- Els dos clients reben DHCP correctament.
- Les proves i les incidències estiguen documentades.
- Les captures reals estiguen guardades en `img/sprint-2/`.
- Els set documents i el README estiguen revisats.
- Trello reflectisca l'avanç real i el professorat tinga accés als recursos.

## 7.8. Fonts tècniques

- [VirtualBox User Manual — Networking](https://www.virtualbox.org/manual/ch06.html).
- [Ubuntu Server documentation](https://ubuntu.com/server/docs).
- [Debian Administrator's Handbook](https://debian-handbook.info/) (client Linux Debian).
- [dnsmasq — documentació del projecte](https://thekelleys.org.uk/dnsmasq/doc.html).
- [Linux kernel — IP sysctl](https://docs.kernel.org/networking/ip-sysctl.html).
