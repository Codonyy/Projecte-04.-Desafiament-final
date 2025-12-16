
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
