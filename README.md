# 🖥️ 16-bit General Purpose Processor & Calculator ASIP

Acest depozit conține proiectarea și implementarea unui procesor pe **16 biți** de tip **ASIP (Application-Specific Instruction set Processor)**, optimizat pentru funcții de calculator de buzunar. Proiectul include arhitectura hardware completă scrisă în **VHDL**, un set de instrucțiuni personalizat și utilitare de asamblare.

## 📋 Specificații Tehnice
* **Lățime Date/Instrucțiuni:** 16 biți.
* **Registre:**
    * **Acumulator (A):** Registru principal pe 16 biți pentru operații.
    * **Registre Generale (X, Y):** Utilizate pentru operanzi.
    * **Program Counter (PC) & Stack Pointer (SP):** Gestionarea fluxului și a stivei.
* **Unitate de Flag-uri:** Z (Zero), N (Negative), C (Carry), O (Overflow).
* **Memorie:** Gestionare separată pentru instrucțiuni și date (Arhitectură de tip Harvard).

---

## 🏗️ Arhitectura Datapath
Procesorul utilizează un flux de date structurat pentru a executa instrucțiunile în mai multe etape (Fetch, Decode, Execute, Write-back):
* **Unitatea de Control (FSM):** Coordonează semnalele de control pentru memorie și regiștri.
* **ALU:** Execută operații aritmetico-logice între acumulator și registrele X/Y sau valori imediate.
* **Sign Extend:** Extinde valorile imediate de la 9 la 16 biți pentru consistența datelor.
---

## 📜 Set de Instrucțiuni (ISA)
Procesorul suportă o gamă variată de operații, organizate pe două formate principale (ALU/Memory și Branch):
* **Transfer de Date:** `LOAD`, `STORE`, `MOV`, `PUSH`, `POP`.
* **Aritmetice & Logice:** `ADD`, `SUB`, `MUL`, `DIV`, `AND`, `OR`, `XOR`, `NOT`.
* **Control Flux:** `BRA` (unconditional), `BRZ/BRN/BRC/BRO` (conditional), `JMP`, `RET`.
* **Extensii Calculator (ASIP):**
    * `SQRT`: Radical din X.
    * `ABS`: Valoare absolută.
    * `NEG`: Negare.
    * `POW2`: Puterea a doua a lui X.

---

## 🛠️ Logica de Control
Funcționarea procesorului este guvernată de o tabelă de control care activează semnale specifice pentru fiecare instrucțiune:
* **MEM_RD/MEM_WR:** Activează citirea/scrierea în memoria de date.
* **ALU_IN2_SEL:** Selectează sursa operantului al doilea (X, Y, IMM sau MEM).
* **WB_DEST/WB_WE:** Definește registrul unde se scrie rezultatul și activează scrierea.

---

## 📂 Structura Proiectului
* **`src/`**: Codul sursă VHDL (ALU, Control Unit, Register File, etc.).
* **`testbench/`**: Fișiere pentru simulare (testarea procesorului și a unității ALU).
* **`tools/`**: Un asamblor scris în **Python** pentru a converti codul Assembly în cod mașină (Hex).
* **`run_sim.do` / `run_alu_test.do`**: Scripturi de automatizare pentru ModelSim.
