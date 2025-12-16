
# 🗂️ Servidor de fitxers Linux amb NFS

Aquesta guia documenta pas a pas la configuració d’un servidor NFS a Ubuntu Server i la connexió des d’un client Linux (Zorin OS). Inclou explicacions de cada acció i captures numerades.

---

## Preparació de l'entorn

### 1. Creació de grups i usuaris

Creem grups (devs, admins) per separar rols i permisos. Els usuaris dev01 i admin01 pertanyen a aquests grups, cosa que ens permet controlar qui pot accedir i modificar els recursos compartits.


### 2. Creació de directoris compartits

Definim els directoris que es compartiran via NFS. Assignem propietaris i permisos perquè només els membres dels grups corresponents puguin escriure-hi. Això garanteix seguretat i organització.


### 3. Instal·lació del servidor NFS

El paquet nfs-kernel-server és el servei que permet exportar directoris a la xarxa. Sense ell, el servidor no pot compartir carpetes amb els clients.

### 4. Configuració de les exportacions

Aquí definim quins directoris es comparteixen i amb quins permisos.

rw: lectura i escriptura

sync: sincronització immediata

no_root_squash: permet que root al client mantingui privilegis

### 5. Activació del servei

Reiniciem i habilitem el servei perquè les exportacions entrin en vigor i el servidor NFS s’executi automàticament en cada arrencada.


### 6. Verificació amb rpcinfo

Comprovem que els serveis NFS (portmapper, mountd, nfs) estan actius i escoltant als ports correctes. És una validació tècnica que el servidor funciona.


### 7. Configuració del client Linux

El client necessita el paquet nfs-common per poder muntar directoris NFS. Sense aquest paquet, no pot connectar-se al servidor.


### 8. Comprovació de les exportacions

Mostra els directoris que el servidor exporta. Ens assegura que el client veu correctament els recursos compartits.


### 9. Muntatge manual

Muntem els directoris compartits al client per accedir-hi com si fossin locals. Això permet treballar amb fitxers de manera transparent.


### 10. Muntatge automàtic amb /etc/fstab

Amb aquesta configuració, els directoris NFS es muntaran automàticament cada cop que el client reiniciï. Evita haver de muntar-los manualment.


### 11. Validació final

Reiniciem el client i comprovem que els directoris NFS apareixen muntats correctament. És la validació final que tot funciona.

### Conclusió NFS

Hem muntat un servidor NFS perquè tots tinguin els fitxers al mateix lloc.
Així evitem que cada persona tingui còpies diferents i es perdi temps.
Els grups i permisos fan que només qui toca pugui escriure o llegir.
També hem vist el tema del root_squash i com afecta al root del client.
Funciona bé, però en el futur caldria posar més seguretat i control d’usuaris.
