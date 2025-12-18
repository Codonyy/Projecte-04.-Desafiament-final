
# Guia d'Accés i Configuració d'Escriptori Remot (RDP) – EverPia IT Support

Aquesta guia documenta el procés de configuració i connexió mitjançant RDP (Remote Desktop Protocol) entre un client (usuari final) i un suport tècnic. El procediment s'ha realitzat seguint les directrius de la tasca **T06: Accés remot. Escriptori remot (RDP)**.

---

## Objectiu

Permetre la connexió remota entre un equip client i un equip de suport, per tal de visualitzar i controlar l'escriptori remot i resoldre incidències en temps real.

---

## Pas 1: Habilitar l'Escriptori Remot a l'Equip Client (Windows)

- Accedir a **Configuració → Sistema → Escriptori remot**.
- Activar l’opció **Escriptori remot**.
- Afegir usuaris amb accés remot (per exemple, l'usuari *Mati* o *Marti*).
- Confirmar amb **Acceptar**.

**Nota:** Cal assegurar-se que l'equip client té un nom identificable a la xarxa (ex: `DESKTOP-BROTAV4`).

---

## Pas 2: Configurar l'Escriptori Remot a l'Equip de Suport (GNU/Linux amb Zorin/GNOME)

- Obrir **Configuració → Compartir**.
- Activar **Compartició d'escriptori** i **Inici de sessió remot**.
- Configurar els detalls de connexió:
  - **Nom de l'equip:** `usuari-VirtualBox`
  - **Port RDP:** `3389` (per defecte) o `3390` (segons configuració)
  - **Usuari i contrasenya locals**

---

## Pas 3: Connexió des del Client de Suport (Remmina o Client RDP)

- Obrir **Remmina** (client d’escriptori remot per a Linux).
- Crear una nova connexió **RDP** amb els següents paràmetres:
  - **Equip:** `DESKTOP-BROTAV4.local`
  - **Usuari:** `Marti`
  - **Contrasenya:** la del compte remot
- Acceptar el certificat de seguretat si es demana (encara que no estigui signat per una entitat de confiança).
- Iniciar la connexió.

---

## Pas 4: Validació i Resolució d'Incidències

- Un cop connectat, es pot visualitzar i controlar l'escriptori remot.
- Es pot comprovar la connectivitat amb `ping` i `ip a` des del terminal.
- En cas d'errors de certificat, es pot continuar igualment en entorns de prova (PoC).
