# Curso de administración de Servidores Linux  Manejo de Recursos

## Como es el arranque del sistema

 EL SO es almacenado en memoria
 Revisión de Hardware
 Selección del dispositivo de arranque
 Carga de Kernel
 Determina el Kernel a usar
 Carga del bootloader
 Detección de la Partición EFI
 Se Carga el primer proceso (PID1)
 Ejecuta scripts de inicio
 Inicia el sistema

![Arranque del sistema](arrangueSistema.jpg)

Firmware del sistema 
Hace un inventario y chequeo de todos los dispositivos conectados al sistema en el momento de arranque (discos, memorias etc). Este a su vez crea interfaces para que el software del sistema operativo pueda usar estos dispositivos.

BootLoader 
Separa el firmware del sistema y el arranque del sistema operativo. Es un paso previo a que ejecute el sistema operativo.
Es útil para correr el SO en forma de rescate o con parámetros extra.

GRUB / The Grand Unifier Boot Loader 
Es el bootloader por defecto en la mayoría de distribuciones Linux
Actualmente contacta con dos versiones 
 GRUB Legacy
 GRUB 2

BIOS vs UEFI 
Sirven para revisar todo el Hardware y arrancar el SO pero funcionan de maneras diferentes
BIOS  El arranque del sistema Legacy aprox 1975 es más lento que UEFI, Master Boot Record particion primitiva de disco 512 bytes, reserva sectores para determinar qué sistema va a arrancar

UEFI 
Usa un sistema de particiones, llamado EFI partición especial de montaje que es similar al FAT12
este sistema de particiones si puede ser modificada

## Modo Recovery

Modo recovery 
En el contexto de Linux, el "modo de recuperación" (recovery mode en inglés) es una opción de arranque especial que proporciona un entorno de trabajo mínimo con privilegios de administrador (root) para solucionar problemas o realizar tareas de mantenimiento en un sistema Linux. También se conoce como "modo de emergencia" o "modo de rescate".

Cuando se inicia en el modo de recuperación, el sistema operativo Linux se inicia con un conjunto mínimo de servicios y controladores. Esto permite al usuario realizar diversas acciones, como 

Recuperación de contraseñas 
En el modo de recuperación, se puede modificar o restablecer contraseñas de usuarios, lo que resulta útil si se ha olvidado una contraseña y no se puede iniciar sesión en el sistema.

Reparación del sistema de archivos 
Si el sistema de archivos tiene errores o problemas de integridad, se puede utilizar el modo de recuperación para realizar una comprobación y reparación del sistema de archivos.

Modificación de configuraciones 
El modo de recuperación permite editar archivos de configuración importantes, como el archivo /etc/passwd, /etc/group, /etc/sudoers y otros, lo que permite realizar cambios necesarios para solucionar problemas.

Actualización de software 
En algunos casos, se puede utilizar el modo de recuperación para actualizar o instalar software adicional o corregir paquetes rotos que están causando problemas en el sistema.

Resolución de problemas de red 
En el modo de recuperación, se pueden realizar pruebas de conectividad de red y solucionar problemas relacionados con la configuración de red, como la configuración de interfaces de red o problemas con el servidor DHCP.

Es importante tener en cuenta que el modo de recuperación proporciona un acceso de nivel de administrador al sistema, por lo que se debe tener cuidado al realizar cambios para evitar daños o alteraciones no deseadas.

## Qué son los grupos y usuarios en Linux

Usuarios 
Nos permite separar las responsabilidades y permisos de acciones en el sistema
Dependiendo de los permisos que tengan son las acciones que podrán ejecutar

Los usuarios suelen tener  
UID  Identificador único del sistema
GIDs uno o más IDs que los relacionan a un grupo
Directorio Home está en la ruta /home/<username>

Archivo /etc/passwd
Contiene información de nuestros usuarios en el siguiente formato

name password UID GID GECOS directory shell

Contiene información de las contraseñas de usuario de forma cifrada
Si el campo password tiene un *, entonces el usuario nunca ha tenido contraseña
Si el campo password tiene un !, entonces el usuario ha sido bloqueado

Grupos
Sirven para agrupar a los usuarios y un conjunto de permisos

## Manejo de Usuarios


etc/passwd



ao7   x   1000   1000   ao7 ...   / home / ao7   / bin / bash 

