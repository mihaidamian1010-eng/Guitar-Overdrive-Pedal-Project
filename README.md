# Guitar-Overdrive-Pedal-Project

# Ibanez Tube Screamer Clone - PCB Design in KiCad

Acest repository conține proiectarea completă (schemă electrică și cablaj imprimat) pentru o clonă a legendarei pedale de efecte pentru chitară, Ibanez Tube Screamer (TS808/TS9). 

Proiectul a fost realizat de la zero în **KiCad 8** (sau versiunea ta) și este optimizat pentru asamblare automatizată (PCBA) folosind componente de suprafață (SMD).

## 📌 Obiectivele Proiectului
* **Reverse Engineering & Analiză:** Înțelegerea și recrearea unuia dintre cele mai faimoase circuite de overdrive din istoria muzicii.
* **Design pentru Fabricație (DFM):** Trecerea de la componente clasice THT la componente SMD (format 0603) pentru a permite asamblarea robotizată (Pick and Place).
* **Organizare Hibridă:** Utilizarea conectorilor de tip Pin Header pentru interfațarea componentelor mecanice (potențiometre și mufe Jack) montate pe carcasa metalică.

---

## 🧠 Arhitectura Circuitului

Circuitul pedalei este împărțit în 4 blocuri funcționale principale:

1. **Input Buffer (Repetor pe emitor):** Un etaj cu tranzistorul `2N3904` care preia semnalul chitarei (impedanță mare) și îl adaptează pentru restul circuitului, prevenind pierderea frecvențelor înalte.
2. **Clipping Amplifier (Inima pedalei):** Utilizează prima jumătate a amplificatorului operațional `NJM4558`. Aici are loc distorsiunea prin limitare activă (soft clipping) folosind o pereche de diode `1N4148` montate antiparalel în bucla de reacție.
3. **Tone Control (Filtru Activ):** Utilizează a doua jumătate a cipului `NJM4558` configurată ca filtru activ RC pentru a mixa frecvențele înalte cu cele joase, permițând ajustarea "culorii" sunetului.
4. **Output Buffer:** Un al doilea etaj cu tranzistor `2N3904` care scade impedanța de ieșire, permițând semnalului să parcurgă cabluri lungi spre amplificator fără degradări.


---

## 📐 Schema Electrică (Schematic)

Schema logică a fost realizată respectând standardele de desen tehnic electronic, incluzând verificarea regulilor electrice (ERC passed) și gestionarea corectă a referințelor de alimentare (PWR_FLAGS).

![Schematic](link_catre_poza_ta_cu_schema.png)
---

## 🛠️ Stadiul Curent al Proiectului

- [x] Analiza schemei de bază (ElectroSmash)
- [x] Crearea schemei electrice în KiCad
- [x] Atribuirea amprentelor fizice (Footprints - tranzitie spre SMD 0603, SOIC-8)
- [x] Verificare ERC (Electrical Rules Checker)
- [ ] Amplasarea componentelor pe PCB (Placement / Layout)
- [ ] Rutarea traseelor de cupru (Routing & GND Pour)
- [ ] Generarea fișierelor de fabricație (Gerber & Drill files)

---

## 📂 Cum să deschizi acest proiect

Pentru a vizualiza sau edita proiectul, ai nevoie de [KiCad EDA](https://www.kicad.org/) (versiune recomandată: 8.0+).
1. Clonează acest repository: `git clone [link-ul-tau-de-github]`
2. Deschide fișierul `.kicad_pro` din folderul principal.
3. Poți naviga independent în `Schematic Editor` sau `PCB Editor`.
