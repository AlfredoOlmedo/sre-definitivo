# SSH

## SSH o Secure Shell 
Es el nombre de un protocolo y del programa que lo implementa cuya principal función es el acceso remoto a un servidor por medio de un canal seguro en el que toda la información está cifrada.

Además SSH permite copiar datos de forma segura (tanto archivos sueltos como simular sesiones FTP cifradas), gestionar claves RSA para no escribir contraseñas al conectar a los dispositivos y pasar los datos de cualquier otra aplicación por una canal seguro tunelizado mediante SSH y también puede redirigir el tráfico del (Sistema de Ventas X) para poder ejecutar programas gráficos remotamente. El puerto TCP asignado es el 22.

## Seguridad
SSH trabaja de forma similar a como se hace Telnet. La diferencia principal es que SSH usa técnicas de cifrado que hacen que la información que viaja por el medio de comunicación vaya de manera no legible, evitando que terceras personas puedan descubrir el usuario y contraseña de la conexión ni lo que se escribe durante toda la sesión; aunque es posible atacar este tipo de sistemas por medio de ataques de REPLAY y manipular así la información entre destinos.

## Historia
Al principio solo existían los R-Commands que eran los basados en el programa rlogin, el cual funciona de una forma similar a telnet.
La primera versión de protocolo y el programa eran libres y los creó un finlandes llamado Tatu Ylonen, pero su licencia fue cambiando y terminó apareciendo la compañía SSH Communications Security, que lo ofrece gratuitamente para uso doméstico y académico, pero exige el pago a otras empresas.

En el año 1997 (dos años después de que creara la primera versión) se propuso como borrador en la IETF
A principios de 1999 se empezó a escribir una versión que se convertiría en la implementación libre por excelencia, la OpenBSD, llamada OpenSSH

## Versiones
Existen 2 versiones de SSH, la versión 1 de SSH hace uso de muchos algoritmos de cifrado patentados(Sin embargo, algunas de estas patentes han expirado) y es vulnerable a un agujero de seguridad que potencialmente permite a un intruso insertar datos en la corriente de comunicación. la suite openssh bajo red hat enterprise linux utiliza por defecto la versión 2 de ssh, la cual tiene un algoritmo de intercambio de claves mejorado que no es vulnerable al agujero de seguridad en la versión 1, sin embargo, la suite openssh también soporta las conexiones de la versión 1


## Cómo funciona SSH
Si usas Linux o Mac, entonces usar el protocolo SSH es muy fácil, si utilizas Windows deberás utilizar un cliente SSH para abrir conexiones SSH. El cliente SSH más popular es Putty
Para Usuarios Mac y Linux, dirígete a tu programa de terminal y sigue este procedimiento

```
ssh {user}@{host}
```

El comando clave SSH le indica a tu sistema que desea abrir una conexión de shell Segura y cifrada. {user} representa la cuenta a la que deseas acceder. {host} Hace referencia al equipo al que quieres acceder. Esto puede ser una dirección ip o un nombre de dominio Al pulsar enter, se te pedirá que escribas la contraseña de la cuenta solicitada. Al escribirla, nada aparecerá en la pantalla, pero la contraseña, se estará transmitiendo. Una vez terminado de escribir, pulsar enter, si la contraseña es correcta, verás una ventana de terminal remota.

## Técnicas de Cifrado

La ventaja del protocolo SSH sobre sus predecesores es el uso del cifrado para asegurar la transferencia segura de información entre el host y el cliente

Host Servidor remoto que se intenta acceder Cliente equipo desde el que se está intentando acceder

### Existen 3 Tecnologías de cifrado
- Cifrado Simétrico
- Cifrado Asimétrico
- Hashing

## Cifrado Simétrico
Se utiliza una clave secreta tanto para el cifrado como para el descifrado, tanto por el cliente como por el host y efectivamente, cualquiera que tenga la clave puede descifrar el mensaje.

A menudo se llama clave compartida (Shared Key), normalmente solo hay una clave que se utiliza, o a veces un par de claves donde una clave se puede calcular fácilmente con la otra clave.

