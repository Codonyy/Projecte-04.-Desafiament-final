
T05: Accés Remot

![][image1]

Martí Codony Sacristan  
SMXA 2n A

1\. Instal·lar SSH al servidor (Ubuntu)

Si el servidor no té SSH instal·lat, pots instal·lar-lo amb:

sudo apt install ssh

![][image2]

2\. Verificar les interfícies de xarxa

Per conèixer les adreces IP del servidor, pots executar:

ip addr show

![][image3]

empos8: té l'adreça **192.168.56.101/24** → aquesta és la IP que utilitzarem per connectar-nos via SSH.

3\. Connectar-se des d'un client Windows

Per conectarnos al ssh haurem de fer la comanda: ssh usuari@192.168.56.101

![][image4]  
![][image5]

4\. Configuració del servidor SSH (sshd\_config)

Els fitxers de configuració es troben a /etc/ssh/sshd\_config.

![][image6]

Configuracions destacades:

PermitRootLogin no → recomanat per seguretat.  
![][image7]

AllowUsers usuari → només permet connexions de l'usuari usuari.  
![][image8]  
Port per defecte: 22\.

Per aplicar canvis després d'editar el fitxer:

sudo systemctl restart ssh

![][image9]

5\. Crear nous usuaris al servidor

sudo adduser usuari2  
![][image10]

Després, si vols permetre que es connecti, has d’afegir-lo a AllowUsers al fitxer sshd\_config com hem vist anteriorment. En aquest cas no te permis per tant no es pot conectar per ssh.

![][image11]

6\. Configuració de proxy (des de Windows)

Obre Propietats d’Internet (des del Panell de Control o Configuració de xarxa).

Vés a Configuració de LAN.

Configura el servidor proxy manualment si cal (exemple: 127.0.0.1:9876 per a SOCKS).  
![][image12]  
![][image13]![][image14]

7\. Captura de trànsit SSH amb Wireshark

Client: 10.0.2.15

Servidor: 192.168.56.101

El trànsit SSH està xifrat, per tant només es veuen paquets de tipus SSH amb longituds, però no el contingut.  
![][image15]  
![][image16]

8\. Configuració d'autenticació amb claus SSH (sense contrasenya)

Generar claus SSH al client (Windows)

ssh-keygen \-t rsa

![][image17]

**Es generen dos fitxers:**

id\_rsa (clau privada) → no compartir.

id\_rsa.pub (clau pública) → es copiarà al servidor.

![][image18]

Copiar la clau pública al servidor

scp .\\.ssh\\id\_rsa.pub usuari@192.168.56.101:

![][image19]  
Configurar l'autorització al servidor

Crea el directori .ssh si no existeix:

mkdir \-p \~/.ssh  
(si ja existeix, apareixerà un missatge d'error "File exists", com es veu a la captura)

Crea o verifica el fitxer authorized\_keys:

touch .ssh/authorized\_keys  
Afegeix la clau pública al fitxer d'autoritzacions:

![][image20]

ssh usuari@192.168.56.101  
Ara hauries de poder entrar sense introduir contrasenya  
![][image21]
