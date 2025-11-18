
# T01: DRP: còpies de seguretat. Estudi cas client (treball cooperatiu)

## Muntatges i Serveis Tècnics SL

## Introducció
La primera hora el responsable de seguretat presenta el tema de les còpies de seguretat a partir d’un material didàctic. Tot seguit, es treballaran els aspectes principals mitjançant una dinàmica cooperativa.

## Presentació del Cas Client
"Muntatges i Serveis Tècnics SL" és una empresa dedicada a la instal·lació i manteniment d’equips industrials.

### Infraestructura Tècnica
- **Servidor de Fitxers (Ubuntu Server):**
  - Documents de Projectes: 300 GB (creixement moderat)
  - Bases de Dades (Comptabilitat i Clients): 20 GB (canvi constant)
  - Carpetes Personals: 100 GB
- **10 Equips Clients (Windows 10/11):** Alguns usuaris guarden dades temporals a *Documents*.
- **Connexió a Internet:** Fibra òptica simètrica de 600 Mbps.

### Requisits de Recuperació
- **RTO:** Dades de Comptabilitat/Clients disponibles en menys de 4 hores.
- **RPO:**
  - General: fins a 24 hores
  - Comptabilitat/Clients: màxim 4 hores de pèrdua
- **Retenció:** Històric mínim d’1 mes.

---

## Fase 1: Treball Individual

### 1. Què copiar? (Priorització)
- Identificar les dades més crítiques del servidor.
- Valorar si cal copiar els 10 equips clients i justificar-ho.

### 2. Periodicitat i Tipus de Còpia
- Proposar un calendari de còpies (diari, setmanal, mensual).
- Seleccionar tipus de còpia:
  - Completa
  - Diferencial
  - Incremental

### 3. Mitjans i Ubicació
- Seleccionar el mitjà de còpia: discs externs, NAS, Cloud, cintes.
- Aplicar la **Regla 3-2-1** (3 còpies, 2 mitjans, 1 fora de lloc).

---

## Fase 2: Treball per Parelles

### 1. Discussió i Consens
Comparació i unificació de respostes individuals.

### 2. Proposta Unificada (Esquema 3-2-1)

| Element | Proposta de la Parella | Justificació |
|---------|--------------------------|---------------|
| **Dades Crítiques** | | |
| **Periodicitat (BD)** | | |
| **Tipus de Còpia (BD)** | | |
| **Mitjà 1 (Local)** | | |
| **Mitjà 2 (Extern)** | | |

---

## Fase 3: Treball en Grup

### 1. Debat i Selecció
Cada parella presenta la seva proposta. El grup analitza:
- Cost
- Temps de recuperació
- Seguretat
- Simplicitat

### 2. Política Final
Redacció de la Política de Còpies de Seguretat definitiva.

---

# Document Final (Fase 3)

## 1. Dades Objecte de Còpia
- Quines dades es copien.
- Freqüència de còpia.
- Separació entre:
  - Servidor / Clients
  - Dades crítiques / no crítiques

---

## 2. Cronograma Setmanal Detallat

| Dia | Dades | Tipus de Còpia | Mitjà |
|------|--------|----------------|--------|
| Dilluns | | | |
| Dimarts | | | |
| Dimecres | | | |
| Dijous | | | |
| Divendres | | | |
| Dissabte | | | |
| Diumenge | | | |

---

## 3. Elecció de Mitjans i Ubicació (Regla 3-2-1)
- **Mitjà 1 (Local):** Tipus concret (NAS, disc USB, etc.).
- **Mitjà 2 (Extern):** Tipus i proveïdor (Cloud, LTO, etc.).
- **Ubicació**