Se utilizan para cifrar toda la comunicación durante una sesión SSH, tanto el cliente como el servidor derivan la clave secreta utilizando un método acordado, y la clave resultante nunca se revela a terceros. El proceso de creación de una clave simétrica se lleva a cabo mediante un algoritmo de intercambio de llaves.

Lo que hace que este algoritmo sea particularmente seguro es el hecho de que la clave nunca se transmite entre el cliente y el host, en lugar de eso, los dos equipos comparten datos públicos y luego los manipulan para calcular de forma independiente la clave secreta. Incluso si otra máquina captura los datos públicamente compartidos, no será capaz de calcular la clave porque el algoritmo de intercambio de clave no se conoce.

Debe tenerse en cuenta que el token secreto es específico para cada sesión SSH y se genera antes de la autenticación del cliente. Una vez generada, todos los paquetes que se mueven entre las dos máquinas deben ser cifradas por la clave privada. Esto incluye la contraseña escrita en la consola por el usuario, por lo que las credenciales siempre están protegidas de los fisgones.

Existen varios códigos cifrados simétricos, incluyendo a AES (Advanced Encryption Standard), Cast 128, Blowfish etc. Antes de establecer una conexión segura, el Cliente y el Host deben decidir qué cifrado usar, publicando una lista de cifrados soportados por orden de preferencia. El Cifrado preferido de entre los soportados por los clientes que presente en la lista del host se utiliza como el cifrado bidireccional.

Ejemplo: si dos máquinas Ubuntu 14.04 LTS se comunican entre si, a traves de SSH, utilizaran AES128-ctr como cifrado predeterminado

## Cifrado Asimétrico

### Hashing
El Hashing unidireccional es otra forma de criptografía utilizada en Secure Shell Connections. Las funciones de hash unidireccionales difieren de las dos formas anteriores de encriptación en el sentido de que nunca están destinadas a ser descifradas. generan un valor único de una longitud fija para cada entrada que no muestra una tendencia clara que pueda explotarse. Esto los hace prácticamente imposibles de revertir

Es fácil generar un hash criptográfico de una entrada dada, pero imposible de generar la entrada del hash. Esto significa que si un cliente tiene la entrada correcta, pueden generar el hash criptográfico y comparar su valor para verificar si poseen la entrada correcta.
SSH utiliza hashes para verificar la autenticidad de los mensajes. Esto se hace usando HMACs, o códigos de autenticación de mensajes basados en hash. Esto asegura que el comando recibido no se altere de ninguna manera.

Mientras se selecciona el algoritmo de cifrado simétrico, también se selecciona un algoritmo de autenticación de mensajes adecuado, esto funciona de manera similar a como se selecciona el cifrado, como se explica en la sección de cifrado simétrico.

Todo mensaje transmitido debe contener un MAC, que se calcula utilizando la clave simétrica, el número de secuencia de paquetes u el contenido del mensaje. Se envia fuera de los datos cifrados simétricamente como la sección final del paquete de comunicaciones.

## Cómo funciona el protocolo SSH con estas técnicas de cifrado.
La forma en que funciona SSH es mediante el uso de un modelo cliente-servidor para permitir la autenticación de dos sistemas remotos y el cifrado de los datos que pasan entre ellos.

SSH opera en el puerto TCP 22 de forma predeterminada (aunque esto se puede cambiar si es necesario). El Host (Servidor) escucha en el puerto 22 (o cualquier otro puerto SSH asignado) para las conexiones entrantes. Organiza la conexión segura mediante la autenticación del cliente y la apertura del entorno de shell correcto si la verificación tiene éxito.

El cliente debe iniciar la conexión SSH iniciando el protocolo TCP con el servidor, asegurando una conexión simétrica segura, verificando si la identidad mostrada por el servidor coincide con los registros anteriores (normalmente grabados en un archivo de almacén de claves RSA) y presenta las credenciales de usuario necesarias para autenticar la conexión.

Hay dos etapas para establecer una conexión: primero ambos sistemas deben acordar estándares de cifrado para proteger futuras comunicaciones y segundo el usuario debe autenticarse. si las credenciales coinciden, se concede acceso al usuario.

## Negociación de cifrado de sesión

