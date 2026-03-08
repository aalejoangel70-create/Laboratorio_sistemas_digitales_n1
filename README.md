# 🔬Laboratorio_sistemas_digitales_n1
### Fundación Universitaria Compensar | Experimenta Conecta

---

## 📋 Tabla de Contenidos
- [Punto 1 – Oscilador Multivibrador Astable con TL555](#punto-1--oscilador-multivibrador-astable-con-tl555)
- [Punto 2 – Compuertas Lógicas](#punto-2--compuertas-lógicas)
- [Integrantes del Equipo](#integrantes-del-equipo)

---

## Punto 1 – Oscilador Multivibrador Astable con TL555

### 🎯 Objetivo
Desarrollar un montaje de un oscilador multivibrador astable con el temporizador **TL555** que genere una onda cuadrada con un periodo de **2 segundos**.

---

### 🔩 Descripción del Circuito

El montaje utiliza:
- **Fuente de alimentación:** Batería de **9V**
- **Regulador de voltaje:** **LM7805** → regula la tensión a **5V** para alimentar el TL555
- **Temporizador:** **TL555** configurado en modo astable
- **Salida:** Onda cuadrada con periodo de 2 segundos

#### Diagrama de bloques del montaje:

```
[Batería 9V] → [LM7805 (regulador 5V)] → [Circuito TL555 Astable] → [Salida onda cuadrada]
```

#### Pinout del TL555:

| Pin | Nombre  | Función                        |
|-----|---------|-------------------------------|
| 1   | GND     | Tierra                        |
| 2   | TRIG    | Disparador                    |
| 3   | OUT     | Salida                        |
| 4   | RESET   | Reset (activo en bajo)        |
| 5   | CONT    | Control de voltaje            |
| 6   | THRES   | Umbral                        |
| 7   | DISCH   | Descarga                      |
| 8   | VDD     | Alimentación positiva (5V)    |

---

### 📐 Cálculo Paso a Paso de los Componentes

#### Fórmulas del modo astable del 555:

El temporizador 555 en modo astable usa **dos resistencias (Ra, Rb)** y **un condensador (C)** para determinar la frecuencia y el ciclo de trabajo.

**Tiempo en ALTO (t_H):**
```
t_H = 0.693 × (Ra + Rb) × C
```

**Tiempo en BAJO (t_L):**
```
t_L = 0.693 × Rb × C
```

**Periodo total (T):**
```
T = t_H + t_L = 0.693 × (Ra + 2×Rb) × C
```

**Frecuencia (f):**
```
f = 1 / T = 1.44 / [(Ra + 2×Rb) × C]
```

---

#### ✅ Cálculo para T = 2 segundos

**Objetivo:** T = 2 s → f = 0.5 Hz

**Paso 1:** Seleccionar el condensador:
```
C = 10 µF (microfaradios)
```

**Paso 2:** Para un ciclo de trabajo cercano al 50%, se busca que Ra sea pequeña comparada con Rb. Usamos:
```
Ra = 1 kΩ
```

**Paso 3:** Despejar Rb de la fórmula del periodo:
```
T = 0.693 × (Ra + 2×Rb) × C
2 = 0.693 × (1000 + 2×Rb) × 10×10⁻⁶
2 / (0.693 × 10×10⁻⁶) = 1000 + 2×Rb
288,617 ≈ 1000 + 2×Rb
2×Rb ≈ 287,617
Rb ≈ 143,808 Ω ≈ 144 kΩ  (usar 150 kΩ disponible comercialmente)
```

**Paso 4:** Verificación con valores comerciales Ra = 1 kΩ, Rb = 150 kΩ, C = 10 µF:
```
T = 0.693 × (1000 + 2×150,000) × 10×10⁻⁶
T = 0.693 × 301,000 × 10×10⁻⁶
T ≈ 2.085 s  ✅ (muy cercano a 2 segundos)
```

---

#### 📦 Lista de Componentes

| Componente       | Valor         | Cantidad |
|-----------------|---------------|----------|
| TL555           | Temporizador  | 1        |
| LM7805          | Regulador 5V  | 1        |
| Resistencia Ra  | 1 kΩ          | 1        |
| Resistencia Rb  | 150 kΩ        | 1        |
| Condensador C   | 10 µF / 16V   | 1        |
| Condensador bypass (pin 5) | 10 nF | 1   |
| Batería         | 9V            | 1        |
| LED + resistencia 470Ω | Indicador visual | 1 |

---

### 📸 Fotos del Montaje

> *(Insertar aquí las fotos del montaje físico en protoboard)*

---

## Punto 2 – Compuertas Lógicas

### 🎯 Objetivo
Reconocer las diferentes compuertas lógicas manejadas en el curso, identificar sus circuitos integrados, tablas de verdad y funciones booleanas.

---

### 🔌 Circuitos Integrados por Compuerta

| Compuerta | CI (Serie HC) | CI (Serie LS) | Función Booleana |
|-----------|--------------|--------------|-----------------|
| AND       | 74HC08       | 74LS08       | Y = A · B       |
| OR        | 74HC32       | 74LS32       | Y = A + B       |
| NOT       | 74HC04       | 74LS04       | Y = Ā           |
| NAND      | 74HC00       | 74LS00       | Y = ‾(A · B)    |
| NOR       | 74HC02       | 74LS02       | Y = ‾(A + B)    |
| XOR       | 74HC86       | 74LS86       | Y = A ⊕ B       |

---

### 📊 Tablas de Verdad

#### Compuerta AND (74HC08 / 74LS08)
| A | B | Salida (Y = A·B) | LED |
|---|---|-----------------|-----|
| 0 | 0 | 0               | ❌  |
| 0 | 1 | 0               | ❌  |
| 1 | 0 | 0               | ❌  |
| 1 | 1 | 1               | ✅  |

**Función booleana:** `Y = A · B`

---

#### Compuerta OR (74HC32 / 74LS32)
| A | B | Salida (Y = A+B) | LED |
|---|---|-----------------|-----|
| 0 | 0 | 0               | ❌  |
| 0 | 1 | 1               | ✅  |
| 1 | 0 | 1               | ✅  |
| 1 | 1 | 1               | ✅  |

**Función booleana:** `Y = A + B`

---

#### Compuerta NOT (74HC04 / 74LS04)
| A | Salida (Y = Ā) | LED |
|---|--------------|-----|
| 0 | 1            | ✅  |
| 1 | 0            | ❌  |

**Función booleana:** `Y = Ā`

---

#### Compuerta NAND (74HC00 / 74LS00)
| A | B | Salida Y = ‾(A·B) | LED |
|---|---|------------------|-----|
| 0 | 0 | 1                | ✅  |
| 0 | 1 | 1                | ✅  |
| 1 | 0 | 1                | ✅  |
| 1 | 1 | 0                | ❌  |

**Función booleana:** `Y = ‾(A · B)`

---

#### Compuerta NOR (74HC02 / 74LS02)
| A | B | Salida Y = ‾(A+B) | LED |
|---|---|------------------|-----|
| 0 | 0 | 1                | ✅  |
| 0 | 1 | 0                | ❌  |
| 1 | 0 | 0                | ❌  |
| 1 | 1 | 0                | ❌  |

**Función booleana:** `Y = ‾(A + B)`

---

#### Compuerta XOR (74HC86 / 74LS86)
| A | B | Salida Y = A⊕B | LED |
|---|---|---------------|-----|
| 0 | 0 | 0             | ❌  |
| 0 | 1 | 1             | ✅  |
| 1 | 0 | 1             | ✅  |
| 1 | 1 | 0             | ❌  |

**Función booleana:** `Y = A ⊕ B`

---

### 🗂️ Fichas Técnicas (Datasheets)

| Compuerta | Datasheet |
|-----------|-----------|
| 74HC08 (AND)  | [Ver datasheet](https://www.ti.com/lit/ds/symlink/sn74hc08.pdf) |
| 74HC32 (OR)   | [Ver datasheet](https://www.ti.com/lit/ds/symlink/sn74hc32.pdf) |
| 74HC04 (NOT)  | [Ver datasheet](https://www.ti.com/lit/ds/symlink/sn74hc04.pdf) |
| 74HC00 (NAND) | [Ver datasheet](https://www.ti.com/lit/ds/symlink/sn74hc00.pdf) |
| 74HC02 (NOR)  | [Ver datasheet](https://www.ti.com/lit/ds/symlink/sn74hc02.pdf) |
| 74HC86 (XOR)  | [Ver datasheet](https://www.ti.com/lit/ds/symlink/sn74hc86.pdf) |

---

### 📸 Fotos del Montaje – Compuertas

> *(Insertar aquí las fotos del montaje de cada compuerta en protoboard)*

---

## 👥 Integrantes del Equipo

| Nombre completo | Rol en el laboratorio |
|----------------|----------------------|
| *(Nombre 1)*   | *(descripción)*      |
| *(Nombre 2)*   | *(descripción)*      |
| *(Nombre 3)*   | *(descripción)*      |

---

## ⚠️ Notas Importantes
- Se utilizó una pila de **9V** + regulador **LM7805** para obtener los **5V** necesarios.
- Todos los integrantes contribuyeron al repositorio (verificable en la métrica **Insights** de GitHub).
- Las fichas técnicas fueron consultadas para verificar los esquemas de conexión de cada CI.

---

*Fundación Universitaria Compensar – Experimenta Conecta*
