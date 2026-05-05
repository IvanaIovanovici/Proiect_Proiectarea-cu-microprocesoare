# Microsistem cu Microprocesor Intel 8086

Acest proiect reprezintă proiectarea completă a unui microsistem bazat pe arhitectura **Intel 8086**, realizat în cadrul facultății de Automatică și Calculatoare, UPT. 

## 🛠️ Specificații Hardware
Sistemul integrează următoarele componente principale:
* **CPU**: Intel 8086 operând la o frecvență de 5 MHz. 
* **Memorie**:
    * 128 KB EPROM (2 circuite 27C512). 
    * 64 KB SRAM (circuite 62256). 
* **Interfețe de Comunicare**:
    * **Serială**: Circuit 8251 (USART) cu suport pentru conversia nivelurilor de tensiune prin MAX232. 
    * **Paralelă**: Circuit 8255 (PPI). 
* **Periferice**:
    * Minitastatură cu 9 contacte în matrice 3x3. 
    * Modul de afișare cu 7 segmente (8 ranguri).
    * Afișaj LCD (2 linii x 16 caractere). 
    * 10 LED-uri de stare.

## 🗺️ Harta de Memorie și I/O
Proiectul utilizează decodificarea adreselor prin circuitele **74x138** pentru selecția chip-urilor. 

| Periferic | Adresă (Varianta 1) | Adresă (Varianta 2) |
| :--- | :--- | :--- |
| Interfață Serială | `04D0H - 04D2H` | `05D0H - 05D2H` | 
| Interfață Paralelă | `0250H - 0256H` | `0A50H - 0A56H` | 
| Tastatură (Intrare/Ieșire) | `0840H / 08C0H` | 

## 💻 Software (Assembly)
Implementarea software include rutine esențiale pentru:
1.  **Inițializarea** circuitelor 8251 și 8255. 
2.  **Scanarea tastaturii** prin metoda scanării matriciale. 
3.  **Afișarea caracterelor** hexazecimale pe segmente. 
4.  **Transmisia/Recepția** serială și emisia paralelă. 
