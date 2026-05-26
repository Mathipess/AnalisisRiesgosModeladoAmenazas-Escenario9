# Registro de Prompt - Clasificación DREAD

- **Fecha:** 21/05/2026
- **Herramienta:** Gemini
- **Propósito:** Cálculo cuantitativo y priorización de riesgos prioritarios.

---

### Prompt Exacto Enviado:

Utiliza como entrada las 6 amenazas técnicas (TH01 a TH06) generadas en la matriz STRIDE previa. Actúa como un analista de riesgos senior y evalúa cuantitativamente cada una de ellas utilizando el framework DREAD.

Asigna a cada variable una puntuación entera en una escala del 1 al 10, basándote en una app móvil de ridesharing con millones de usuarios concurrentes.

Calcula el Riesgo Absoluto final mediante la sumatoria lineal de los factores: Total = D + R + E + A + D. Puedes utilizar el documento de guia adjunto previamente. 

Ordena la tabla resultante de mayor a menor puntaje de riesgo y genera la salida exclusivamente en una matriz tabular de Markdown.