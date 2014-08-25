=== MANUAL DE INSTALACI�N DEL FBPLUGIN v1.0 ===

Advertencia: este plugin ha sido desarrollado para Moodle 2.5.5+, tanto la instalaci�n como el funcionamiento de dicho plugin
no esta garantizado para una versi�n de Moodle que no sea la misma.

Para empezar, "fbplugin" se sincroniza con el plugin "mod_feedback" (versi�n 2013050100). As� pues, lo primero ser� confirmar que nuestro sitio Moodle disponga de este m�dulo y que est� habilitado. Es posible hacer dichas comprobaciones navegando a "Administraci�n del sitio > Extensiones > Vista general de extensiones".

Siguiendo los pasos de "Usuarios como clientes con ficha" en "Administraci�n del sitio > Extensiones > Servicios Web > Vista general" o en https://docs.moodle.org/25/en/Using_web_services resulta sencillo activar el uso de Web Services en nuestro sitio Moodle. A continuaci�n se resumen los pasos principales, incluyendo la instalaci�n del plugin:

1� Activaci�n de las Web Services:

En "Administraci�n del sitio > Caracter�sticas avanzadas", habilitamos los servicios web.

2� Activaci�n del protocolo REST

En "Administraci�n del sitio > Extensiones > Servicios Web > Administrar protocolos", habilitamos el protocolo REST.

3� Instalaci�n del Plugin:

Procedemos a la instalaci�n del plugin en nuestro sitio Moodle, lo que a�adir� las funciones necesarias para que la app
funcione correctamente y crear� un servicio que contenga a las mismas.

Para ello, copiamos el plugin en la carpeta "local" de nuestra instalaci�n de Moodle, que debe quedar de esta manera: "/local/fbplugin".
Al ingresar en la web con permisos de administrador, se disparar� un aviso en el que debemos aceptar la instalaci�n del nuevo plugin (actualizar base de datos de Moodle) para que realmente surjan los cambios.

Nota: cada vez que se quieran actualizar los ficheros del plugin en Moodle, no bastar� con sustituir dichos ficheros, adem�s de deber� de incrementar el n�mero de versi�n del plugin que se encuentra en "" y un usuario con permisos de administrador deber� permitir dicho cambio accediendo a la web.

4� Configuraci�n del "shortname" del servicio:

En esta versi�n de Moodle, no existe la asignaci�n de "shortnames" por web. La inserci�n de este dato debe de ser manual, manipulando directamente la base de datos. En futuras versiones, es posible que la asignaci�n sea m�s sencilla: https://tracker.moodle.org/browse/MDL-29807

Para asignar un shortname al nuevo servicio instalado con el plugin, se debe acceder a la tabla "mdl_external_services"
de la base de datos y asignar manualmente un nombre al servicio "Service for fbplugin". La app esta implementada para que funcione con el nombre "wsfbplugin", as� que cualquier otro nombre diferente har� que la app no conecte con el plugin instalado.

Nota: modificar la app para cambiar el shortname por defecto es f�cil, simplemente hay que modificar la variable global "WS_short_name"
que se encuentra declarada en el archivo "index.html".

5� Habilitando permisos:

Debemos activar dos permisos necesarios para que los usuarios puedan usar el nuevo servicio.

- Permite la creaci�n de calves de seguridad por los usuarios: moodle/webservice:createtoken

- Permite el uso del protocolo REST: webservice/rest:use

Podemos hacer este paso de varias maneras, pero se recomienda a�adir estos permisos al rol "Usuario Identificado" para que cualquier persona con cuenta en Moodle, pueda acceder sin errores a la aplicaci�n (disponga o no de encuestas que completar). Otras posibilidades son la de a�adir estos permisos a otros roles como el de "Estudiante" o crear un rol propio que a�ada estos permisos y asignarlo a los usuarios.

Recomendaciones:

Se recomienda que se habilite HTTPS con un certificado v�lido, para evitar problemas de seguridad.

Problemas:

Para cualquier problema, contactar con Alejandro Molina Salazar (amolinasalazar@gmail.com).

M�s informaci�n:

https://docs.moodle.org/25/en/Using_web_services
https://docs.moodle.org/dev/Creating_a_web_service_client