# Informe tècnic: Selecció d’un SAI per una empresa client
**Data:** 02/10/2025  
**Autor:** Víctor Rodríguez Amills | SMX2B | Seguretat informàtica  

<img src="img/logo_fp.png" alt="Logo de FP de Escola Pia Santa Anna" width="150">

---

## Índex
1. [Introducció](#1-introducció)  
2. [Inventari d’equips](#2-inventari-dequips)  
3. [Càlcul de potència](#3-càlcul-de-potència)  
4. [Autonomia estimada requerida](#4-autonomia-estimada-requerida)  
5. [Models cercats i comparats](#5-models-cercats-i-comparats)  
6. [Justificació de la selecció del SAI](#6-justificació-de-la-selecció-del-sai)  

---

## 1. Introducció
L’empresa **TecnoGestió S.L.**, dedicada a la gestió documental i assessorament informàtic, té un petit despatx amb:  

- 4 ordinadors de sobretaula  
- Una impressora-fotocopiadora multifunció (similar a les que té l’escola)  
- Un router d’accés a Internet  

Davant les constants incidències amb el subministrament elèctric a la zona, la direcció ha decidit adquirir un **SAI** per garantir la continuïtat del servei i protegir els equips.

---

## 2. Inventari d’equips
Encara que disposen de 4 ordinadors de sobretaula, una impressora-fotocopiadora multifunció i un router d’accés a Internet, **només es connectaran els ordinadors de sobretaula amb els seus perifèrics i el router al SAI**, ja que la impressora no és essencial davant d’una incidència elèctrica.

| Dispositiu                         | Quantitat | Consum per unitat (W) | Consum total (W) |
|------------------------------------|-----------|----------------------|-----------------|
| Ordinador d’oficina + pantalla + perifèrics | 4         | 500 W                | 2000 W          |
| Router                              | 1         | 20 W                 | 20 W            |
| **Total**                           |           |                      | **2020 W**      |

---

## 3. Càlcul de potència
- Potència eficaç: 2020 W  
- Potència aparent: 2885 VA (2020 W / 0,7)  
- Amb marge de seguretat del 20%: **3.462 VA**  

---

## 4. Autonomia estimada requerida
El client requereix **10 minuts d’autonomia** per poder apagar els equips correctament o guardar treballs.  

Fórmules per al càlcul de capacitat de la bateria:  

```
Temps = (Capacitat bateries * Eficiència / Potència (VA)) * 60
Capacitat bateries = (Temps * Potència (VA) / Eficiència) / 60
```

Exemples amb models proposats:  

- **SAI 4000 VA**: (10 * 4000 / 0,7) / 60 = 952,4 Ah  
- **SAI 7500 VA**: (10 * 7500 / 0,7) / 60 = 1785,7 Ah  

---

## 5. Models cercats i comparats

| Característica     | SLC-4000 TWIN PRO3                  | SLC-4000 TWIN RT3                     | SLC-7,5 CUBE4                     |
|-------------------|------------------------------------|--------------------------------------|----------------------------------|
| Marca             | Salicru                            | Salicru                               | Salicru                           |
| Tipus             | On-line monofàsic (torre)          | On-line monofàsic (torre/rack convertible) | On-line trifàsic (3F+N)          |
| Potència          | 4000 VA                            | 4000 VA                               | 7500 VA                           |
| Sortida           | ±1% tensió / THDv <1% lineal       | ±1% tensió / THDv <1% lineal         | ±1% tensió / THDv <1% lineal     |
| Rendiment         | 95% On-line / 98% Eco              | 95% On-line / 98% Eco                 | >96% On-line / fins 98% Eco      |
| Treball en paral·lel | Sí, fins a 3 equips               | Sí, fins a 3 equips                    | Sí, fins a 4 equips               |
| Dimensions        | 492x225x589 mm                     | 570x438x220 mm                        | 689x250x827 mm                    |
| Pes               | 51 kg                               | 55,6 kg                               | 88 kg                             |
| Preu estimat      | 1900 €                              | 2200 €                                 | 4600 €                            |

## 6. Justificació de la selecció del SAI
El **SAI més adequat** és el **SLC‑4000 TWIN PRO3 de Salicru**, basant-se en els següents aspectes:  

- **Potència suficient i segura:** 4 kVA cobreix àmpliament els 3.462 VA necessaris amb marge de seguretat del 20%.  
- **Autonomia adequada:** Permet apagar els equips correctament i evitar pèrdua de dades.  
- **Cost-eficiència:** Comparat amb altres models, ofereix una solució fiable a un preu raonable (1.900 €).  
- **Funcionalitats complementàries:** Rendiment elevat (95% on-line), connexió en paral·lel, comunicacions completes (USB, RS232, RJ45, HDMI, SNMP) i bateries AGM segellades amb recàrrega ràpida.  

**Conclusió:** El SLC‑4000 TWIN PRO3 equilibra necessitats tècniques, autonomia i cost, garantint la continuïtat del servei i protecció dels equips.

[Tornar a enunciat](README.md)
