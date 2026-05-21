# Arquitectura del Sistema y Límites de Confianza

Este documento define las fronteras lógicas y de red donde cambian los niveles de confianza del sistema, permitiendo identificar puntos críticos de control de accesos.

## 1. Zonas de Confianza (Trust Zones)

1. **Zona Externa / No Confiable:** Comprende los dispositivos móviles de pasajeros y conductores (T01) operando en redes públicas (celulares, redes Wi-Fi públicas).
2. **Zona Perimetral / DMZ:** Frontera de red expuesta a Internet controlada por el API Gateway, encargada de la terminación TLS, limitación de tasa (rate limiting) y enrutamiento inicial.
3. **Zona Interna / Cloud Privada:** Red interna de microservicios protegida donde operan el Backend Node.js (T02), PostgreSQL (T03) y Redis (T04). No tiene exposición directa a Internet.

## 2. Límites de Confianza (Trust Boundaries)

* **TRUST BOUNDARY 1 (Frontera de Red Externa a Cloud Pública):** Ubicada entre las aplicaciones móviles (T01) y el API Gateway. El tráfico cruza de un entorno completamente inseguro a un entorno controlado de la organización.
* **TRUST BOUNDARY 2 (Frontera de Microservicios Internos):** Ubicada entre el API Gateway y el Backend Node.js/Bases de datos. Garantiza que las solicitudes hayan sido autenticadas y sanitizadas antes de tocar la lógica de negocio.

## 3. Flujo de Datos Crítico
Las coordenadas GPS son capturadas por el dispositivo móvil (T01), viajan cifradas por WebSockets cruzando el **Trust Boundary 1** hasta el API Gateway, se validan en el **Trust Boundary 2** y el Backend Node.js las procesa para almacenarlas efímeramente en Redis (T04) y persistentemente al finalizar el viaje en PostgreSQL (T03).