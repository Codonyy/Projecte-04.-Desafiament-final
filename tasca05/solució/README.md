
# T05: Accés Remot


Martí Codony Sacristan  
SMXA 2n A

## 1\. Instal·lar SSH al servidor (Ubuntu)

Si el servidor no té SSH instal·lat, pots instal·lar-lo amb:

sudo apt install ssh

![solucio](/tasca05/img/cap1.png)

## 2\. Verificar les interfícies de xarxa

Per conèixer les adreces IP del servidor, pots executar:

ip addr show

![solucio](/tasca05/img/cap2.png)

empos8: té l'adreça **192.168.56.101/24** → aquesta és la IP que utilitzarem per connectar-nos via SSH.

## 3\. Connectar-se des d'un client Windows

Per conectarnos al ssh haurem de fer la comanda: ssh usuari@192.168.56.101

![solucio](/tasca05/img/cap3.png)
![solucio](/tasca05/img/cap4.png)

## 4\. Configuració del servidor SSH (sshd\_config)

Els fitxers de configuració es troben a /etc/ssh/sshd\_config.

![solucio](/tasca05/img/cap5.png)

Configuracions destacades:

PermitRootLogin no → recomanat per seguretat.  
![solucio](/tasca05/img/cap6.png)

AllowUsers usuari → només permet connexions de l'usuari usuari.  
![solucio](/tasca05/img/cap7.png)
Port per defecte: 22\.

Per aplicar canvis després d'editar el fitxer:

sudo systemctl restart ssh

![solucio](/tasca05/img/cap8.png)

## 5\. Crear nous usuaris al servidor

sudo adduser usuari2  
![solucio](/tasca05/img/cap9.png)

Després, si vols permetre que es connecti, has d’afegir-lo a AllowUsers al fitxer sshd\_config com hem vist anteriorment. En aquest cas no te permis per tant no es pot conectar per ssh.

![solucio](/tasca05/img/cap10.png)

## 6\. Configuració de proxy (des de Windows)

Obre Propietats d’Internet (des del Panell de Control o Configuració de xarxa).

Vés a Configuració de LAN.

Configura el servidor proxy manualment si cal (exemple: 127.0.0.1:9876 per a SOCKS).  
![solucio](/tasca05/img/cap11.png)
![solucio](/tasca05/img/cap12.png)
![solucio](/tasca05/img/cap13.png)

## 7\. Captura de trànsit SSH amb Wireshark

Client: 10.0.2.15

Servidor: 192.168.56.101

El trànsit SSH està xifrat, per tant només es veuen paquets de tipus SSH amb longituds, però no el contingut.  
![solucio](/tasca05/img/cap14.png)
![solucio](/tasca05/img/cap15.png)

## 8\. Configuració d'autenticació amb claus SSH (sense contrasenya)

Generar claus SSH al client (Windows)

ssh-keygen \-t rsa

![solucio](/tasca05/img/cap16.png)

**Es generen dos fitxers:**

id\_rsa (clau privada) → no compartir.

id\_rsa.pub (clau pública) → es copiarà al servidor.

![solucio](/tasca05/img/cap17.png)

Copiar la clau pública al servidor

scp .\\.ssh\\id\_rsa.pub usuari@192.168.56.101:

![solucio](/tasca05/img/cap18.png)
Configurar l'autorització al servidor

Crea el directori .ssh si no existeix:

mkdir \-p \~/.ssh  
(si ja existeix, apareixerà un missatge d'error "File exists", com es veu a la captura)

Crea o verifica el fitxer authorized\_keys:

touch .ssh/authorized\_keys  
Afegeix la clau pública al fitxer d'autoritzacions:

![solucio](/tasca05/img/cap19.png)

ssh usuari@192.168.56.101  
Ara hauries de poder entrar sense introduir contrasenya  
![solucio](/tasca05/img/cap20.png)

