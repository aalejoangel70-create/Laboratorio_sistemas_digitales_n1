# Laboratorio Sistemas Digitales 1

<p align="center">
  <img src="https://img.shields.io/badge/Institución-Fundación%20Universitaria%20Compensar-orange"/>
  <img src="https://img.shields.io/badge/Programa-Ingeniería%20de%20Sistemas-blue"/>
  <img src="https://img.shields.io/badge/Área-Sistemas%20Digitales-green"/>
  <img src="https://img.shields.io/badge/Fecha-Marzo%202026-lightgrey"/>
</p>

---

##  Integrantes del Equipo

| Nombre | Rol |
|--------|-----|
| Jorge Torrenegra Almanza | Integrante |
| Gilbert Alejandro Ángel Jimenez | Integrante |


---

##  Tabla de Contenidos

- [Punto 1 – Oscilador Multivibrador Astable con TL555](#punto-1--oscilador-multivibrador-astable-con-tl555)
  - [Introducción](#introducción)
  - [Objetivos](#objetivos)
  - [Materiales y Componentes](#materiales-y-componentes)
  - [Descripción del TL555](#descripción-del-temporizador-tl555)
  - [Proceso de Montaje](#proceso-de-montaje-y-configuración)
  - [Principio de Funcionamiento](#principio-de-funcionamiento)
  - [Resultados](#resultados-y-funcionamiento)
  - [Dificultades](#dificultades-durante-el-montaje)
  - [Conclusión](#conclusión)
  - [Referencias](#referencias-bibliográficas)
- [Punto 2 – Compuertas Lógicas](#punto-2--compuertas-lógicas)

---

# Punto 1 – Oscilador Multivibrador Astable con TL555

## Introducción

El presente trabajo documenta la construcción de un circuito oscilador utilizando el temporizador **TL555 / NE555** en **modo astable**. Este modo de operación se caracteriza porque el circuito **no tiene un estado estable**, lo que provoca que el pin de salida (Pin 3) cambie continuamente entre **nivel alto (HIGH)** y **nivel bajo (LOW)**.

Este comportamiento genera una **onda cuadrada periódica**, utilizada ampliamente en aplicaciones como:

- Generación de señales de reloj en sistemas digitales
- Control de parpadeo de LEDs
- Circuitos de temporización
- Osciladores electrónicos básicos

> El circuito 555 fue desarrollado en **1971** y sigue siendo uno de los integrados más utilizados en electrónica, debido a su bajo costo, facilidad de uso y gran versatilidad.

---

## Objetivos

###  Objetivo General
Diseñar y montar en el aula de clase un circuito generador de **onda cuadrada utilizando el temporizador TL555 en modo astable**, con el fin de comprender el funcionamiento de los osciladores electrónicos y la generación de señales periódicas mediante el uso de componentes electrónicos básicos.

###  Objetivo Práctico
Implementar sobre una **protoboard** un circuito oscilador basado en el temporizador TL555, realizando la correcta configuración de sus **8 pines**, la conexión de resistencias, capacitor y potenciómetro, y verificar su funcionamiento mediante la observación del encendido y apagado de **LEDs** conectados a la salida del circuito.

###  Objetivo de Aprendizaje
Comprender el comportamiento del temporizador 555 en **modo astable**, analizando el proceso de **carga y descarga del capacitor**, así como la influencia de los valores de resistencia y capacitancia en la generación de una señal periódica tipo **onda cuadrada**.

---

## Materiales y Componentes

| Componente | Valor | Función |
|------------|-------|---------|
| Circuito Integrado | TL555 / NE555 | Generador de señal |
| Resistencia R1 | 4.7 kΩ | Control de carga del capacitor |
| Resistencia R2 | Potenciómetro 10 kΩ | Control de frecuencia |
| Resistencia R3 | 1 kΩ | Protección del LED |
| Resistencia adicional | 330 Ω | Protección segundo LED |
| Capacitor C1 | 100 µF | Control del tiempo de oscilación |
| Capacitor de filtro | 10 µF | Estabilización de la fuente |
| LEDs | 2 LEDs verdes | Visualización de la señal |
| Fuente | Batería de 9V | Alimentación del circuito |
| Protoboard | — | Montaje del circuito |
| Jumpers | — | Conexiones |

**  – Todos los componentes antes del montaje**

![Componentes antes del montaje](foto1_componentes.png)

---

## Descripción del Temporizador TL555

El circuito integrado TL555 contiene **comparadores internos, un flip-flop y un transistor de descarga** que permiten generar señales temporizadas. El encapsulado tiene **8 pines**, cada uno con una función específica:

| Pin | Nombre | Función |
|-----|--------|---------|
| 1 | GND | Tierra del circuito |
| 2 | Trigger | Activa el ciclo cuando el voltaje cae por debajo de 1/3 Vcc |
| 3 | Output | Salida de la señal cuadrada |
| 4 | Reset | Reinicia el circuito |
| 5 | Control Voltage | Ajuste del comparador (normalmente no se usa) |
| 6 | Threshold | Detecta cuando el capacitor alcanza 2/3 Vcc |
| 7 | Discharge | Descarga el capacitor |
| 8 | Vcc | Alimentación positiva |

---

## Proceso de Montaje y Configuración

El montaje se realizó utilizando una **protoboard**, colocando el TL555 en la parte central para distribuir correctamente las conexiones hacia cada uno de sus pines.

###  Configuración Pin a Pin

** Pin 1 – GND (Tierra)**
Conectado directamente a la línea negativa de la protoboard (terminal negativo de la batería de 9V). Establece la referencia de tierra para todo el circuito.

** Pin 8 – VCC (Alimentación)**
Conectado a la línea positiva de la protoboard (terminal positivo de la batería). Suministra la energía necesaria para el funcionamiento interno del temporizador.

** Pin 4 – RESET**
Se realizó un **puente entre el pin 8 y el pin 4**, conectándolo directamente al voltaje positivo para evitar reinicios accidentales. El temporizador permanece activo de forma continua.

** Pines 2 y 6 – TRIGGER / THRESHOLD**
Se conectó el terminal positivo del **capacitor electrolítico de 100µF**. El terminal negativo va a la línea negativa. Este capacitor es el encargado de almacenar energía durante la carga y descarga que genera la oscilación.

** Pin 7 – DISCHARGE**
Conectado al **potenciómetro de 10kΩ** (terminal central). Permite modificar la resistencia y controlar el tiempo de descarga del capacitor.

** Configuración del Potenciómetro**
Un terminal lateral del potenciómetro se conectó al **pin 2**, creando el camino de carga y descarga. Al girarlo se modifica la resistencia total y por tanto la **frecuencia de la señal generada**.

**  – Circuito en protoboard (sin energizar)**

![Circuito armado en protoboard](foto3_protoboard.png)

**  – Montaje completo con conexiones**

![Montaje completo](foto2_montaje_led.png)

---

## Principio de Funcionamiento

El funcionamiento se basa en el **proceso repetitivo de carga y descarga del capacitor**:

```
1. El capacitor comienza a CARGARSE a través de las resistencias.
2. Cuando el voltaje alcanza 2/3 Vcc → el comparador interno cambia de estado.
3. El transistor interno DESCARGA el capacitor a través del Pin 7.
4. Cuando el voltaje baja a 1/3 Vcc → el ciclo vuelve a comenzar.
```

Este proceso se repite continuamente, generando una **onda cuadrada en el Pin 3**.

###  Fórmula del Periodo

La frecuencia depende de **R1**, **R2 (potenciómetro)** y **C1**:

```
T = 0.693 × (R1 + 2×R2) × C
```

**Cálculo con los valores del circuito** (R1 = 4.7 kΩ, R2 = 10 kΩ, C = 100 µF):

```
T = 0.693 × (4700 + 2 × 10000) × 100×10⁻⁶
T = 0.693 × 24700 × 0.0001
T ≈ 1.71 segundos
```

---

## Resultados y Funcionamiento

Al conectar la batería de **9V**, el temporizador 555 inició automáticamente el ciclo de carga y descarga del capacitor, provocando que el **LED parpadeara** y demostrando la generación de una señal cuadrada.

**Observaciones durante la prueba:**

-  El circuito funcionó correctamente.
-  La variación del potenciómetro cambió la velocidad de parpadeo del LED.
-  Las resistencias limitaron la corriente evitando daños en los LEDs.

**  – Circuito funcionando con LED encendido**

![Circuito funcionando - LED encendido](foto5_circuito_completo.png)

**  – LED en máxima intensidad**

![LED encendido máxima intensidad](foto4_led_encendido.png)

**  – Segunda toma del circuito en funcionamiento**

![Segunda toma funcionando](foto6_funcionando.png)

---

## Dificultades Durante el Montaje

**1. Identificación de pines del TL555**
Fue necesario verificar correctamente la orientación del CI usando el **punto o marca del integrado**, que indica la referencia del pin 1.

**2. Falsos contactos en la protoboard**
En algunos momentos el circuito no respondía por conexiones mal ajustadas. Se solucionó revisando cada conexión y asegurando que todos los componentes estuvieran firmemente insertados.

**3. Parpadeo irregular del LED**
El LED no parpadeaba de forma regular inicialmente debido a conexiones incorrectas en el ciclo de carga/descarga del capacitor. Tras revisar las conexiones del temporizador y el potenciómetro, el circuito funcionó correctamente.

---

## Conclusión

La implementación del circuito **TL555 en modo astable** permitió comprender de forma práctica el funcionamiento de los osciladores electrónicos y la generación de señales digitales.

El uso del temporizador 555 demuestra cómo componentes electrónicos básicos como **resistencias, capacitores y semiconductores** pueden combinarse para generar señales periódicas útiles en múltiples aplicaciones.

La visualización mediante LEDs permitió verificar de forma directa el comportamiento de la señal de salida, reforzando los conceptos teóricos sobre temporización y electrónica digital.

---

## Referencias Bibliográficas

- Texas Instruments. (2016). *NE555, SA555, SE555 precision timers* (datasheet). https://www.ti.com/lit/ds/symlink/ne555.pdf
- Kynix. (2025). *Building a square wave generator using basic components*. https://www.kynix.com/Blog/Building-a-Square-Wave-Generator-Using-Basic-Components.html
- Allelco Electronics. (2025). *Understanding square waveforms in electronics*. https://www.allelcoelec.es/blog/understanding-square-waveforms-in-electronics.html
- Electronics Tutorials. *555 oscillator tutorial – The astable multivibrator*. https://www.electronics-tutorials.ws/waveforms/555_oscillator.html
- Electronics Tutorials. *RC waveforms and RC circuits with square wave signals*. https://www.electronics-tutorials.ws/rc/rc_3.html
- Elsevier. *Square wave*. ScienceDirect Topics. https://www.sciencedirect.com/topics/physics-and-astronomy/square-wave

---

---

# Punto 2 – Compuertas Lógicas

##  Objetivo
Reconocer las diferentes compuertas lógicas manejadas en el curso, identificando sus circuitos integrados, esquemas de conexión, tablas de verdad y funciones booleanas.

## Resumen de Circuitos Integrados

| Compuerta | CI Serie HC | CI Serie LS | Función Booleana |
|-----------|-------------|-------------|-----------------|
| AND  | 74HC08 | 74LS08 | Y = A · B |
| OR   | 74HC32 | 74LS32 | Y = A + B |
| NOT  | 74HC04 | 74LS04 | Y = Ā |
| NAND | 74HC00 | 74LS00 | Y = ‾(A · B) |
| NOR  | 74HC02 | 74LS02 | Y = ‾(A + B) |
| XOR  | 74HC86 | 74LS86 | Y = A ⊕ B |

---

## Compuerta AND – 74HC08 / 74LS08

**Función Booleana:** `Y = A · B`

La salida es **1** únicamente cuando **todas** las entradas son 1.

### Tabla de Verdad

| A | B | Y = A · B | LED |
|---|---|-----------|-----|
| 0 | 0 | 0 |  Apagado |
| 0 | 1 | 0 |  Apagado |
| 1 | 0 | 0 |  Apagado |
| 1 | 1 | 1 |  Encendido |

### Ficha Técnica
-  **74HC08:** https://www.ti.com/lit/ds/symlink/sn74hc08.pdf
-  **74LS08:** https://www.ti.com/lit/ds/symlink/sn74ls08.pdf

>  **Esquema y foto del montaje – Compuerta AND**
> 

---

## Compuerta OR – 74HC32 / 74LS32

**Función Booleana:** `Y = A + B`

La salida es **1** cuando **al menos una** de las entradas es 1.

### Tabla de Verdad

| A | B | Y = A + B | LED |
|---|---|-----------|-----|
| 0 | 0 | 0 |  Apagado |
| 0 | 1 | 1 |  Encendido |
| 1 | 0 | 1 |  Encendido |
| 1 | 1 | 1 |  Encendido |

### Ficha Técnica
-  **74HC32:** https://www.ti.com/lit/ds/symlink/sn74hc32.pdf
-  **74LS32:** https://www.ti.com/lit/ds/symlink/sn74ls32.pdf

>  **Esquema y foto del montaje – Compuerta OR**
> 

---

## Compuerta NOT – 74HC04 / 74LS04

**Función Booleana:** `Y = Ā`

La salida es siempre el **inverso** de la entrada.

### Tabla de Verdad

| A | Y = Ā | LED |
|---|-------|-----|
| 0 | 1 |  Encendido |
| 1 | 0 |  Apagado |

### Ficha Técnica
-  **74HC04:** https://www.ti.com/lit/ds/symlink/sn74hc04.pdf
-  **74LS04:** https://www.ti.com/lit/ds/symlink/sn74ls04.pdf

>  **Esquema y foto del montaje – Compuerta NOT**
> 

---

## Compuerta NAND – 74HC00 / 74LS00

**Función Booleana:** `Y = ‾(A · B)`

La salida es **0** únicamente cuando **todas** las entradas son 1.

### Tabla de Verdad

| A | B | Y = ‾(A·B) | LED |
|---|---|------------|-----|
| 0 | 0 | 1 |  Encendido |
| 0 | 1 | 1 |  Encendido |
| 1 | 0 | 1 |  Encendido |
| 1 | 1 | 0 |  Apagado |

### Ficha Técnica
-  **74HC00:** https://www.ti.com/lit/ds/symlink/sn74hc00.pdf
-  **74LS00:** https://www.ti.com/lit/ds/symlink/sn74ls00.pdf

>  **Esquema y foto del montaje – Compuerta NAND**
> 

---

## Compuerta NOR – 74HC02 / 74LS02

**Función Booleana:** `Y = ‾(A + B)`

La salida es **1** únicamente cuando **todas** las entradas son 0.

### Tabla de Verdad

| A | B | Y = ‾(A+B) | LED |
|---|---|------------|-----|
| 0 | 0 | 1 |  Encendido |
| 0 | 1 | 0 |  Apagado |
| 1 | 0 | 0 |  Apagado |
| 1 | 1 | 0 |  Apagado |

### Ficha Técnica
-  **74HC02:** https://www.ti.com/lit/ds/symlink/sn74hc02.pdf
-  **74LS02:** https://www.ti.com/lit/ds/symlink/sn74ls02.pdf

>  **Esquema y foto del montaje – Compuerta NOR**
> 

---

## Compuerta XOR – 74HC86 / 74LS86

**Función Booleana:** `Y = A ⊕ B`

La salida es **1** cuando las entradas son **diferentes** entre sí.

### Tabla de Verdad

| A | B | Y = A ⊕ B | LED |
|---|---|-----------|-----|
| 0 | 0 | 0 |  Apagado |
| 0 | 1 | 1 |  Encendido |
| 1 | 0 | 1 |  Encendido |
| 1 | 1 | 0 |  Apagado |

### Ficha Técnica
-  **74HC86:** https://www.ti.com/lit/ds/symlink/sn74hc86.pdf
-  **74LS86:** https://www.ti.com/lit/ds/symlink/sn74ls86.pdf

>  **Esquema y foto del montaje – Compuerta XOR**
> 

---

<p align="center">
  <em>Fundación Universitaria Compensar – Experimenta Conecta · Marzo 2026</em>
</p>*Fundación Universitaria Compensar – Experimenta Conecta*
