

# T02: DPR - Còpies de Seguretat (Cas Pràctic)

## 📌 Descripció Breu
Aquest projecte mostra la implementació pràctica d'una política de còpies de seguretat per al client **Muntatges i Serveis Tècnics SL**, seguint l'estudi previ realitzat. Inclou guies tècniques i proves de concepte per qualificar el personal en la implantació del pla de còpies.

---

## 🎯 Objectius
- Implementar còpies de seguretat en entorns **Windows** i **Linux**.
- Aplicar l'esquema **3-2-1** per garantir redundància i seguretat.
- Automatitzar processos amb **scripts** i **cron**.

---

## 📂 Contingut del projecte

### ✅ Part 1: Còpia de seguretat en equips Windows
- Excepció per a l'equip del director (Windows 11).
- Política **3-2-1**:
  - **Còpia local** en disc secundari.
  - **Còpia al núvol** (Google Drive) amb **Duplicati**.
- **Prova de concepte**:
  - Crear VM Windows 11 amb dos discos (OS + secundari 10 GB).
  - Configurar còpies horàries al disc secundari i còpia diària (18:00) a Google Drive.
  - Documentar:
    - Instal·lació de **Duplicati**.
    - Configuració dels plans de còpia.
    - Restauració des de disc i des del núvol.

---

### ✅ Part 2: Còpia de seguretat en servidor Linux
- Eina: **Duplicity** + **cron**.
- **Prova de concepte**:
  - Crear VM Ubuntu Server amb disc addicional (10 GB).
  - Formatar en **XFS** i muntar a `/media/backup`.
  - Instal·lar **Duplicity**.
  - Crear usuaris i arxius de prova.
  - Fer còpia completa i restauració.
  - Comprovar còpia incremental.
- **Automatització**:
  - Script `fullbackup.sh` per còpia completa (diumenge 23:00).
  - Script `incrementalbackup.sh` per còpies incrementals (dilluns-dissabte 23:00).
  - Ús de variable d'entorn `PASSPHRASE` per seguretat.
  - Muntar/desmuntar unitat abans/després de cada còpia.

---

## 🛠️ Requisits
- **Windows 11** VM amb dos discos.
- **Ubuntu Server** VM amb disc addicional.
- Connexió a **Google Drive** (compte extern).
- Eines:
  - Duplicati
  - [Duplicity](http://manpages.ubuntu.com/manpages/trusty/man1/dupliccati
- [Creació d'arxius amb fsutil (Windows)](https://waytoit.wordpressa en Linux](https://waytoit.wordpress.com/2015/03/21/creando-archivos-de-prueba-encom/programar-tareas-en-linux-usando-crontab clone https://github.com/usuari/nom-repositori.git