Cuando un cliente intenta conectarse al servidor presenta los protocolos de cifrado y las versiones respectivas que soporta. Si el cliente tiene un par similar de protocolo y versión, se alcanza un acuerdo y se inicia la conexión con el protocolo aceptado. el servidor también utiliza una clave pública asimétrica que el cliente puede utilizar para verificar la autenticidad del host
Una vez que esto se establece, las dos partes usan lo que se conoce como algoritmo de intercambio de Claves Diffie-Hellman para crear una clave simétrica. Este algoritmo permite que tanto el cliente como el servidor lleguen a una clave de cifrado compartida que se utilizará en adelante para cifrar toda la sesión de comunicación.

### Aquí es como el algoritmo trabaja en un nivel muy básico:
1. Tanto el cliente como el servidor coinciden en un número primo muy grande, que por supuesto no tiene ningún factor común. Esta valor de número primo también se conoce como el valor semilla (seed value)

2. Las dos partes acuerdan un mecanismo de cifrado común para generar otro conjunto de valores manipulando los valores semilla de una manera algorítmica específica. estos mecanismos, también conocidos como generadores de cifrado,. realizan grandes operaciones sobre la semilla. un ejemplo de dicho generador es AES (Advanced Encryption Standard)

3. Ambas partes generan independientemente otro número primo. Esto se utiliza como una clave privada secreta para la interacción.

4. Esta clave recién generada, con el número compartido y el algoritmo de cifrado, se utiliza para calcular una clave pública que se distribuye a la otra computadora.

5. A continuación, las partes utilizan su clave privada, clave pública y el número primo original para crear una clave compartida final. Esta clave se calcula de forma independiente por ambos equipos, pero creará la misma clave de cifrado en ambos lados.
Ahora que ambas partes tienen una clave compartida, pueden cifrar simétricamente toda la sesión SSH. la misma clave se puede utilizar para cifrar y descifrar mensajes (leer: sección sobre cifrado simétrico)

6. Ahora que se ha establecido la sesión cifrada segura simétricamente, el usuario debe ser autenticado.

## Autenticación del usuario
La etapa final antes de que se conceda al usuario acceso al servidor es la autenticación de sus credenciales, para ello la mayoría de los usuarios de SSH utilizan una contraseña. Se le pide al usuario que introduzca el nombre del usuario, seguido de la contraseña. Estas credenciales pasan con seguridad a través del túnel cifrado simétricamente, así que no hay ninguna posibilidad de que sean capturadas por un tercero.

Aunque las contraseñas se cifran, todavía no se recomienda usar contraseñas para conexiones seguras. Esto se debe a que muchos robots pueden simplemente realizar ataques de fuerza bruta para descifrar contraseñas fáciles o predeterminadas y así obtener acceso a tu cuenta. En vez de esto, la alternativa recomendada es un par de claves SSH
Se trata de un conjunto de claves asimétricas utilizadas para autenticar al usuario sin necesidad de introducir ninguna contraseña

## Conclusión
Obtener una comprensión en profundidad de la forma subyacente de funcionamiento de SSH puede ayudar a los usuarios a comprender los aspectos de seguridad de esta tecnología. La mayoría de la gente considera este proceso extremadamente complejo y poco comprensible, pero es mucho más simple de lo que la mayoría piensa.

Si te estás preguntando cuánto tiempo toma una computadora para calcular un hash y autenticar a un usuario, bueno, sucede en menos de un segundo. De hecho, la mayor cantidad de tiempo se gasta en la transferencia de datos a través de Internet.

Con suerte, este tutorial de SSH te ha ayudado a ver la forma en que se pueden combinar diferentes tecnologías para crear un sistema robusto en el que cada mecanismo tiene un papel muy importante que desempeñar. Además, ahora ya sabes por qué Telnet se convirtió en una cosa del pasado tan pronto apareció SSH.

From
https://www.hostinger.mx/tutoriales/que-es-ssh

## SSH Key
1.  Generar ssh
```
ssh-keygen -t rsa -b 4096 -C "email"
```

2. Nombre
```
.ssh/nombre_rsa
```

3. Ubicación ssh (en usuario) ~
```
cd .ssh/
```

4. Copia de SSH
```
xclip -sel clip < ~/.ssh/id_rsa.pub
```

5. Pegarlo en la ubicacion de por ejemplo Gitlab
```
User Settings
SSH Keys
Key
```

