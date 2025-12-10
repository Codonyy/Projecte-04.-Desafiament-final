
# Projecte04: Servidor NFS  
## DevOptimize Solutions – Proof of Concept

## Descripció del projecte
DevOptimize Solutions és una startup de desenvolupament de programari que treballa exclusivament amb Linux. Actualment tenen un problema greu d’organització: cada desenvolupador guarda còpies locals del codi i dels recursos, provocant inconsistències, conflictes de versions i pèrdues d’eficiència.

La solució proposada és desplegar un servidor de fitxers centralitzat amb NFS (Network File System). Com que el client no disposa d’un sistema d'autenticació centralitzat, la gestió d’usuaris i permisos es farà localment a cada màquina.

Aquest projecte és una demostració funcional per mostrar el funcionament del sistema i les seves limitacions.

---

# Objectius del projecte
- Configurar un servidor NFSv3 amb Ubuntu Server 24.04.  
- Configurar un client Linux amb Zorin OS 18.  
- Crear usuaris, grups i permisos.  
- Configurar `/etc/exports` i demostrar control d’accés.  
- Mostrar diferències entre `root_squash` i `no_root_squash`.  
- Configurar muntatge automàtic amb `/etc/fstab`.

---

# Fases del Projecte

## Fase 1: Preparació de l'entorn
Es creen dues màquines virtuals:

### Servidor
- Sistema: Ubuntu Server 24.04 LTS  
- Idioma: Espanyol  
- Servei SSH instal·lat  
- Xarxes:
  - NAT (accés a Internet)
  - Host-only (comunicació amb el client)

### Client
- Sistema: Zorin OS 18  
- Xarxes: NAT + Host-only  

Ambdues màquines s’actualitzen i es comprova la comunicació entre elles.

---

## Fase 2: Preparació del servidor

### Creació de grups
- devs  
- admins

### Creació d’usuaris
- dev01 (membre de devs)  
- admin01 (membre de admins)

Nota: Cal replicar usuaris i grups al client o assegurar que UID i GID coincideixen.

### Creació de directoris
- `/srv/nfs/dev_projects`  
- `/srv/nfs/admin_tools`

### Permisos
- Propietari: root  
- Grup assignat segons directori  
- Objectius:
  - Els desenvolupadors tenen control total sobre `dev_projects`
  - Els administradors tenen control sobre `admin_tools`

S’instal·len els paquets NFS i es prepara `/etc/exports`.

---

## Fase 3: Exportació d'Administració – root_squash

### Prova 1: Error habitual
1. Exportar `/srv/nfs/admin_tools` amb: `rw,sync`.  
2. Muntar al client a `/mnt/admin_tools`.  
3. Com a root del client, crear un fitxer.  
4. Comprovar el propietari.

Resultat: el fitxer no pertany a root.  
Explicació: NFS aplica `root_squash`, convertint root en `nobody`.

### Prova 2: Solució
1. Afegir a l’exportació l’opció `no_root_squash`.  
2. Desmuntar i remuntar.  
3. Crear un fitxer com a root.

Resultat: root passa a ser propietari real.  
Explicació: `no_root_squash` desactiva la conversió de UID 0.

---

## Fase 4: Exportació de Desenvolupament – permisos rw vs ro
Es configura `/etc/exports` perquè:

- La xarxa 192.168.56.0/24 tingui permisos d'escriptura (rw).  
- La IP 192.168.56.100 tingui només lectura (ro).  

### Proves
1. Com a dev01, muntar `/mnt/dev_projects` i escriure-hi: funciona.  
2. Canviar la IP del client a 192.168.56.100: només lectura.  
3. Canviar a admin01 i provar d'escriure: no pot, perquè no és membre del grup devs.

---

## Fase 5: Muntatge automàtic amb /etc/fstab
Afegir entrades com:

<server_ip>:/srv/nfs/admin_tools /mnt/admin_tools nfs defaults 0 0
<server_ip>:/srv/nfs/dev_projects /mnt/dev_projects nfs defaults 0 0


### Comprovacions
- Executar `mount -a` per provar les entrades.  
- Reiniciar el client i verificar que els recursos es munten automàticament.

---

# Conclusió
Aquesta prova de concepte demostra el funcionament d’un servidor NFS configurat segons les necessitats del client. Tot i així, la solució presenta limitacions importants en termes de seguretat i gestió d’usuaris.

## Recomanacions de millora
- Implementar un sistema d’autenticació centralitzada (LDAP, FreeIPA, AD).  
- Migrar a NFSv4 amb suport Kerberos.  
- Millorar la gestió d’usuaris i permisos amb eines centralitzades.  
- Considerar solucions alternatives per al control de versions (Git).  
