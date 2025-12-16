
# Sistema de Còpies de Seguretat amb Duplicity

## 📋 Prova de concepte

### 1. Crear VM Ubuntu Server amb disc addicional (10 GB)

He creat una màquina virtual Ubuntu Server i afegit un disc dur addicional de 10 GB per emmagatzemar les còpies de seguretat.

---

### 2. Formatar en XFS i muntar a /media/backup

He utilitzat l'eina `parted` per crear una partició GPT al disc addicional i formatar-la amb el sistema de fitxers XFS. Després l'he muntat al directori `/media/backup`.

---

### 3. Instal·lar Duplicity

He instal·lat el paquet `duplicity` des dels repositoris d'Ubuntu, que és una eina de còpies de seguretat incremental amb suport per a xifrat.

---

### 4. Crear usuaris i arxius de prova

He creat dos usuaris (`usuari1` i `usuari2`) i diversos fitxers binaris de prova de 10 MB cadascun al directori `/home` per tenir dades reals per a les còpies.

---

### 5. Fer còpia completa i restauració

He executat Duplicity per fer una còpia completa del directori `/home` al disc muntat `/media/backup`, utilitzant una passphrase per xifrar les dades.

---

### 6. Comprovar còpia incremental

Després d'afegir un nou fitxer, he fet una còpia incremental que només ha capturat els canvis des de la còpia completa. He verificat l'estat de les còpies amb `duplicity collection-status`.

---

## 🤖 Automatització

### 1. Script fullbackup.sh per còpia completa (diumenge 23:00)

He creat un script bash `/usr/local/bin/fullbackup.sh` que executa una còpia completa, muntant automàticament el disc de backup, fent la còpia, i desmuntant-lo després.

---

### 2. Script incrementalbackup.sh per còpies incrementals (dilluns-dissabte 23:00)

He creat un segon script `/usr/local/bin/incrementalbackup.sh` per a còpies incrementals diàries, que només copia els canvis des de l'última còpia.

---

### 3. Ús de variable d'entorn PASSPHRASE per seguretat

En ambdós scripts, he utilitzat:

```bash
export PASSPHRASE="contrasenya_forta"
