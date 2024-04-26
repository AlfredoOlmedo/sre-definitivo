# Admnistracion de servidores linux

## Configuracion basica para un servidor remoto

Conocer si está activo
```
systemctl status sshd
```

Conocer la ip
```
ip address
```

Para conectarse
```
ssh user@192.168.0.1
```

## Qué son los sistemas de archivos
Es un sistema que nos permite almacenar, mover, eliminar y buscar archivos, Puede ser compatible o no entre diferentes sistemas operativos

- FAT
- FAT 32
- NTFS
- EXT4
- XFS
- BtrFS
- ZFS

Nota:
- En Windows el mejor es NTFS
- En Linux EXT4 solo para linux
- XFS se a vuelto estándar, es robusto, gran intercambio para - Volatilidad como cluster MongoDB etc

## Particiones de un servidor Linux
#### Todo es un archivo.
  Esto significa que todos los elementos del sistema, como dispositivos de entrada y salida, carpetas, procesos y sockets de red, se representan como archivos en el sistema de archivos. Esto permite que el sistema operativo y las aplicaciones accedan a ellos de manera uniforme utilizando el mismo conjunto de funciones y llamadas al sistema.

Command  | Description

`lsblk` Lista los dispositivos de bloques y las particiones en el sistema

`fdisk` Herramienta para administrar particiones de disco

`parted` Herramienta para crear y administrar particiones de disco

`mkfs` Formatea una partición con un sistema de archivos

`mount` Monta un sistema de archivos en una partición o un directorio

`umount` Desmonta un sistema de archivos

`df` Muestra el espacio libre y utilizado en las particiones montadas

`du` Muestra el tamaño de un archivo o directorio

`resize2fs` Ajusta el tamaño de un sistema de archivos ext2, ext3 o ext4

`lvcreate` Crea un volumen lógico en un grupo de volúmenes LVM

`lvextend` Amplía el tamaño de un volumen lógico

`lvresize` Ajusta el tamaño de un volumen lógico

`lvremove` Elimina un volumen lógico

`vgcreate` Crea un grupo de volúmenes LVM

`vgextend` Amplía un grupo de volúmenes LVM

`vgreduce` Reduce un grupo de volúmenes LVM

`pvcreate` Crea un volumen físico LVM en una partición o dispositivo

`pvextend` Amplía un volumen físico LVM

`pvresize` Ajusta el tamaño de un volumen físico LVM

`pvremove` Elimina un volumen físico LVM

##  Manejo de un archivo swap
Un archivo *swap*, también conocido como espacio de intercambio o memoria virtual, es un espacio en el disco duro que se utiliza para almacenar temporalmente datos que no están siendo utilizados por el sistema operativo

*Modificar swap*

```
sudo fallocate l 2G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
```

Necesitamos modificar el archivo de configuración de arranque, usando VIM

```
vim /etc/fstab
swapfile swap swap defaults 0 0
```

para apagarlo como el tamaño original
```
sudo swapoff /swapfile
```

para regresar al tamaño original tenemos que usar *Vim*

```
vim /etc/fstab
```
y remover la línea
```
swapfile swap swap defaults 0 0
```
Ver tamaño
```
free h
```

## Árbol de directorios

El árbol de directorios en Linux es una estructura jerárquica de directorios y archivos que se utiliza para organizar y almacenar datos en un sistema operativo Linux. Este árbol de directorios comienza en el directorio raíz, representado por una sola barra ( / ), y se extiende a través de una serie de subdirectorios que se organizan en función de su función y contenido.

`*/bin` Contiene archivos binarios ejecutables esenciales para el sistema.

`*/boot` Contiene los archivos necesarios para arrancar el sistema.

`*/dev` Contiene archivos de dispositivos que representan hardware y otros dispositivos del sistema.

`*/etc` Contiene archivos de configuración del sistema.

`*/home` Contiene los directorios personales de los usuarios.

`*/lib` Contiene bibliotecas compartidas necesarias para los programas del sistema.

`*/media` Contiene puntos de montaje para dispositivos extraíbles, como unidades flash USB y discos duros externos.

`*/mnt` Contiene puntos de montaje para sistemas de archivos temporales o permanentes.

`*/opt` Contiene programas y archivos adicionales del sistema.

`*/proc` Contiene información en tiempo real sobre el sistema y los procesos en ejecución.

`*/root` El directorio personal del usuario “root”.

`*/run` Contiene archivos de estado del sistema y otros archivos temporales.

`*/sbin` Contiene archivos binarios ejecutables esenciales para el sistema.

`*/srv` Contiene datos de servicio para servidores web y otros servicios de red.

`*/sys` Contiene archivos de dispositivos virtuales que representan hardware y otros dispositivos del sistema.

`*/tmp` Contiene archivos temporales.

`*/usr` Contiene programas y archivos no esenciales del sistema.

`*/var` Contiene datos variables del sistema, como registros y archivos de caché.

En general, el árbol de directorios en Linux está diseñado para proporcionar una estructura coherente y fácil de entender para el almacenamiento y la organización de datos del sistema, lo que hace que sea más fácil administrar y mantener sistemas Linux.

