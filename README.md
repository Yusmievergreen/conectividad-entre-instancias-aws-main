# connectividad-entre-intancias-aws
Documentacion para crear instancias en AWS y establecer conectividad entre ellas a través de la IP publica y privada

# Crear dos instancias Linux AMI 2023 en Amazon EC2

Para crear una instancia Linux AMI 2023 en Amazon EC2, sigue los siguientes pasos:

1. Accede a la [Consola de AWS](https://aws.amazon.com/).
2. En la barra de búsqueda de la consola, escribe "EC2" y selecciona "EC2" en los resultados.


3. En el panel de navegación izquierdo, selecciona "Instancias" bajo "Instancias de EC2".


4. Haz clic en el botón "Lanzar instancias".


5. En "Seleccionar una imagen de máquina (AMI)", elige "Amazon Linux 2023" como la imagen de sistema.


6. En "Seleccionar tipo de instancia", deja seleccionada la opción por defecto, que es "t2.micro".

7. En "Par de claves", selecciona la opción predeterminada o crea una nueva clave si aún no tienes una.


8. En "Configuración de grupos de seguridad", elige "Seleccionar un grupo de seguridad existente" y selecciona "default" en el menú desplegable.


9. En "Configurar almacenamiento", puedes dejar la opción predeterminada o personalizarla según tus necesidades.

10. Haz clic en "Revisar y lanzar instancias".

11. Asegúrate de que todas las configuraciones sean correctas y haz clic en "Lanzar instancias". 

12. Las instancias se lanzarán y podrás ver su estado en la sección "Instancias de EC2" en la consola.

## Establecer conectividad de red entre las instancias

Para establecer la conectividad de red entre las instancias, es necesario crear un grupo de seguridad y agregar reglas de entrada que permitan la conexión.

Sigue estos pasos para crear un grupo de seguridad:

1. Inicia sesión en la [Consola de AWS](https://aws.amazon.com/).

2. Accede al servicio de EC2 siguiendo los pasos descritos anteriormente.

3. En el panel de navegación izquierdo, selecciona "Grupos de seguridad" bajo "Red y seguridad".

4. Haz clic en "Crear grupo de seguridad".

5. Configura el grupo de seguridad:
   - Asigna un nombre y una descripción al grupo de seguridad (opcional pero recomendado).
   - En el campo "VPC", selecciona la Virtual Private Cloud (VPC) en la que deseas crear el grupo de seguridad.

6. Configura las reglas de entrada:
   - Haz clic en "Agregar regla de entrada".
   - Para permitir conexiones SSH, configura la regla de la siguiente manera:
     - Tipo: SSH (puerto 22)
     - Origen: 0.0.0.0/0 (esto permitirá conexiones desde cualquier dirección IP).
   - Para permitir el tráfico ICMP (ping), configura la regla de la siguiente manera:
     - Tipo: ICMP - IPv4
     - Código: -1 (esto permite todos los tipos de mensajes ICMP)
     - Origen: 0.0.0.0/0 (esto permitirá ping desde cualquier dirección IP).

7. Haz clic en "Revisar y crear" para verificar la configuración.

8. Una vez que estés seguro de que todo está configurado correctamente, haz clic en "Crear grupo de seguridad".

## Conectar a las instancias

Para conectarte a las instancias, sigue estos pasos:

1. Selecciona el nombre de la instancia MyWebServer2 y desplázate hacia abajo. En los detalles de la instancia, encuentra la dirección IP privada y cópiala para usarla en el siguiente paso.

2. Navega hacia atrás y haz clic en la instancia desde la que deseas conectarte.

3. Haz clic en "Conectar" en la parte superior derecha.

4. En "Conectarse a la instancia", selecciona la pestaña "Cliente SSH" y copia el DNS público de la instancia.

5. Abre una terminal en tu ordenador y pega el DNS público de la instancia.

6. Ejecuta el comando `ping` a la dirección IP privada de la instancia WebServer2 y comprueba que la conexión sea exitosa.

7. Repite el paso anterior para comprobar la conexión a la dirección IP pública.
