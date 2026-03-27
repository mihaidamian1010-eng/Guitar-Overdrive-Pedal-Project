# Ibanez Tube Screamer Clone - PCB & PCBA Design

Acesta este un proiect hardware complet open-source care replică topologia faimoasei pedale de efecte **Ibanez Tube Screamer (TS808/TS9)**. 
Proiectul a fost desenat de la zero în KiCad și este optimizat special pentru fabricație automatizată (PCBA - Printed Circuit Board Assembly).

## 🌟 Caracteristici Principale
* **Tehnologie SMD:** Toate componentele pasive sunt în format **0603**, iar circuitul integrat (NJM4558) folosește capsula **SOIC-8**. Designul este gândit pentru eficiență și asamblare robotizată (*Pick and Place*).
* **Off-board Wiring:** Potențiometrele și mufele Jack folosesc conexiuni tip Pin Header (2.54mm) pentru a fi montate mecanic pe carcasa metalică și cablate ulterior, permițând flexibilitate în alegerea cutiei (ex: 1590B).
* **Zgomot Redus (Low Noise):** Implementarea unor planuri de masă (GND Pour) pe ambele fețe ale cablajului (Top & Bottom) pentru o ecranare electromagnetică superioară și reducerea zgomotului de fond.
* **Gata de Fabricare:** Proiectul include setul complet de fișiere de fabricație (Gerber, Drill, BOM, CPL).

---

## 📸 Prezentare Vizuală

### Randare 3D a Cablajului
![3D Render](https://cdn.discordapp.com/attachments/947587161358737498/1487085522697588766/image.png?ex=69c7dbd1&is=69c68a51&hm=5ccb127032fb3ded1cbe390651e73cfb145a509e59e39417e37487a6ef0a9994&)
*(Notă: Placa asamblată, pregătită pentru integrarea în carcasă)*

### Schema Electrică
![Schematic](link_catre_schema.png)

---

## 🧠 Arhitectura Circuitului
Designul respectă topologia clasică în 4 etaje de procesare a semnalului:

1. **Input Buffer (2N3904):** Repetor pe emitor pentru adaptarea impedanței. Preia semnalul de impedanță mare al dozelor chitarei și previne pierderea frecvențelor înalte.
2. **Clipping Amplifier (NJM4558 + 1N4148):** Inima pedalei. Generează distorsiunea de tip *soft-clipping* prin plasarea diodelor antiparalel direct în bucla de reacție a amplificatorului operațional.
3. **Tone Control (NJM4558):** Filtru activ RC utilizat pentru ajustarea răspunsului în frecvență (mixajul între frecvențele tăioase și cele calde).
4. **Output Buffer (2N3904):** Scade impedanța de ieșire pentru a menține integritatea semnalului pe cabluri lungi, spre amplificator.

---

## 📂 Structura Repository-ului
* `*.kicad_sch` & `*.kicad_pcb` -> Fișierele sursă editabile (necesită KiCad 8.0 sau mai nou).

* `Arhiva .zip` -> Conține tot necesarul pentru producători (JLCPCB / PCBWay).
[Overdrive_Pedal.zip](https://github.com/user-attachments/files/26306992/Overdrive_Pedal.zip)
---

## 🛠️ Cum să fabrici această placă
Proiectul este gândit pentru a fi trimis direct la o fabrică de cablaje care oferă servicii de asamblare:
1. Mergi pe site-ul producătorului (ex: JLCPCB).
2. Încarcă arhiva `.zip` generată din KiCad.
3. Bifează opțiunea **PCBA** (Asamblare componente).
4. Sistemul va citi automat fișierele BOM și CPL/POS pentru a plasa componentele SMD pe placă.
5. La primirea pachetului fizic, lipiți doar firele (Off-board wiring) pentru `RV1`, `RV2`, `RV3` și mufele Jack `J1`, `J2`, `J3`.
   
