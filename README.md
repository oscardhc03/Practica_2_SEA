# Generador de Notas Musicales - Proyecto Experimental SEA (ITESO-DESI)

Proyecto para la materia **Sistemas Electrónicos Analógicos** (O2024). Implementación de un sintetizador básico que genera una escala de 7 notas musicales (C, D, E, F, G, A, B) con ondas cuadrada y triangular, usando un VCO basado en IC 555, LFO para modulación, VCA para control de amplitud, e integrador con TL082.

## Enunciado del Proyecto
Diseñar e implementar un sistema musical que genere señales periódicas en el rango de audio (20 Hz - 20 kHz). Basado en circuitos generadores de onda senoidal, cuadrada y triangular. Incluye bloques como VCO (Voltage Controlled Oscillator), LFO (Low Frequency Oscillator), VCA (Voltage Controlled Amplifier) y envolvente ADSR (Attack-Decay-Sustain-Release).

Referencia principal: [SEA - Práctica 04a - Generador de Notas Musicales - O2024.pdf](docs/SEA - Práctica 04a - Generador de Notas Musicales - O2024.pdf)


## Esquema del VCO con IC 555
```plantuml
@startuml
!define RECTANGLE class
!define IC << (I,#FF7700) >>

skinparam monochrome true
skinparam backgroundColor #FFFFFF

package "VCO con IC 555" {
    [Vcc] -down-> [Pin 8]
    [Pin 8] -down-> [R1 : 1kΩ]
    [R1] -down-> [Pin 7]
    [Pin 7] -down-> [R2 : 10kΩ]
    [R2] -down-> [Pin 6]
    [Pin 6] -down-> [C : 0.01µF]
    [C] -down-> [Pin 2]
    [Pin 2] -down-> [GND]
    [Pin 7] -down-> [Pin 2]
    [Pin 4] -down-> [Vcc]
    [Pin 1] -down-> [GND]
    [Pin 5] -down-> [Control Voltage]
    [Pin 3] -down-> [Salida Onda Cuadrada]

    [Control Voltage] .up.> [Botón C : 10kΩ]
    [Control Voltage] .up.> [Botón D : 9kΩ]
    [Control Voltage] .up.> [Botón E : 8kΩ]
    [Control Voltage] .up.> [Botón F : 7.5kΩ]
    [Control Voltage] .up.> [Botón G : 6.8kΩ]
    [Control Voltage] .up.> [Botón A : 6kΩ]
    [Control Voltage] .up.> [Botón B : 5.5kΩ]
    [Botón C] -up-> [Vcc]
    [Botón D] -up-> [Vcc]
    [Botón E] -up-> [Vcc]
    [Botón F] -up-> [Vcc]
    [Botón G] -up-> [Vcc]
    [Botón A] -up-> [Vcc]
    [Botón B] -up-> [Vcc]

    [IC 555] #IC
    [IC 555] -[hidden]down- [Pin 3]
}
@enduml

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
