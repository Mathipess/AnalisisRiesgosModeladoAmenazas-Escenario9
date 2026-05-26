# Memory Bank - Contexto de Ciberseguridad para IA

## Objetivo del Proyecto
Este entorno contiene el Análisis de Riesgos y Modelado de Amenazas integral para la plataforma corporativa de transporte bajo demanda **SafeRide** (Escenario 9: Ridesharing tipo Uber).

## Arquitectura y Componentes en Alcance
- **Clientes:** Aplicaciones móviles nativas iOS/Android (Pasajeros y Conductores).
- **Perímetro:** API Gateway en DMZ (Terminación TLS 1.3, Rate Limiting, JWT Validation).
- **Core Backend:** Servicios distribuidos en Node.js (Matching Engine y lógicas de negocio).
- **Persistencia:** PostgreSQL (Historial inmutable) y Redis Cache (Coordenadas GPS vivas).
- **APIs Externas:** Google Maps API (Enrutamiento) y Stripe API (Pasarela de pagos PCI-DSS).

## Reglas de Interacción con la IA
1. **Rol:** Actúa como un Ingeniero de Seguridad de la Información (CISO) y Arquitecto de Threat Modeling.
2. **Metodologías:** Todo análisis debe estructurarse bajo los marcos STRIDE, DREAD, MITRE ATT&CK, ISO 27001 y NIST SP 800-53.

## Archivos de contexto necesarios
1. Plantilla_Análisis_de_Riesgo.pdf: Estructura oficial y formato requerido para el desarrollo del modelado de amenazas y el checklist final de entregables.
2. Guía - Indicadores SGSI_v3 r20220803.pdf: Guía metodológica elaborada por Agesic para medir el avance en la implantación de un Sistema de Gestión de la Seguridad de la Información.
3. Guía - Equipo responsable de la gestión de riesgo.pdf: Documento de Agesic que define los roles, actividades principales y responsabilidades del equipo de gestión de riesgos.
4. Matriz RACI.docx: Plantilla y guía de asignación de responsabilidades (Responsable, Líder, Consultado, Informado) para los procesos de seguridad.
5. Informe ejecutivo riesgos.docx: Modelo formal para la presentación de resultados, escalas de impacto/probabilidad y el plan de remediación ante la Dirección.
6. Guia - Implantacion SGSI - Inventario activos y Evaluacion riesgos_1.xlsx