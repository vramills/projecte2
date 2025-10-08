# 🧾 Proposta de domini i hosting per al client MotoBits IoT

## 1. Presentació del client

### Breu descripció del negoci
MotoBits IoT és una startup tecnològica de Mataró dedicada al desenvolupament de solucions IoT (Internet of Things) per al monitoratge intel·ligent de vehicles i dispositius connectats. El seu públic objectiu són empreses i professionals del sector tecnològic que busquen integracions eficients i dades en temps real per millorar processos i rendiment.

### Objectius principals de la web
La web ha de:
- Crear una imatge professional i innovadora de l’empresa.
- Oferir documentació tècnica SaaS i informació d’API REST per a desenvolupadors.
- Permetre la publicació d’actualitzacions i notícies del producte.
- Garantir una base escalable i segura per al creixement de la plataforma.

### Requeriments tècnics identificats
- Suport per Node.js i API REST
- Entorn staging per a proves
- Certificat SSL i compliment del RGPD (servidors a la UE)
- CDN integrat per optimitzar la càrrega global
- Alta disponibilitat i escalabilitat

## 2. Anàlisi de dominis

### Criteris per al naming
- Identitat de marca curta i tecnològica
- Extensió professional i reconeguda al món startup (.io o .tech)
- Bona visibilitat SEO i facilitat de record
- Coherència amb la imatge digital i internacional de MotoBits

### Alternatives de dominis disponibles

| Domini        | Estat       | Preu aproximat |
|---------------|------------|----------------|
| motobits.io   | Disponible | 50 €/any       |
| motobits.tech | Disponible | 60 €/any       |
| motobits.es   | Disponible | 1 €/any        |

### Recomanació final de domini
**Domini recomanat:** `motobits.io`  
**Motiu:** L’extensió .io és molt utilitzada per startups tecnològiques i projectes SaaS. És curta, moderna i fàcil de recordar, reforçant la imatge internacional i innovadora de MotoBits IoT.

## 3. Comparativa de hostings

| Proveïdor   | Pla (Triat per Node.js) | Espai disc   | Transferència | Preu Anual (Oferta) | Preu Anual (Renovació Estimat) | Pros Principals                                       | Contres                                           |
|------------|------------------------|-------------|---------------|-------------------|-------------------------------|-----------------------------------------------------|--------------------------------------------------|
| SiteGround | GrowBig                | 20 GB SSD   | Il·limitada   | ~66 € (5,49 €/mes) | ~336 € (27,99 €/mes)         | Rendiment i velocitat superiors per a l'API, entorn staging inclòs | Preu de renovació prohibit per a una startup amb pressupost ajustat |
| Hostinger  | Business               | 200 GB NVMe | 600 GB/mes    | ~45 € (3,79 €/mes) | ~156 € (12,99 €/mes)         | Preu assequible, tecnologia ràpida (NVMe), gran capacitat d'emmagatzematge | Suport Node.js menys gestionat, ubicació sense datacenter a Espanya |
| OVHcloud   | Web Cloud              | 250 GB SSD  | Il·limitada   | ~85 € (6,64 €/mes) | ~85 € (preu estable)         | Suport natiu i gestionat per a Node.js, preu estable i baix a llarg termini, compliment RGPD | Suport percebut més lent que SiteGround       |
| IONOS      | Developer              | 50 GB SSD   | Il·limitada   | ~65 € (5,42 €/mes) | ~132 € (11 €/mes)            | Preu de renovació baix i previsible, ideal per al pressupost | Configuració de Node.js pot ser més complexa   |

## 4. Checklist de requeriments complerts
- SSL inclòs
- Backups automàtics
- Correu corporatiu (opcional)
- CDN integrat
- Escalabilitat i entorn staging
- Compliment del RGPD i servidors UE

## 5. Recomanació final
- **Hosting escollit:** OVHcloud Web Cloud – Pla Professional amb suport Node.js  
- **Domini recomanat:** motobits.io  

**Justificació de la decisió:**  
Aquesta combinació ofereix un bon equilibri entre rendiment, compatibilitat tècnica i escalabilitat. OVH proporciona serveis europeus amb RGPD complert, CDN integrat i SSL gratuït, ideals per a una startup com MotoBits IoT.  
El domini .io transmet una imatge tecnològica i global, reforçant la identitat moderna de la marca. En conjunt, és una opció fiable, segura i preparada per al creixement futur de l’empresa.

## 6. Conclusions

### Criteris decisius:
- Compatibilitat amb Node.js i API REST
- Escalabilitat i rendiment alt
- Servidors europeus i compliment RGPD
- Suport tècnic fiable i continu
- Domini curt i internacionalitzable (.io)

### Per què aquesta proposta és la millor opció:
La solució escollida combina tecnologia, seguretat i rendiment. El domini `motobits.io` reforça la imatge moderna i global, mentre que el hosting OVH Web Cloud garanteix una infraestructura estable i escalable, essencial per a una startup IoT en expansió.

[Tornar a enunciat](README.md)