ao7             nombre usr
x               password cifrado
1000             user id
1000            group id
ao7             información gecos
/ home / ao7    ruta home
/ bin / bash    terminal

Shadow Guarda información acerca del password del usuario

/etc/shadow

gecos información

Full Name []
Room Number []
Work Phone []
Home Phone []
Other []

Para modificar el gecos

chfn usuario


deshabilitar usuario

usermod lock usuario


eliminar un usuario
 tienes que eliminar los procesos
 con el root 
 pones el siguiente comando 

sudo rm rf /home/usuarioABorrar

Nota 
Cuando creas un nuevo usuario, por defecto No existe como administrador
después podemos otorgarle privilegios mediante incorporandolo a un grupo

## Manejo de Grupos

Los grupos nos ayudan para repartir permisos a diferentes usuarios e inclusive agruparlos

ubicación

/etc/group


ver si un usuario está en algún grupo

less /etc/group  grep ao7


grupos

groups

usuarios que pertenecen a algún grupo

getent group sudo


Crear un Grupo

groupadd amigos


cambiar el nombre de un grupo (primero se agrega el nombre que queremos y después el nombre a modificar) 

sudo groupmod n friends amigos 


Crear carpeta compartida entre 2 usuarios

adduser fulano


agregar usuarios a una carpeta compartida

usermod aG grupo usuario

a append
G group 

Remover usuario

su root
gpaaswd a usuario


Eliminar Grupo

Nota 
en la carpeta para compartir entre usuarios, crear carpeta, cambiar permisos
chmod 770 
owner todos los permisos, grupo todos los permisos, los demás Nada 

Para manejar grupos de usuarios en Linux, se pueden seguir los siguientes pasos 

1.  Verificar los grupos existentes  se puede usar el comando cat /etc/group para mostrar una lista de los grupos existentes en el sistema.

2. Crear un nuevo grupo  se puede utilizar el comando sudo groupadd <nombre_del_grupo> para crear un nuevo grupo en el sistema.

3. Agregar usuarios a un grupo  se puede utilizar el comando sudo usermod a G <nombre_del_grupo> <nombre_de_usuario> para agregar un usuario existente al grupo.

4. Verificar los usuarios de un grupo  se puede utilizar el comando id <nombre_del_grupo> para mostrar una lista de usuarios que pertenecen a un grupo.

5. Eliminar un grupo  se puede utilizar el comando sudo groupdel <nombre_del_grupo> para eliminar un grupo existente en el sistema.

6. Cambiar los permisos de un archivo o directorio para un grupo  se puede utilizar el comando sudo chgrp <nombre_del_grupo> <ruta_al_archivo_o_directorio> para cambiar el grupo propietario de un archivo o directorio. Luego se puede utilizar el comando sudo chmod g+<permisos> <ruta_al_archivo_o_directorio> para otorgar permisos específicos para el grupo propietario.

7. Cambiar el nombre de un grupo  se puede utilizar el comando sudo groupmod n <nuevo_nombre> <nombre_actual> para cambiar el nombre de un grupo existente.

8. Verificar los permisos de un grupo  se puede utilizar el comando sudo getfacl /ruta/al/archivoodirectorio para verificar los permisos de un archivo o directorio. En la salida del comando, se puede observar información sobre los permisos de usuario, grupo y otros.

9. Agregar usuarios a un grupo secundario  se puede utilizar el comando sudo usermod a G <nombre_del_grupo_secundario> <nombre_de_usuario> para agregar un usuario existente a un grupo secundario.

10. Eliminar usuarios de un grupo  se puede utilizar el comando sudo gpasswd d <nombre_de_usuario> <nombre_del_grupo> para eliminar un usuario existente de un grupo.
    
11. Verificar los permisos de un grupo específico  se puede utilizar el comando sudo visudo para abrir el archivo de configuración sudoers, y luego agregar la siguiente línea para permitir que los usuarios del grupo tengan permisos de superusuario  %<nombre_del_grupo> ALL=(ALL) ALL.

12. Verificar los grupos de un usuario  se puede utilizar el comando groups <nombre_de_usuario> para mostrar una lista de grupos a los que pertenece un usuario específico.

## El control de accesos en linux
Para linux todo es un archivo  objeto

