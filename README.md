# Implementing-Security-Controls-with-OX
**Objetivo**: Establecer un modelo de seguridad automatizado en el ciclo de desarrollo utilizando OX Security. Se requiere implementar bloqueos preventivos de código, controles centralizados en el pipeline y un sistema de excepciones inmutable gestionado íntegramente desde la plataforma OX.
## 1. Implementación de Push Bloqueante (Prevención de Subida)
**Contexto**: Se necesita evitar que código con vulnerabilidades severas llegue al repositorio remoto. La validación debe ocurrir en la máquina del desarrollador en el momento exacto en el que intenta enviar el código.
* **Definición de Umbrales**: Configurar el escáner local de OX para que identifique y catalogue vulnerabilidades. El foco estricto de bloqueo debe configurarse para niveles de severidad **Alta** (High) y **Crítica** (Critical).
* **Configuración del Hook de Bloqueo**: Implementar la validación mediante el CLI de OX integrado como un evento de validación local (pre-push). Si el CLI de OX detecta una vulnerabilidad Alta o Crítica, la acción debe devolver un error fatal en la terminal del desarrollador, abortando la subida del código inmediatamente.
## 2. Bloqueo de Security Gates desde la Plataforma OX
**Contexto**: El control sobre qué detiene un despliegue no debe residir en scripts aislados, sino que debe ser gobernado y auditado centralizadamente desde la consola de OX Security.
* **Configuración de Políticas (Enforcement)**: Establecer las reglas de negocio dentro del panel de administración de OX Security. Se debe crear una política que dicte un estado de "Rechazado/Fallido" cuando se detecten vulnerabilidades Altas o Críticas sin resolver en un repositorio.
* **Integración en la Pipeline**: Añadir el componente de OX Security a la pipeline de integración continua (ej. GitHub Actions). La pipeline simplemente debe consultar a OX; si OX determina que la política centralizada se incumple, la pipeline debe adoptar el estado bloqueante y cancelar el proceso de construcción o despliegue.
## 3. Proceso de Excepciones Gestionado en OX
**Contexto**: Se requiere un flujo auditable y seguro para gestionar falsos positivos o riesgos temporalmente aceptados, erradicando el uso de ficheros manuales en el código que son propensos a manipulaciones de fechas.
* **Solicitud Centralizada**: El equipo de desarrollo debe utilizar la interfaz o los enlaces generados por OX en los reportes de vulnerabilidad para solicitar una excepción formalmente, detallando el motivo y la fecha de caducidad necesaria.
* **Aprobación y Efecto Dinámico**: La revisión de excepciones se realizará exclusivamente a través de la interfaz de OX Security por personal autorizado. Una vez que OX aprueba la excepción, la plataforma actualizará automáticamente la respuesta del "Security Gate", permitiendo que la pipeline pase a verde sin requerir cambios adicionales en el código.
* **Caducidad Automática**: Configurar las excepciones para que expiren estrictamente en la fecha acordada. Una vez superada, OX volverá a marcar el hallazgo como bloqueante de forma automática.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Referencias de Documentación para Ejecución
El equipo asignado deberá consultar las siguientes secciones de la documentación oficial de OX Security para implementar las tareas descritas:
* **Para el Push Bloqueante**:
  * Instalación y parámetros de control del cliente local: `docs.ox.security/cli/installation`
  * Configuración de integraciones de bloqueo pre-push: `docs.ox.security/cli/pre-push-hook`
* **Para el Bloqueo de Security Gates en Pipeline**:
  * Implementación de políticas restrictivas: `docs.ox.security/policy/pipeline-enforcement`
  * Integración del estado bloqueante en repositorios: `docs.ox.security/integration/github-enforcement`
* **Para la Gestión de Excepciones**:
  * Administración del ciclo de vida de excepciones en la plataforma: `docs.ox.security/workflow/exception-management`
 
