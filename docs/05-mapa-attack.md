# Mapeo Táctico a MITRE ATT&CK

Análisis del comportamiento del adversario adaptado a las tácticas, técnicas y procedimientos (TTPs) del framework global de ciberseguridad.

## 1. Táctica: Acceso Inicial / Acceso a Cuentas
* **Técnica:** Valid Accounts (T1078)
* **Contexto en Ridesharing:** Comprometer credenciales o tokens de conductores legítimos mediante phishing o compra en mercados ilegales para operar cuentas clonadas y perpetrar fraudes.

## 2. Táctica: Evadir Defensas / Manipulación
* **Técnica:** Data Manipulation (T1565.001)
* **Contexto en Ridesharing:** Modificación maliciosa del flujo de entrada de telemetría GPS o alteración del SDK del mapa en dispositivos comprometidos (Jailbreak) para engañar al calculador de rutas del backend.

## 3. Táctica: Exfiltración / Impacto
* **Técnica:** Exploit Public-Facing Application (T1190)
* **Contexto en Ridesharing:** Aprovechamiento de fallos lógicos o parámetros desprotegidos en las REST APIs expuestas para la extracción automatizada masiva (scraping) de historiales de ubicación guardados en PostgreSQL.