# Generador de Notas Musicales - Proyecto Experimental SEA (ITESO-DESI)

Proyecto para la materia **Sistemas Electrónicos Analógicos** (O2024). Implementación de un sintetizador básico que genera una escala de 7 notas musicales (C, D, E, F, G, A, B) con ondas cuadrada y triangular, usando un VCO basado en IC 555, LFO para modulación, VCA para control de amplitud, e integrador con TL082.

## Enunciado del Proyecto
Diseñar e implementar un sistema musical que genere señales periódicas en el rango de audio (20 Hz - 20 kHz). Basado en circuitos generadores de onda senoidal, cuadrada y triangular. Incluye bloques como VCO (Voltage Controlled Oscillator), LFO (Low Frequency Oscillator), VCA (Voltage Controlled Amplifier) y envolvente ADSR (Attack-Decay-Sustain-Release).

Referencia principal: [SEA - Práctica 04a - Generador de Notas Musicales - O2024.pdf](docs/SEA - Práctica 04a - Generador de Notas Musicales - O2024.pdf)

## Diagrama de Bloques del Sintetizador Simple
Basado en la Figura 1 del enunciado:

```mermaid
graph TD
    A[Teclado 7 Notas] --> B[VCO Oscilador Principal]
    C[LFO Baja Frecuencia] --> B
    B --> D[VCA Control de Amplitud]
    D --> E[Env. ADSR Attack-Decay-Sustain-Release]
    E --> F[Amplificador]
    F --> G[Salida Audio]
    H[Filtro] --> F
    style B fill:#f9f,stroke:#333
    style C fill:#bbf,stroke:#333
    style D fill:#ff9,stroke:#333
