# Vincular nuestra cuenta de GitHub con OX Security
Actualmente ya tenemos nuestro código que queremos escanear en un repo de GitHub, en este paso vamos a vincular nuestra cuenta de GitHub con OX Security para así escanear el repo.

## Para vincular tu cuenta de GitHub con OX Security, sigue estos pasos:
1. Accede a la plataforma de OX Security e inicia sesión con tus credenciales de GitHub.
2. Al no tener nada aún, te saldrá automáticamente un panel para integraciones o conexiones. Selecciona GitHub como proveedor de código fuente.
3. Serás redirigido a GitHub para autorizar el acceso. Asegúrate de conceder los permisos necesarios para que OX Security pueda acceder a tus repositorios.
4. Una vez autorizada la integración, regresa a OX Security y selecciona el repositorio que deseas escanear.
5. Por último, confirma la configuración y espera hasta que se muestren los resultados.

<img width="1707" height="993" alt="image" src="https://github.com/user-attachments/assets/10682798-7065-4902-a075-446bf93f4e03" />
💡 Tip: Si trabajas con repositorios privados, asegúrate de otorgar permisos adecuados durante la autorización para evitar problemas de acceso.

## OX In Pipeline 
Ahora mismo si vamos a Applications dentro de OX y seleccionamos el repo, nos saldrá que OX in Pipeline está deshabilitado. 
<img width="925" height="663" alt="image" src="https://github.com/user-attachments/assets/0b633a7f-6780-408d-acbf-7c79a14f5105" />

Esto significa que OX no está ejecutándose como parte de tus builds y por tanto, no puede bloquear nada. Para habilitarlo, debemos crear un flujo en nuestro repo que lo llame (un YAML) o usar la integración nativa que es más sencillo. Para ello:
1. En el panel anterior, le damos a la opción de Pipeline Setting que nos aparece abajo.
2. Esto nos abrirá el panel que vemos en la primera imagen, seleccionamos _Block on Timeout_, habilitamos _GitHub Checks_ y en Default Branch seleccionamos _Pull Request_
3. Luego, abrimos la opción que aparece arriba de _Navigate to Pipeline Workflows_ y seleccionamos el Default Workflow, esto hará que OX en el Pipeline esté habilitado
   
<img width="2560" height="1169" alt="image" src="https://github.com/user-attachments/assets/4ec570d8-3934-4c20-a73b-9b51aaac54cf" />
