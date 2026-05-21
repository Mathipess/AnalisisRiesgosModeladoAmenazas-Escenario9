# SafeRide Enterprise Architecture - Threat Modeling & Risk Assessment

Este repositorio contiene el análisis de riesgos integral, el modelado de amenazas y el diseño de controles de seguridad para la plataforma de ridesharing corporativa **SafeRide**. El proyecto aplica de manera combinada las metodologías globales **STRIDE**, **DREAD**, **MITRE ATT&CK** y los marcos de control **ISO/IEC 27001** y **NIST SP 800-53**.

---

## 1. INFORMACIÓN GENERAL DEL PROYECTO

* **Fecha de inicio:** [14/05/2026]
* **Fecha de entrega:** [28/05/2026]
* **Versión del documento:** 1.0
* **Equipo de análisis:** [Mathias Pessaj, Ignacio Gonzalez, Sebastian Di Loreto]

---

### 1.1 Descripción del Sistema (Escenario Seleccionado)

El sistema bajo análisis corresponde al **Escenario 9: Plataforma Ridesharing**. Es una solución ecosistémica de transporte bajo demanda basada en una arquitectura móvil-servidor de alta concurrencia y baja latencia. El sistema orquesta dinámicamente las solicitudes de transporte mediante un motor de emparejamiento inteligente (*matching engine*) y procesa flujos continuos de telemetría georreferenciada.

#### Componentes del Core Tecnológico en Alcance:
* **Aplicaciones Móviles Nativas (T01):** Interfaces de usuario dedicadas e independientes para Pasajeros y Conductores en sistemas operativos iOS y Android.
* **Capa Perimetral / DMZ:** API Gateway y balanceadores encargados del enrutamiento, terminación de cifrado TLS, control de tasa (*rate limiting*) y validación perimetral de sesiones.
* **Backend Core (T02):** Microservicios desarrollados sobre la pila Node.js encargados de la lógica de negocio, asignación de viajes, enrutamiento óptimo y chat *in-app*.
* **Capa de Datos y Persistencia:**
  * **PostgreSQL (T03):** Almacenamiento persistente, relacional e inmutable para el historial de rutas, transacciones de pago, calificaciones (*reviews*) y perfiles de identidad.
  * **Redis Cache (T04):** Motor NoSQL en memoria de ultra-alta velocidad utilizado para almacenar los estados dinámicos de los viajes y la telemetría GPS en tiempo real de los conductores activos.
* **Integraciones y Servicios de Terceros:**
  * **Google Maps API:** Proveedor externo para la georreferenciación cartográfica, cálculo preciso de distancias y renderizado de rutas.
  * **Stripe API:** Pasarela financiera delegada para el procesamiento seguro de pagos, facturación recurrente y tokenización bancaria bajo estándares normativos.

---

### 1.2 Alcance del Análisis

#### Componentes Incluidos:
- [X] Aplicación móvil de Pasajeros y Conductores (iOS/Android)
- [X] Backend Node.js y capa intermedia de API Gateway
- [X] Bases de datos PostgreSQL y clúster de caché en Redis
- [X] Flujos de integración de datos con la API externa de Google Maps
- [X] Flujos de transacciones monetarias y tokenización con Stripe API

#### Componentes Fuera de Alcance:
- **Redes de Telecomunicaciones de Operadores Móviles:** Se asume que el canal de transporte físico provisto por las empresas de telefonía móvil de los usuarios puede ser inseguro, por lo cual se mitiga mediante controles de capa de aplicación (Cifrado de extremo a extremo).

---

### 1.3 Supuestos de Seguridad Básicos
1. Se asume que la infraestructura de la nube pública donde se aloja la Zona Interna cumple con los estándares físicos de seguridad de centros de datos de nivel Tier III o superior.
2. Se asume que los SDKs oficiales de terceros provistos por Stripe y Google Maps no contienen vulnerabilidades de día cero (*Zero-Days*) en el momento del análisis y se actualizan de forma continua según el ciclo de parches de los proveedores.

---

## Estructura del Repositorio Git

El entregable técnico se encuentra segmentado modularmente en los siguientes archivos Markdown y de diagramación nativa:

```
Escenario9-riesgos/
├── README.md                    # Descripción del grupo y escenario elegido
├── docs/
│   ├── 01-inventario-activos.md
│   ├── 02-arquitectura-trust-boundaries.md
│   ├── 03-analisis-stride.md
│   ├── 04-priorizacion-dread.md
│   ├── 05-mapa-attack.md
│   ├── 06-plan-mitigacion.md
│   └── 07-riesgos-residuales.md
├── diagrams/
│   ├── arquitectura pseudocodigo.txt
│   ├── arquitectura.png
├── templates/                  # Plantillas utilizadas
│   └── Plantilla_Analisis_Riesgos.md
└── references/
    ├── Guía - Equipo responsable de la gestión de riesgo.pdf
    ├── Guia - Implantacion SGSI - Inventario activos y Evaluacion riesgos_1
    ├── Guía - Indicadores SGSI_v3 r20220803.pdf
    ├── Informe ejecutivo riesgos.docx
    └── Matriz RACI.docx
```