## Diferentes Tipos de Archivos
#### Archivos regulares
Consiste en una serie de bytes, el sistema de archivos no le impone una estructura Archivos de texto, archivos de datos, programas ejecutables y librerías

#### Directorios`
Contiene referencias a otros archivos   
`/.` referencia al directorio   
`/..` referencia al directorio derivado

#### Hard Links
 Estos links son una copia de una un archivo original, hacen referencia a un punto de la memoria en la que se almacena el archivo

#### Links simbólicos
- También se conoce como soft links, apuntan al archivo original, por una referencia por nombre.
- Si eliminamos el archivo original, el link queda inservible, a diferencia de los hard links

#### Archivos de dispositivos
- De caracteres/bloque 
- Estos archivos permiten que los programas se comuniquen con los periféricos y el hardware
- No son drivers, pero sí definen la comunicación con ellos y el manejo del dispositivo

#### Sockets de dominio local
- Son conexiones entre procesos que intermedian la comunicación, sobre todo lo que involucra la red
- Solo se puede acceder a ellos desde el localhost

#### Named Pipes
- Estos archivos comunican dos procesos que corren al mismo tiempo
- Se conocen como FIFO Files (First in / first out), que pueden entenderse como una pila de procesos


*Permiso* | *Identifica*  
`-`  Archivo    
`d`	Directorio    
`b`	Archivo de bloques especiales   
`c` Archivo de caracteres especiales    
`l`	Link simbólico      
`p` Archivo especial de cauce   
`s`	Socket de dominio

##  Conociendo los repositorios y paquetes

##### Paquetes 
 Incluyen todos los archivos necesarios para ejecutar el software, hacen el proceso de instalación lo mas sencillo posible, porque incluye los archivos binarios, de configuración y dependencias

##### Repositorios 
 Almacena los paquetes para que el usuario pueda descargarlos e instalar el software
Pertenecen a los distribuidores de Linux, aquí se liberan las actualizacione de los paquetes

`.deb`
 Formato de instalación de paquetes de DEBIAN y UBUNTU  
`dpkg`  Herramienta que instala, desinstala y consulta

`.rpm`
 Formato de instalación de paquetes de Red Hat, CentosOS, SUSE, Amazon Linux    
 `rpm`  Herramienta que instala, desinstala y consulta

#### Comandos 

install / remove  
`l` list  
`i` install   
`q` query, acompaña con una bandera   
`U` upgrade   
`e` erase


## Que es un manejador de paquetes

Debian / Ubuntu 
 apt  debian ubuntu
 apt version

Red Hat, CentosOS, SUSE, Amazon Linux
 dnf version
 yum version

Comandos

ver los pkg instalados
dnf list installed 

guardar la lista de los pkg instalados
dnf list  installed > paquete

buscar un pkg
dnf search pkg

actualizarlos
sudo dnf update pkg

remover
sudo dnf remove pkg


Nota 
dnf es para REDHAT


## Como instalar Software

Instalar 

sudo apt install <nombre_del_paquete>


Podemos enviar un pkg a la carpeta de ./bin para ejecutarlos previamente le tenemos que dar chmod

chmod +x paquete


Referencias 
 App stores for Linux

Snapcraft   snapcraft.io
Flatpak     flatpak.org


## Manejo de Repositorios a profundidad

Muestra todos los repositorios

cat /etc/apt/sources.list


Tipos de Repositorios
 Universe
 Multiverse

Ver Repositorios

sudo addaptrepository universe
sudo addaptrepository multiverse


activar repositorio

dnf configmanager setenabled repositorio


Referencias 

ITSFOSS Ubuntu      itsfoss.com
RPMFUSION RedHat    rpmfusion.org


## Que es un proceso
Un proceso representa una referencia a un programa ejecutándose dentro de nuestro sistema, el cual puede ser controlado y monitoreado
Esto hace uso de recursos de memoria, de I/O, de procesamiento etc.

Demonio 
 Son procesos que se ejecutan en segundo plano, ejecutándose de forma persistente o reiniciando de forma automática bajo ciertas condiciones
 Usualmente, se inician en el arranque del sistema

Señales 
 Son procesos de bajo nivel que sirven como peticiones en el ámbito de kernel para interrumpir otros procesos

Comandos

ps aux 

ps aux grep

pidof less "del archivo ejecutado"

top monitor de procesos
htop monitor de procesos mejorado



## Manejo de Procesos
Running or Runnable (R)
Uninterrumptible Sleep (D)
Interrumpible Sleep (S)
Stopped (T)
Zombie (Z)

La forma mas rápida de mandar un archivoproceso al background es &

less archivo &


la forma de listar los comandos en segundo plano

jobs l


para traerlos de vuelta es

fg [número]


matar proceso

kill N_Proceso


para matar procesos en Bakground

kill s proceso N_Proceso


mátalos a todos los procesos asociados al que quieres matar

killall Nombre_Proceso



## Creación y Manejo de Demonios

systemd  es un manejador de servicios de sistema
systemctl  controla el systemd

si queremos crear un demonio lo tenemos que agregar a systemd 


ver el estado de un demonio

systemctl status daemon


## Automatización de procesos con Cron job


systemctl status cron


ubicación

ls /var/spool/cron/crontabs/


editar crontab

crontab e
