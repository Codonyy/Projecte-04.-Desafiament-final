
# T07: Accés Remot – Serveis d’Assistència Remota  
## Tasca en Parelles

## Breu descripció
Fins ara s’han treballat eines d’administració remota de servidors com SSH, RDP i VNC. Tot i això, una part molt important de l’activitat d’EverPia és el **suport directe a l’usuari final (Helpdesk)**.

Quan un client truca amb incidències habituals com:
- "El PDF no s’obre"
- "Ha desaparegut una icona"
- "La impressora no imprimeix"

no és viable demanar-li que configuri una VPN o obri ports del router. En aquests casos cal una eina d’assistència remota **sota demanda**, que sigui:
- ràpida,
- fiable,
- segura,
- funcional fins i tot en xarxes restrictives.

La direcció d’EverPia ha decidit **estandarditzar una eina oficial** per al suport immediat. L’objectiu d’aquesta tasca és analitzar el mercat, seleccionar la millor solució i crear la documentació oficial per a tècnics i clients.

---

# Fase 1: Anàlisi Comparativa i Selecció de la Solució

## Objectiu
Analitzar diferents eines d’assistència remota i proposar la millor opció per a EverPia mitjançant un breu informe comparatiu.

## Tasques
### Investigació d’eines
S’han d’analitzar com a mínim quatre solucions populars:
- TeamViewer  
- AnyDesk  
- Google Remote Desktop  
- Una quarta eina a elecció de l’equip

### Taula comparativa
Crear una taula que avali cada eina segons els criteris següents:

#### Facilitat d’ús (per al client)
- Requereix instal·lació?
- És portable?
- Facilitat per compartir l’ID de sessió amb el tècnic.

#### Disponibilitat (Sistemes Operatius)
- Compatibilitat amb Windows
- Compatibilitat amb macOS
- Compatibilitat amb Linux  
*(Criteri clau per a EverPia, que dona suport a entorns mixtos)*

#### Model de preu (Llicència)
- És gratuïta per a ús comercial?
- Cost de la llicència per tècnic.
- Limitacions de la versió gratuïta.

### Recomanació final
A partir de la taula comparativa, cal:
- Recomanar oficialment una eina.
- Justificar la decisió basant-se en l’equilibri entre facilitat d’ús, funcionalitat i cost.

---

# Fase 2: Creació de les Guies d’Ús (Documentació)

Un cop seleccionada l’eina, s’ha de crear la documentació oficial. Aquesta fase és crítica i es divideix en dues guies diferenciades.

---

## Guia 1: Manual per al Tècnic (Intern d’EverPia)

### Objectiu
Formar futurs becaris i tècnics en l’ús correcte de l’eina d’assistència remota.

### Contingut mínim
La guia ha d’incloure captures de pantalla i explicar:
- Com instal·lar la versió completa o tècnica de l’eina.
- Com iniciar una sessió de suport.
- Com gestionar funcions clau:
  - Transferència d’arxius
  - Canvi de pantalla
  - Reinici remot
- Bones pràctiques de seguretat:
  - Tancar sempre la sessió
  - No desar credencials dels clients
  - Verificar permisos abans de connectar-se

---

## Guia 2: Manual per al Client (Usuari Final)

### Objectiu
Ajudar l’usuari final a permetre l’assistència remota de manera ràpida, segura i sense coneixements tècnics.

### Contingut mínim
La guia ha de ser molt visual, clara i senzilla, amb captures de pantalla detallades:
- Enllaç o mètode per descarregar el mòdul de **Quick Support** (o equivalent).
- Accions exactes que ha de fer l’usuari (on clicar).
- Com identificar i comunicar l’ID de sessió i la contrasenya (si existeix).
- Com acceptar la sol·licitud de connexió del tècnic.

---
