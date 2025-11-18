
**Introducció**

La primera hora el vostre responsable de seguretat us presenta el tema de les còpies de seguretat a partir d’un material didàctic. A continuació, caldrà que hi treballeu els aspectes del tema i ho fareu mitjançant una dinàmica cooperativa.

**Presentació del cas client**

"Muntatges i Serveis Tècnics SL" és una petita empresa dedicada a la instal·lació i manteniment d'equips industrials.

**Infraestructura** **Tècnica**:

·         Servidor de Fitxers (Ubuntu Server): Conté tota la documentació crítica:

o   Documents de Projectes: Plànols, especificacions tècniques (300 GB, creixement moderat).

o   Bases de Dades (Comptabilitat i Clients): Crítiques i d'ús diari (20 GB, canvi constant).

o   Carpetes Personals dels Usuaris: Per a la feina diària (100 GB).

·         10 Equips Clients (Windows 10/11): Els usuaris treballen majoritàriament amb fitxers del servidor, però alguns tècnics guarden de forma temporal informes i altres arxius importants a la carpeta Documents.

·         Connexió a Internet: Fibra òptica de 600 Mbps (simètrica).

**Requisits de Recuperació:**

·         Temps de Recuperació (RTO): Les dades de Comptabilitat/Clients han d'estar disponibles en menys de 4 hores.

·         Pèrdua de Dades Admesa (RPO): Es pot admetre una pèrdua màxima de 24 hores per a la majoria de dades, però les dades de Comptabilitat/Clients no poden perdre més de 4 hores de treball.

·         Retenció: Cal guardar les dades amb un historial d'almenys un mes.

**Fase 1: Treball individual**

De forma individual, heu de donar resposta a les següents preguntes basant-se en el cas pràctic:

1\.     Què copiar? (Priorització): Quines són les dades més crítiques del servidor? Cal fer còpia dels 10 equips clients? Justifica-ho.

Les dades més crítiques són les bases de dades de comptabilitat com poden ser factures i clients com pot ser comptes bancaris o contrasenyes, ja que son les dades més importants i més exigents. Els equips clients no cal copiar-los completament, només sincronitzar o fer còpia dels documents temporals ja que és informació no tant important.

2\.  Periodicitat i Tipus de Còpia: Proposa un calendari bàsic per a la setmana (Diari/Setmanal/Mensual) i quin tipus de còpia aplicaràs (Completa, Diferencial, Incremental) per a les dades crítiques.

**Bases de dades:** còpia incremental cada 4 hores i completa setmanal per garantir que es guarda tota l’informació. 

**Documents i carpetes:** incremental diària i completa setmanal. L’he triat mensual per reduir espai i temps.

3\.     Mitjans i Ubicació: Quin tipus de mitjà de còpia utilitzaries (Discs durs externs, NAS, Cloud, Cintes)? On s'hauria de guardar físicament la còpia més recent (Regla 3-2-1).

**Mitjans:** NAS intern per restauració ràpida, Cloud per còpia externa segura, i disc dur extern per còpia mensual offline.

**Regla 3-2-1:** 3 còpies (original \+ NAS \+ Cloud), 2 tipus de mitjà, 1 còpia fora de l’empresa. 

**Ubicació més recent:** NAS intern per complir el RTO de 4 hores; còpies al Cloud i disc extern per seguretat i retenció.

2\.     Elaboració d'una Proposta Unificada: Heu de consensuar i dissenyar el vostre propi Esquema 3-2-1 de Còpies (3 còpies, 2 mitjans, 1 fora de lloc) basat en els requisits del cas.

