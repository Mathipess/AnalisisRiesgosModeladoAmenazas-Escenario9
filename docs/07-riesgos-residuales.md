# Evaluación de Riesgos Residuales y Conclusiones

Identificación y justificación formal de los riesgos remanentes una vez aplicados todos los controles de mitigación tecnológica del plan de seguridad.

## 1. Matriz de Riesgos Residuales Aceptados

* **R01: Spoofing por Hardware Avanzado (Simuladores Físicos RF):** Modificación física de la antena del smartphone mediante hardware de simulación satelital que burla los chequeos de software tradicionales del sistema operativo.
    * *Tratamiento:* **Aceptado.** La probabilidad remanente se reduce a nivel *Bajo* gracias al algoritmo backend de plausibilidad cinemática (que detecta las velocidades absurdas en el servidor). Desarrollar contramedidas de radiofrecuencia de hardware es inviable a nivel de costo-beneficio para el modelo de negocio.
* **R02: Exfiltración de datos visuales por Ingeniería Social (Fotografía Física):** Captura fotográfica o grabación de video externa (usando otro teléfono físico) de la pantalla de un conductor mostrando los datos en curso o el rostro de un pasajero.
    * *Tratamiento:* **Aceptado y Transferido.** Se mitiga parcialmente reduciendo al mínimo indispensable los datos personales visibles en la app y truncando las direcciones exactas a aproximaciones tras culminar el servicio. El riesgo legal residual es transferido mediante los contratos de Términos y Condiciones firmados por los conductores.

## 2. Conclusiones Generales del Equipo de Análisis

1. **Arquitectura Zero-Trust Obligatoria:** Las aplicaciones móviles operan en un entorno salvaje y no confiable. Toda la validación lógica del negocio de geolocalización debe recaer rigurosamente sobre el servidor Node.js.
2. **Ciclo de Vida de API Seguro:** Los fallos de control de accesos funcionales (IDOR) representan la mayor amenaza para la privacidad del negocio. Es indispensable implementar pruebas automatizadas de seguridad (DAST/SAST) integradas en el pipeline de CI/CD cada 6 meses.