# Registro de Prompt - Análisis STRIDE

- **Fecha:** 21/05/2026
- **Herramienta:** Gemini
- **Propósito:** Generación y refinamiento de la matriz de amenazas de geolocalización y APIs.

---

### Prompt Exacto Enviado:

Teniendo en cuenta el contexto de los archivos enviados y la letra de la tarea, realiza un modelado de amenazas aplicando de forma estricta la metodología STRIDE. 

Quiero que identifiques exactamente una amenaza técnica crítica por cada una de las letras (Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege).

Para cada amenaza detectada, debes proveer obligatoriamente:
1. ID único de amenaza (formato TH01, TH02...).
2. Componente tecnológico específico afectado (tomado de nuestro inventario de activos).
3. Descripción detallada del vector de ataque (enfocado en riesgos de ridesharing como GPS Spoofing, IDOR en historial de viajes, inyección de telemetría falsa o fraude transaccional).
4. El identificador numérico de la debilidad de software asociada de la lista CWE (Common Weakness Enumeration).

Presenta el resultado final estructurado en una tabla Markdown limpia, técnica y profesional. No agregues introducciones ni textos de relleno.