Control de Accesos 
 Depende del usuario y las acciones que quiera realizar (permitidas o denegadas)
 Quien crea el objeto es dueño de el
 La cuenta root puede acceder a cualquier objeto que quiera de las demás cuentas
 Solo la cuenta root puede hacer ciertas operaciones 
 No acceder directamente desde la cuenta root, mejor usar su
 Otorgar permisos de administrador solo a los usuarios necesarios y revocar accesos después de cierto tiempo
 Hardening

## Creacion de un usuario administrador

Para crear o agregar un usuario como administrador "sudo"
se tiene que agregar a un archivo de linux

sudo /etc/sudoers

se edita con VISUDO que es parecido a Vim

línea 
# Allow members of group sudo to execute any command
%sudo ALL=(ALL ALL) ALL

Regla ALL=(ALL ALL) significa que tenga acceso completo

Nota 
Controla los Administradores
Nunca uses el Root
Revoca los derechos de sudo si algun usuario dejó de trabajar en la empresa

## Particionando y montando una unidad

Listar particiones después de crear el disco .

lsblk

sudo fdisk l


Comando para crear particiones   sudo fdisk /dev/sdb

F   listar las particiones en fdisk

    Creando nueva partición fdisk  n

    Seleccionar el tipo de partición  p (primaria)

    Seleccionar entre 14 tamaño inicial por defecto  1

    Indicar el tamaño que quieres la partición   +4G tamaño en Gigabytes.

    Por defecto te crea una unidad llamada "sdb1" con el tamaño asignado.

    Realiza el proceso con la segunda unidad presionando ENTER para que use el tamaño de disco restante.

    Para guardar los cambios presione   w

    Formatear partición con ext4   sudo mkfs.ext4 /dev/sdb1

    Montar la partición  crea una carpeta con mkdir "scripts"   sudo mkdir scripts.

    Comando para montar  sudo mount /dev/sdb1 /scripts

    Desmontar unidad   sudo umount /dev/sdb1/scripts

    Editar el file system para que el disco se monte en el inicio del sistema 

sudo vim /etc/fstab

línea que debes agregar  /dev/sdb1 /scripts ext4 defaults 0 0

12+1  Guardar cambios y reiniciar.

Si tienes problemas o escribiste mal puedes ingresar en modo recovery.

## Que es el RAID y LVM

RAID
Redundant Array of Independent Disks 
Nos permite crear discos discos redundantes en caso de fallos sacrificando espacio

![RAID](RAID.jpg)

LVM
Logical Volume Manager 
Es un gestor lógico de discos en Linux que permite redimensionar sectores

![LVM](LVM.jpg)

LVM + RAID
Nos permite hacer uso de los beneficios de ambos arreglos  tener la redundancia que nos ofrece RAID, y el dinamismo en la administración de particiones que nos ofrece LVM.

![LVM sobre RAID](LVM+RAID.png)

## Creación de sistemas RAID 1

Creación de un sistema RAID 1

Añadimos 2 discos físicos en nuestro VirtualBox, los cuales deben ser del mismo tamaño.

Iniciamos nuestra máquina virtual.

Creamos las particiones virtuales con los comandos 


fdisk /dev/sdb
n → crea partición
p → crear partición primaria
Elegimos el primer sector para guardar nuestra partición.
Elegimos qué tamaño deseamos para la partición  +3G
p → Nos muestra la tabla de particiones.
t → cambia el tamaño de las particiones.
w → Guardar los cambios (cuidado, una vez hecho, no hay vuelta atrás).

Repetimos el proceso para el segundo disco.

Validamos la creación con 

lsblk

Creamos nuestro arreglo RAID con una herramienta de instalación de medios, que deberemos instalar 

apt install mdadm

luego, ejecutamos el programa para crear el volumen lógico 

mdadm create /dev/md0 level=1 raiddevices=2 /dev/sd{c,d}

Validamos la creación con 

lsblk

Para mayor información debemos ingresar el siguiente comando 

mdadm misc detail /dev/md0


Nota  
Se usa un apt llamado MDM Manage Device Manager

mdadm


## Creación de LVM sobre RAID 1

Creación de LVM sobre RAID1

Instalamos el paquete 

apt install lvm2


Creamos primero el PV (Physical Volume) que aloja el LVM (Logical Volume) 

pvcreate /dev/md0