| Element | Proposta de la Parella | Justificació |
| :---- | :---- | :---- |
| Dades Crítiques | **Bases de dades del servidor  i configuracions.**  |  **Les bases de dades són les més sensibles i informació privada els clients es poden restaurar amb imatge estàndard.** |
| Periodicitat (BD) | **Incremental cada 4 hores i una completa setmanal.** |  **Les bases de dades necessiten còpies cada cert temps per no perdre informació així tens copies.** |
| Tipus de Còpia (BD) | **Incremental per  cada 4h, Diferencial per la setmanal, Completa per la mensual.** | **és molt més ràpida i bona de temps i sobretot molta seguretat, et dona restauració total.** |
| Mitjà 1 (Local) | **NAS intern** |  **volem que sigui xarxa, i ajuda a tenir restauracions ràpides** |
| Mitjà 2 (Extern) | **Cloud i un disc dur extern**  | **Posem cloud mes un disc extern que protegeix contra desastres físics i té regla 3-2-1 amb còpia fora de l’empresa.** |

**Document Final (Fase 3\)**

El grup ha de generar un document amb els següents punts resolts:

1\)      Dades Objecte de Còpia

Quines dades es copien i amb quina freqüència (separant Servidor/Clients i crítiques/no crítiques).

2\)      Cronograma Setmanal Detallat

| Dia | Dades | Tipus de còpia | Mitjà |
| :---- | ----- | ----- | :---- |
| Dilluns | Bases de dades i configuracions crítiques | Incremental | NAS / Disc dur extern |
| Dimarts | Bases de dades i configuracions crítiques | Incremental | NAS / Disc dur extern |
| Dimecres | Bases de dades i configuracions crítiques | Incremental | NAS / Disc dur extern |
| Dijous | Bases de dades i configuracions crítiques | Incremental | NAS / Disc dur extern |
| Divendres | Bases de dades i configuracions crítiques | Incremental | NAS / Disc dur extern |
| Dissabte | Còpia diferencial setmanal de BD i dades crítiques clients | Diferencial | NAS / Disc dur extern \+ Cloud |
| Diumenge | Còpia completa mensual (si toca) de tota la informació crítica | Completa | Cloud / Cinta LTO |

 

3\)      Elecció de Mitjans i Ubicació (Regla 3-2-1)

| Element | Mitjà | Ubicació / Responsable | Justificació |
| ----- | ----- | ----- | ----- |
| **Mitjà 1 (Local)** | NAS intern o Disc dur extern | Instal·lacions de l’empresa, gestionat pel departament IT | Permet restauracions ràpides de la còpia més recent, assegurant disponibilitat immediata. |
| **Mitjà 2 (Extern)** | Cloud (Azure / Google Cloud) \+ Disc dur extern fora del lloc | Ubicació remota o proveïdor de cloud; responsable: IT | Garanteix còpia fora de lloc, protecció davant robatoris, incendis o desastres locals. Compliment de la regla 3-2-1. |
| **Ubicació Fora de Lloc** | Cloud / Disc dur extern en lloc remot | Proveïdor cloud o emmagatzematge físic extern | Manté la còpia off-site, assegurant redundància i seguretat extra de dades crítiques. |

4\)      Estratègia de Recuperació (RTO/RPO)

Com es garanteix que les dades de Comptabilitat/Clients compleixen amb el requisit de RPO (4 hores) i RTO (4 hores).

| Tipus de Dades | RPO (Recovery Point Objective) | RTO (Recovery Time Objective) | Estratègia |
| ----- | ----- | ----- | ----- |
| Bases de dades crítiques i comptabilitat | 4 hores | 4 hores | Les còpies incrementals cada 4 hores garanteixen el mínim de pèrdua de dades (RPO). Restauració ràpida des de NAS o disc dur extern compleix l’RTO. |
| Configuracions i dades crítiques clients | 24 hores | 4 hores | Còpies setmanals i cloud permeten restauració completa en cas de desastre, assegurant disponibilitat segons els requisits de l’empresa. |
| Dades no crítiques | 7 dies | 24-48 hores | Còpies setmanals i mensuals, prioritzant eficiència de recursos i protecció bàsica. |
