
Projecte04: Servidor NFS
DevOptimize Solutions – Proof of Concept
🧩 Descripció del projecte

DevOptimize Solutions és una startup de desenvolupament de programari que treballa exclusivament amb Linux. Actualment pateixen un problema greu de desorganització: cada desenvolupador té còpies locals del codi i dels recursos del projecte, provocant inconsistències, conflictes de versió i una pèrdua d’eficiència constant.

La solució proposada és desplegar un servidor de fitxers centralitzat amb NFS (Network File System). El client no disposa d’un entorn d’autenticació centralitzada, així que la gestió d’usuaris i permisos es farà de manera local a cada màquina.

Aquest projecte mostra una demostració funcional que permet al client visualitzar tant el funcionament correcte de NFS com les seves limitacions.

🚀 Objectius de la demostració

Configurar un servidor NFSv3 amb Ubuntu Server 24.04.

Configurar un client Linux amb Zorin OS 18.

Crear estructura d’usuaris, grups i permisos.

Demonstrar el control d’accés via /etc/exports i permisos del sistema.

Mostrar problemes i solucions relacionats amb root_squash i no_root_squash.

Configurar muntatge automàtic via /etc/fstab.

🏗️ Fases del Projecte
Fase 1: Preparació de l'entorn

Es creen dues màquines virtuals:

🔧 Servidor

Sistema: Ubuntu Server 24.04 LTS

Idioma: Espanyol

SSH: Instal·lat durant la configuració

Xarxes:

NAT (accés a Internet)

Host-only (comunicació amb el client)

💻 Client

Sistema: Zorin OS 18

Xarxes: NAT + Host-only

Tots dos sistemes es connecten entre ells i s’actualitzen amb les últimes versions.

Fase 2: Preparació del servidor
👥 Creació de grups

devs

admins

👤 Creació d’usuaris

dev01 (grup: devs)

admin01 (grup: admins)

⚠️ Important: Cal replicar els mateixos usuaris i grups al client o assegurar que els UID i GID coincideixen.

📁 Directori de treball

/srv/nfs/dev_projects

/srv/nfs/admin_tools

🔐 Permisos

Propietari: root

Grup: devs o admins segons el cas

Objectiu:

Els desenvolupadors tenen control total sobre dev_projects

Els administradors tenen control sobre admin_tools

Finalment, s’instal·len els paquets NFS i es configura /etc/exports.

Fase 3: Exportació d'Administració – El dilema del root_squash
🧪 Prova 1 – L’error habitual

Exportar /srv/nfs/admin_tools amb:

rw,sync


Muntar al client: /mnt/admin_tools

Com a root, crear un fitxer al recurs NFS.

Verificar propietari del fitxer.

📌 Resultat: El fitxer NO pertany a root.
📘 Explicació: NFS aplica root_squash, convertint root (UID 0) en nobody.

🧪 Prova 2 – La Solució

Afegir a l’exportació l’opció:

no_root_squash


Desmuntar i remuntar el recurs.

Com a root, crear un fitxer de nou.

📌 Resultat: Ara sí, el fitxer pertany a root.
📘 Explicació: no_root_squash desactiva la protecció i preserva UID 0.

Fase 4: Exportació de Desenvolupament – Permisos rw vs ro

Editar /etc/exports per permetre:

A la xarxa 192.168.56.0/24 → rw

A la IP 192.168.56.100 → ro

Proves:

Com a dev01, muntar /mnt/dev_projects i escriure → Funciona.

Canviar IP del client a 192.168.56.100 → només lectura.

Canviar usuari a admin01 → no pot escriure (no pertany a devs).

Fase 5: Muntatge Automàtic amb /etc/fstab

Afegir entrades com:

<server_ip>:/srv/nfs/admin_tools   /mnt/admin_tools   nfs   defaults   0  0
<server_ip>:/srv/nfs/dev_projects   /mnt/dev_projects  nfs   defaults   0  0

✔️ Proves:

Executar mount -a → comprovar que no hi ha errors

Reiniciar el client → els recursos es munten automàticament

🏁 Conclusió i Recomanacions

Aquesta prova de concepte demostra el funcionament bàsic d’un servidor NFS sense autenticació centralitzada. Tot i així, aquest model té limitacions importants:

🔒 Recomanacions de millora

Implementar autenticació centralitzada:

LDAP

FreeIPA

Active Directory (via compatibilitat Samba)

Gestionar permisos de manera consistent entre equips.

Utilitzar NFSv4 amb suport d’autenticació Kerberos.

Considerar alternatives més segures:

Samba + ACLs

Git per control de versions

Automatitzar provisionament d’usuaris amb Ansible, Puppet o similars.
