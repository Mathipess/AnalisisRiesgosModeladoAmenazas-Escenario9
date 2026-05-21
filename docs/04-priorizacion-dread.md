# Análisis Cualitativo y Cuantitativo DREAD

Cálculo del nivel de riesgo absoluto aplicando los cinco factores de la metodología DREAD (escala del 1 al 10).

* **Fórmula:** Riesgo Absoluto = Daño (D) + Reproducibilidad (R) + Explotabilidad (E) + Afectados (A) + Descubribilidad (D)

## 1. Matriz de Riesgos

| ID | Amenaza | D | R | E | A | D | Total | Severidad |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: | :---: | :--- |
| **TH01** | Suplantación de GPS para fraude financiero | 8 | 8 | 9 | 7 | 8 | **40 / 50** | **CRÍTICO** |
| **TH04** | Fuga de datos de ubicación en tiempo real (*Stalking*) | 10 | 5 | 6 | 9 | 7 | **37 / 50** | **ALTO** |
| **TH06** | Acceso no autorizado a historial de viajes (IDOR) | 7 | 6 | 8 | 8 | 7 | **36 / 50** | **ALTO** |
| **TH03** | Repudio de transacciones de pago fraudulentas | 7 | 9 | 5 | 6 | 5 | **32 / 50** | **ALTO** |
| **TH05** | DoS al matching engine mediante solicitudes falsas | 6 | 5 | 7 | 9 | 4 | **31 / 50** | **ALTO** |

## 2. Criterios de Aceptación de Riesgo de la Organización
* **Puntuación >= 40:** Severidad Crítica. Requiere mitigación e ingeniería inmediata obligatoria previa al despliegue.
* **Puntuación de 30 a 39:** Severidad Alta. Mitigación prioritaria planificada dentro del ciclo de desarrollo actual (Sprint en curso).