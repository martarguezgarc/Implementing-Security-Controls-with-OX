# 1 Implementación de Push Bloqueante (Prevención de Subida)
**Contexto**: Se necesita evitar que código con vulnerabilidades severas llegue al repositorio remoto. La validación debe ocurrir en la máquina del desarrollador en el momento exacto en el que intenta enviar el código.

## Definición de Umbrales 
Configurar el escáner local de OX para que identifique y catalogue vulnerabilidades. El foco estricto de bloqueo debe configurarse para niveles de severidad Alta (High) y Crítica (Critical).
1. Dentro de OX Security, nos vamos a la sección Pipeline Workflows y creamos uno nuevo. Para este ejemplo solo voy a detectar problemas de SAST y SCA para ello selecciono las opciones:
    * Any Code Security policy
    * Any Open Source Security policy
    * SAST issue
    * Secret in code
2. De que tenemos las reglas, configuramos la condición. Para nuestro ejemplo, queremos que las High o superiores bloqueen el pipeline, mientras que las Medium o inferiores solo notifiquen, por ello creo dos condiciones para cada caso de forma que el diagrama queda así:
<img width="1184" height="766" alt="image" src="https://github.com/user-attachments/assets/0cd78bde-5ce7-40d3-ac61-39f202d0a058" />
<br>
3. Para que mi aplicación pase por este flujo, debo seleccionarlo dentro de Pipeline Settings de la aplicación
<img width="1827" height="942" alt="image" src="https://github.com/user-attachments/assets/1569bba6-e12e-482c-a9b1-c5dfbe612767" />
<br>
4. Ahora si, al hacer un commit con errores, nos saldrá el icono del círculo marrón de que está siendo escaneado el commit y luego este error
<img width="968" height="590" alt="image" src="https://github.com/user-attachments/assets/b07a8dfd-384a-4d65-b879-83c7beafe727" /> 
<br>
5. En el apartado de Actions de GitHub no nos saldrá nada, solo sabremos que el commit ha fallado por el históricos de commit y porque en la interfaz de OX Security, en Pipelines Summary veremos que ha bloqueado el flujo
<img width="1816" height="491" alt="image" src="https://github.com/user-attachments/assets/46ab5dfe-1f63-46e8-8746-2b6676748b08" />

## Configuración del Hook de Bloqueo 
Implementar la validación mediante el CLI de OX integrado como un evento de validación local (pre-push). Si el CLI de OX detecta una vulnerabilidad Alta o Crítica, la acción debe devolver un error fatal en la terminal del desarrollador, abortando la subida del código inmediatamente.
[No se puede completar ya que por restricciones del entorno no puedo ejecutar correctamente ox-cli]
