# Plan de Mitigación y Diseño de Controles

Controles técnicos, operativos y preventivos estructurados bajo los marcos normativos ISO 27001 y NIST SP 800-53 para neutralizar las amenazas prioritarias.

## 1. Controles Específicos por Actividad

### Actividad 1 & 2: Privacidad y Seguridad en Geolocalización (Mitigación TH01 y TH04)
* **Detección de Mock Locations (Lado Cliente):** Implementación de código nativo en las apps para consumir las APIs del sistema operativo (`isMockProviderEnabled` en Android y flags anti-spoofing en iOS) bloqueando el servicio si la simulación está activa.
* **Validación Cinemática (Lado Servidor):** Algoritmo heurístico en Node.js que valida si el salto geográfico entre coordenadas consecutivas de un conductor viola límites físicos reales (ej: recorrer 5 kilómetros en 2 segundos).
* **Ofuscación Geográfica:** Anonimizar los datos de ubicación histórica en PostgreSQL tras finalizar el viaje truncando los decimales finales de la latitud y longitud.

### Actividad 3 & 5: Seguridad en Pagos y Control de Fraude (Mitigación TH03)
* **Tokenización PCI-DSS vía Stripe:** Prohibición absoluta de almacenar o transmitir datos de tarjetas de crédito en la infraestructura propia. Uso obligatorio de *Stripe SDK* que delega el procesamiento completo.
* **Autenticación 3D Secure (3DS):** Desencadenar de forma mandatoria la verificación biométrica o SMS bancaria ante registros de tarjetas nuevas o desvíos transaccionales geográficos atípicos.

### Actividad 4: Integridad de Comunicaciones en Tiempo Real (Mitigación TH02 y TH06)
* **Cifrado TLS 1.3 con SSL Pinning:** Implementación de anclaje de certificados criptográficos en las apps móviles para imposibilitar la interceptación por proxies interceptores (MitM).
* **Defensa anti-IDOR Estricta:** Validar a nivel base de datos en cada endpoint de Node.js que el ID del token JWT del usuario emisor sea idéntico al ID del propietario del recurso solicitado.

## 2. Matriz Organizacional de Controles

| ID Control | Tipo de Control | Referencia Normativa | Descripción Operativa del Control | Prioridad de Despliegue |
| :--- | :--- | :--- | :--- | :--- |
| **C-01** | Preventivo | **NIST SC-8** | Cifrado en tránsito mediante TLS 1.3 y SSL Pinning obligatorio en apps. | **Prioridad 1 (Alta)** |
| **C-02** | Preventivo | **NIST AC-2** | Validación estricta de autorización de sesión JWT contra IDOR en APIs. | **Prioridad 1 (Alta)** |
| **C-03** | Detectivo | **ISO 27001 A.12.4** | Generación de registros de auditoría técnicos e inmutables en CloudWatch/SIEM. | **Prioridad 2 (Media)** |
| **C-04** | Preventivo | **ISO 27001 A.14.1** | Despliegue de chequeos de integridad de dispositivo (detección de Root/Jailbreak). | **Prioridad 1 (Alta)** |