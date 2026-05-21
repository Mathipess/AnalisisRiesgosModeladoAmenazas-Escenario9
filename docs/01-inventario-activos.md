# Inventario de Activos Criticos - SafeRide Enterprise Architecture

Siguiendo el inventario estándar para la evaluación de riesgos, se categorizan y clasifican los activos críticos identificados dentro del alcance de la plataforma de ridesharing.

## 1. Activos de Información (Datos)

| ID | Activo | Propietario | Tipo de Dato | Clasificación | Descripción / Propósito |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **A01** | Datos de Geolocalización en Tiempo Real | Core Engine | PII | Alta | Coordenadas GPS exactas de conductores y pasajeros para el matching y seguimiento en ruta. |
| **A02** | Historial de Viajes | Módulo de Viajes | PII | Alta | Rutas históricas, direcciones de inicio/destino, tiempos y marcas de timestamp. |
| **A03** | Tokens de Pago / Datos Financieros | Módulo Financiero | Financiero | Alta | Tokens de sesión seguros delegados por Stripe y datos de facturación de tarjetas. |
| **A04** | Datos de Perfil e Identidad | Módulo de Usuarios | PII | Media-Alta | Nombres, fotografías, números de teléfono, calificaciones (reviews) y chats in-app. |

## 2. Activos Tecnológicos (Infraestructura / Componentes)

| ID | Activo | Tipo | Criticidad | Notas / Especificaciones |
| :--- | :--- | :--- | :--- | :--- |
| **T01** | Aplicaciones Móviles Nativas | Software (Client) | Alta | Clientes móviles (iOS/Android) que consumen las APIs del Backend. |
| **T02** | Backend Node.js / API Gateway | Software (Server) | Alta | Core central del negocio: orquestador de microservicios y motor de matching. |
| **T03** | Base de Datos PostgreSQL | Software (DB) | Alta | Almacenamiento persistente del historial de viajes, auditorías y perfiles. |
| **T04** | Caché en Memoria Redis | Software (Caché) | Alta | Gestión dinámica del estado transitorio de pings GPS y sesiones vivas. |