Validamos que se haya creado el PV con el siguiente comando 

pvdisplay


Creamos ahora nuestro grupo de volúmenes (VG) 

vgcreate volumegroup /dev/md0


Validamos que se haya creado el VG con el siguiente comando 

vgdisplay


Finalmente, crearemos las particiones más pequeñas 

lvcreate name newname1 size 1Gb volumegroupname1
lvcreate name newname2 size 1Gb volumegroupname2
lvdisplay


## Agregando el sistema a FSTAB

Una vez creados los RAID y los Volúmenes lógicos, ya podemos pasar a montarlos en nuestro sistema para poderles dar uso.

Pasos 

1 Formateamos a EXT4.
2 Agregar a fstab para poderlas usar.
3 Extras  puedes crear permisos, grupos, etc.
    Para formatear el sistema, escribimos 

mkfs.ext4 /dev/volumegroup/public


Confirmamos con 

lsblk


Ahora procederemos a montarlos 

cd / →Vamos al directorio principal
ls la → Listamos
mkdir public && mkdir private → Creamos las carpetas.
sudo mount /dev/volumegroup/public /public →Montamos la unidad sobre esa carpeta
touch /public/new_file.txt
ls /public


Finalmente, los añadiremos al archivo fstab, escribiendo 

vim /etc/fstab


En el archivo de configuración añadimos 

/dev/volumegroup/private /private ext4  defaults    0       0
/dev/volumegroup/public/public ext4  defaults       0       0


## Preparando el sistema

Recuperar GRUB

Cuando nuestro GRUB se desconfigura (que es un evento bastante común), debemos estar en la capacidad de restaurarlo, para ello debemos seguir las siguientes indicaciones 

La carpeta donde se aloja el archivo de configuración es el siguiente  /boot/grub/grub.cfg
 Primero, romperemos nuestro grub, de tal manera que podamos repararlo 

sudo mv /boot/grub/grub.cfg.bck → Cambia el nombre del archivo original de grub.cfg


Reiniciamos nuestra máquina virtual con 

sudo reboot


## Escalando el sistema con CHRoot e instalando Grub

Reparando el archivo grub con chroot

Para poder reparar el archivo debemos hacer un escalamiento de privilegios a través de chroot, esto aprovechando una vulnerabilidad del sistema de linux. Para esto es importante tener en cuenta que los discos no han sido cifrados.

Iniciamos como si fuéramos a instalar una nueva máquina virtual, pero en la misma máquina de Ubuntu.

 Vamos a configuración > Storage >Controller IDE > seleccionamos nuestra distribución de Ubuntu.
 Iniciamos la máquina virtual.
 Seleccionamos try or install Ubuntu.
 En la pantalla de login, presionas  fn + f2 para abrir una nueva consola.
 Lo primero que haremos será crear una contraseña al usuario root.


sudo passwd


Luego validamos las particiones o discos existentes con 

fdisk l  less


Vamos a la carpeta home del usuario 

cd /


Montamos la unidad que contiene el file system que validamos con el comando fdisk, en este caso es el sda2 

mount /dev/sda2 /mnt


Para acceder a los archivos dañados bastará con acceder a la carpeta que los contiene, para ello deberemos saber la ruta 

ls /mnt/boot/grub/


Ahora haremos el montaje de todo el sistema uniendo los archivos de nuestro sistema live con los del SO estropeado 

mount o bind /dev/     /mnt/dev
mount o bind /dev/pts  /mnt/dev/pts
mount o bind /proc     /mnt/proc
mount o bind /run      /mnt/run
mount o bind /sys      /mnt/sys


Luego, para volver a ser el usuario root del sistema corrupto (en lugar del root del live SO), debemos emplear el comando chroot (change root), así 

chroot /mnt /bin/bash → Lo cual nos abrirá una shell con permisos del usuario root del SO que fue reparado. 


Después, para reparar el grub, debemos tipear 

grubmkconfig o /boot/grub/grub.cfg


Finalmente, si queremos instalar este grub debemos escribir 

grubinstall bootdirectory=/boot/ recheck /dev/sda


Hacemos un ls /boot/grub para validar que todo esté correcto; cerramos sesiones con éxito y apagamos la máquina.

Ya solo queda eliminar la imagen live, iniciar la máquina e iniciar sesión.
