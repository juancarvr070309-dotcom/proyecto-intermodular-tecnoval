# 1. Pla d'intervenció i organització del treball

## 1.1. Objectiu

Implantar una infraestructura de laboratori per a TecnoVal Asistencia IT, basada en el disseny del Sprint 1. Es configuraran una xarxa LAN, una DMZ separada, un servidor Linux d'encaminament i DHCP, i dos clients de prova (Windows i Linux).

**Important sobre les màquines:** el PDF estableix cinc equips en total: servidor de comunicacions Linux, servidor intern Windows, client Windows, client Linux i servidor Linux de la DMZ. Per tant, només dos són clients. Es manté aquesta estructura mínima del professorat sense crear màquines per als 12 treballadors de l'empresa.

## 1.2. Seqüència, dependències i temps previst

| Setmana | Tasques | Dependència | Responsable principal | Col·laborador |
|---|---|---|---|---|
| 1 | Revisar IP, versions, capacitat dels ordinadors i preparar VirtualBox/ISOs | Cap | Juan Carlos | Isaac |
| 1 | Crear les cinc màquines i instal·lar els sistemes | Recursos preparats | Isaac | Juan Carlos |
| 2 | Crear LAN i DMZ virtuals; configurar noms i IP fixes | Màquines instal·lades | Isaac | Juan Carlos |
| 3 | Configurar encaminament IPv4 i connectivitat exterior | Interfícies configurades | Isaac | Juan Carlos |
| 3 | Instal·lar i configurar DHCP només per a la LAN | Encaminament i LAN operatius | Isaac | Juan Carlos |
| 4 | Configurar clients per DHCP i fer proves de connectivitat | DHCP operatiu | Juan Carlos | Isaac |
| 4 | Corregir incidències i repetir proves | Resultats de proves | Ambdós | Ambdós |
| 5 | Completar captures, documentació, diagrama i revisió final | Configuració acabada | Juan Carlos | Isaac |
| 5 | Revisar GitHub, Trello i preparar lliurament | Documents revisats | Ambdós | Ambdós |

Els temps són una previsió orientativa. Al final de cada sessió s'anotarà el temps real i el treball pendent en Trello i en el document 07.

## 1.3. Recursos materials i programari

- Ordinador amfitrió amb VirtualBox i virtualització activada a BIOS/UEFI.
- Connexió a Internet per descarregar actualitzacions i imatges ISO.
- Imatges ISO d'Ubuntu Server 26.04.1 LTS per als servidors Linux, Debian 13 amb XFCE per al client Linux i Windows (versions autoritzades pel professorat).
- Espai lliure recomanat: almenys 100 GB per a les màquines i les instantànies.
- Memòria RAM recomanada: 16 GB a l'amfitrió per executar les cinc màquines amb comoditat. Si l'equip té menys memòria, s'iniciaran només les màquines necessàries en cada prova, sempre que es puga mantenir l'entorn connectat.
- GitHub, Trello i editor de Markdown.

## 1.4. Distribució de les màquines

Per simplificar la pràctica, la primera opció és allotjar les cinc màquines virtuals en **un mateix ordinador amfitrió**. Així, les xarxes internes de VirtualBox anomenades `TecnoVal-LAN` i `TecnoVal-DMZ` seran compartides per totes les màquines del laboratori.

Si es reparteixen entre els dos ordinadors físics dels integrants, les xarxes internes amb el mateix nom no es connectaran automàticament. En eixe cas, caldrà acordar amb el professorat una connexió física comuna (per exemple, adaptadors en pont a una xarxa de laboratori controlada) i comprovar que no es connecta accidentalment a la xarxa real de l'aula.

## 1.5. Permisos i autoritzacions

- Utilitzar únicament els ordinadors i les xarxes autoritzats pel professorat.
- No modificar la configuració de la xarxa física del centre ni del router de l'aula.
- No connectar la LAN o la DMZ de proves a la xarxa real sense autorització.
- Utilitzar les ISO i llicències facilitades o autoritzades pel centre.
- Informar el professorat si falta algun permís, recurs o versió de programari.

## 1.6. Riscos i mesures preventives

| Risc | Mesura preventiva | Mitjà de protecció o recuperació |
|---|---|---|
| Fatiga per treball prolongat davant de pantalles | Fer pauses curtes, ajustar la postura i la il·luminació i seguir les normes de l'aula | Cadira i pantalla ben ajustades |
| Manipulació de cables o connexions elèctriques | No obrir equips ni manipular endolls amb les mans humides; demanar ajuda al professorat | Regletes en bon estat i supervisió |
| Pèrdua de dades o configuracions | Fer instantànies abans de canvis importants i còpies dels fitxers de configuració | Instantànies de VirtualBox i còpia de la documentació |
| Canvis de xarxa que afecten altres equips | Utilitzar xarxes internes virtuals i no modificar la xarxa física | Aïllament de VirtualBox i autorització docent |
| Sobrecàrrega de RAM o disc | Comprovar recursos abans d'arrancar totes les VM | Apagar VM no necessàries i alliberar espai |

## 1.7. Imprevistos previstos

| Imprevist | Solució prevista |
|---|---|
| Falta de memòria RAM | Reduir temporalment la RAM assignada dins dels límits del sistema, tancar aplicacions de l'amfitrió i executar les proves per fases. |
| Espai de disc insuficient | Esborrar ISO duplicades i instantànies antigues després de comprovar que no són necessàries; ampliar l'espai amb autorització. |
| Una instal·lació no arranca | Revisar l'ordre d'arrancada, la ISO i la configuració de la VM; tornar a una instantània o repetir la instal·lació. |
| Les dues xarxes virtuals no es comuniquen | Revisar el nom exacte de les xarxes, els adaptadors i les IP; comprovar que totes les VM estan en el mateix amfitrió o en una xarxa física comuna autoritzada. |

## 1.8. Seguiment

Al final de cada sessió, Juan Carlos i Isaac revisaran les targetes de Trello, anotaran el temps real, les tasques acabades, les incidències i el següent pas. Si una desviació posa en risc el termini o canvia l'abast, s'informarà el professorat i es registrarà l'acord en el document 07.

**Tauler Trello:** [Proyecto Intermodular — TecnoVal Assistència IT](https://trello.com/b/PPo2BEAZ/proyecto-intermodular-tecnoval-assistencia-it-juan-carlos-isaac-beltran).

## 1.9. Distribució del treball

Els dos integrants participaran en la instal·lació, les proves i la documentació. Com a repartiment inicial, Isaac coordinarà la configuració de xarxa i dels servidors, mentre Juan Carlos coordinarà el registre de proves, les captures i la documentació. Les decisions i comprovacions finals es faran conjuntament. El repartiment es podrà ajustar segons el treball real de cada sessió.
