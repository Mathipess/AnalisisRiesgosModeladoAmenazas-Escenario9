# Matriz de Modelado de Amenazas STRIDE

Aplicación sistemática de la metodología STRIDE sobre los componentes de la plataforma de Ridesharing para identificar vectores de ataque realistas.

| ID | Componente Afectado | Categoría STRIDE | Descripción de la Amenaza | CWE Asociada |
| :--- | :--- | :--- | :--- | :--- |
| **TH01** | Aplicación Móvil (T01) | **S**poofing | Inyección de coordenadas GPS falsas (*GPS Spoofing*) mediante herramientas en dispositivos rooteados/Jailbreak para cobrar tarifas fraudulentas. | **CWE-290** |
| **TH02** | Canal de Comunicación | **T**ampering | Interceptación Man-in-the-Middle (MitM) de la telemetría para modificar datos geográficos en tránsito hacia el API Gateway. | **CWE-319** |
| **TH03** | Backend Node.js (T02) | **R**epudiation | Ausencia de logs de auditoría inmutables en cancelaciones de viajes o disputas de pago, impidiendo determinar responsabilidades. | **CWE-778** |
| **TH04** | Base de Datos (T03/T04) | **I**nformation Disclosure | Exposición involuntaria de ubicaciones históricas de pasajeros a través de APIs mal protegidas, facilitando acoso (*stalking*). | **CWE-200** |
| **TH05** | API / Backend (T02) | **D**enial of Service | Inundación masiva de peticiones simuladas de inicio de viaje (solicitudes fantasma) que satura y agota el motor de matching. | **CWE-400** |
| **TH06** | API Gateway / Node.js | **E**levation of Privilege | Explotación de vulnerabilidades de control de acceso a nivel de objeto (IDOR) para consultar historiales de viaje de terceros modificando el ID de usuario. | **CWE-284** |