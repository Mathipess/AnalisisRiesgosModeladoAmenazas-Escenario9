# Evaluación de Riesgos Residuales y Conclusiones

Identificación y justificación formal de los riesgos remanentes una vez aplicados todos los controles de mitigación tecnológica del plan de seguridad.

## 1. Matriz de Riesgos Residuales Aceptados

* **R01: Spoofing por Hardware Avanzado (Simuladores Físicos RF):** Modificación física de la antena del smartphone mediante hardware de simulación satelital que burla los chequeos de software tradicionales del sistema operativo.
    * *Tratamiento:* **Aceptado.** La probabilidad remanente se reduce a nivel *Bajo* gracias al algoritmo backend de plausibilidad cinemática (que detecta las velocidades absurdas en el servidor). Desarrollar contramedidas de radiofrecuencia de hardware es inviable a nivel de costo-beneficio para el modelo de negocio.
* **R02: Exfiltración de datos visuales por Ingeniería Social (Fotografía Física):** Captura fotográfica o grabación de video externa (usando otro teléfono físico) de la pantalla de un conductor mostrando los datos en curso o el rostro de un pasajero.
    * *Tratamiento:* **Aceptado y Transferido.** Se mitiga parcialmente reduciendo al mínimo indispensable los datos personales visibles en la app y truncando las direcciones exactas a aproximaciones tras culminar el servicio. El riesgo legal residual es transferido mediante los contratos de Términos y Condiciones firmados por los conductores.

## 2. Conclusiones Generales del Equipo de Análisis

### 2.1 Reflexión sobre la Postura de Seguridad Actual

Luego de aplicar metodologías rigurosas como STRIDE y DREAD, llegamos a una conclusión que puede parecer obvia pero que es fundamental: **la plataforma de ridesharing SafeRide no es un simple servicio de transporte, es un intermediario que maneja datos sumamente sensibles de dos poblaciones vulnerables simultáneamente.** 

Por un lado, tenemos conductores que ponen su seguridad física y financiera en nuestras manos. Por el otro, pasajeros que comparten ubicaciones precisas en tiempo real. Esto significa que no podemos permitirnos fallos de seguridad mediocres. Cada vulnerabilidad es un riesgo de fraude financiero, suplantación de identidad, acoso o incluso daño físico.

### 2.2 Pilares de la Defensa

**1. Arquitectura Zero-Trust Obligatoria**

Las aplicaciones móviles operan en un entorno desconcocido e incontrolable. No importa cuántos chequeos hagamos en el cliente (jailbreak detection, mock location detection), un adversario determinado con un teléfono rooteado o con conocimientos de ingeniería inversa siempre encontrará forma de pasar por elloss.

Por eso,toda la validación lógica del negocio debe recaer sobre el servidor. No confiar en nada que venga del cliente. 

**2. Fallos de Control de Acceso: Nuestra Mayor Amenaza**

Entre los riesgos analizados, los fallos IDOR (Insecure Direct Object References) no son solo un número en nuestra matriz DREAD. Son la puerta que permite que un atacante vea el historial completo de viajes de cualquier usuario simplemente cambiando un número en una URL.

Sobre esto se puede poner un ejemplo:
Imagina que Andres consulta su historial de viajes en la app. Internamente, el hace una llamada a `/api/v1/users/12345/trips`. Un atacante, viendo esta estructura, prueba `/api/v1/users/12346/trips` y obtiene el historial completo de otro usuario: dónde trabaja, dónde vive, con quién se desplaza, patrones de viaje.

Este es un riesgo que no podemos aceptar en producción. Debe ser controlado en cada endpoint mediante validación explícita del JWT contra el propietario del recurso.

**3. La Importancia del Testing Continuo**

Las vulnerabilidades no aparecen una sola vez y desaparecen. Emergen en refactores de código, en nuevas features, en actualizaciones de dependencias. Por eso, implementar pruebas automatizadas de seguridad (DAST/SAST) integradas en el pipeline de CI/CD no es un lujo: es una necesidad operativa.

Recomendamos ejecutarlas **al menos cada 6 meses**, preferiblemente integradas en cada release. Herramientas como Snyk, SonarQube o OWASP ZAP pueden detectar automáticamente muchas clases de vulnerabilidades antes de que lleguen a producción.

### 2.3 Lo Que No Podemos Controlar (Y Debemos Aceptar)

**R01: Simuladores Físicos de RF (Radiofrecuencia)**

Existe un escenario límite donde alguien compra un simulador de GPS físico de radiofrecuencia por $500-1000 USD y lo instala en su automóvil. Esto burla incluso nuestro algoritmo de plausibilidad cinemática porque la mentira ocurre a nivel de hardware antes de que el sistema operativo interviene.

¿Podemos detectarlo? Parcialmente. Nuestro algoritmo backend puede identificar patrones sospechosos estadísticos a largo plazo, pero un ataque puntual es difícil de detener. ¿Vale la pena desarrollar contramedidas de radiofrecuencia tan sofisticadas? Para un modelo de negocio de ridesharing, creemos que la respuesta seria no. Es un riesgo residual que aceptamos porque el costo de mitigación excede el beneficio potencial.

**R02: Ingeniería Social y Captura Visual**

Un conductor malintencionado podría fotografiar la pantalla de un pasajero mostrando su hogar, su cara, datos personales. ¿Qué hacemos? Minimizar la información visible en pantalla, truncar direcciones exactas a aproximaciones. Pero al final, si alguien quiere capturar una pantalla, puede hacerlo.

El riesgo residual aquí se transfiere legalmente: los Términos y Condiciones que firman usuarios y conductores incluyen cláusulas sobre privacidad y confidencialidad. No es una solución perfecta, pero es realista.

### 2.4 El Camino Forward

Este análisis nos ha enseñado que la seguridad de SafeRide no es un checkbox que marcamos y olvidamos. Es un proceso continuo de:

- Monitoreo de amenazas emergentes
- Actualización de controles según nuevas técnicas de ataque
- Testing regular y pentesting
- Capacitación del equipo en seguridad defensiva
- Revisión periódica de nuestra postura

Si implementamos los controles propuestos en el Plan de Mitigación con rigor, reducimos nuestro riesgo de **40/50 (CRÍTICO)** a aproximadamente **15-20/50 (BAJO-MEDIO)** en amenazas como GPS Spoofing. Eso es una mejora de seguridad del 50-65%.

Pero también sabemos que no será perfecto. Habrá brechas que descubriremos. La pregunta no es "¿Podemos eliminar todo riesgo?" sino "¿Estamos preparados para responder rápidamente cuando detectemos un problema?" La respuesta debe ser sí.