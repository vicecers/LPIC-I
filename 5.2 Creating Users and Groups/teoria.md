Áreas de conocimiento clave

-   Comandos de usuario y de grupo
    
-   Identificadores de los usuarios (IDs)
    

Lista parcial de archivos, términos y utilidades

-   `/etc/passwd`,  `/etc/shadow`,  `/etc/group`,  `/etc/skel/`
    
-   `useradd`,  `groupadd`
    
-   `passwd`
## Introducción

Administrar usuarios y grupos en un equipo con Linux es uno de los aspectos clave de la administración del sistema. De hecho, Linux es un sistema operativo multiusuario en el que varios de estos pueden usar la misma máquina al mismo tiempo.

La información sobre usuarios y grupos se almacena en cuatro archivos dentro del árbol de directorios  `/etc/`:

`/etc/passwd`

Es un archivo de siete campos delimitados por dos puntos que contiene información básica sobre los usuarios.

`/etc/group`

Es un archivo de cuatro campos delimitados por dos puntos que contienen información básica sobre grupos.

`/etc/shadow`

Es un archivo de nueve campos delimitados por dos puntos que contienen contraseñas cifradas de los usuarios.

`/etc/gshadow`

Es un archivo de cuatro archivos delimitados por dos puntos que contienen contraseñas cifradas de los grupos.

Todos estos archivos se actualizan mediante un conjunto de herramientas de línea de comandos para la administración de usuarios y grupos, las cuales discutiremos más adelante en esta lección. También se pueden administrar mediante aplicaciones gráficas según la distribución que proporcionan interfaces más simples e inmediatas.

Warning

Aunque los archivos son texto sin formato, no los edite directamente. Utilice siempre las herramientas proporcionadas con su distribución para este propósito.

### El archivo  `/etc/passwd`

`/etc/passwd`  es un archivo legible por todos (world-readable) que contiene una lista de usuarios en cada línea:

frank:x:1001:1001::/home/frank:/bin/bash

Cada línea constante de siete campos delimitados por dos puntos:

Username

El nombre utilizado cuando el usuario inicia sesión en el sistema.

Password

La contraseña cifrada (o una  `x`  si se usan contraseñas ocultas).

User ID (UID)

El número de ID asignado al usuario en el sistema.

Group ID (GID)

El número de grupo primario del usuario en el sistema.

GECOS

Un campo de comentario opcional, que se utiliza para agregar información adicional sobre el usuario (como el nombre completo). El campo puede contener múltiples entradas separadas por comas.

Home directory

La ruta absoluta del directorio de inicio del usuario.

Shell

La ruta absoluta del programa que se inicia automáticamente cuando el usuario inicia sesión en el sistema (generalmente un shell interactivo como  `/bin/bash`).

### El archivo  `/etc/group`

`/etc/group`  es un archivo legible en todos (world-readable) que contiene una lista de grupos, cada uno en una línea separada:

developer:x:1002:

Cada línea constante de cuatro campos delimitados por dos puntos:

Group Name

El nombre del grupo.

Group Password

La contraseña cifrada del grupo (o una  `x`  si se usan contraseñas ocultas).

Group ID (GID)

El número de identificación asignado al grupo en el sistema.

Member list

Una lista delimitada por comas de los usuarios que pertenecen al grupo, excepto aquellos para quienes este es el grupo primario.

### El archivo  `/etc/shadow`

`/etc/shadow`  es un archivo legible solo por usuarios root y usuarios con privilegios de root. Además contiene las contraseñas cifradas de los usuarios seperadas por una línea


```bash
frank:$6$i9gjM4Md4MuelZCd$7jJa8Cd2bbADFH4dwtfvTvJLOYCCCBf/.jYbK1IMYx7Wh4fErXcc2xQVU2N1gb97yIYaiqH.jjJammzof2Jfr/:18029:0:99999:7:::
```
Cada línea consta de nueve campos delimitados por dos puntos:

Username

El nombre utilizado cuando el usuario inicia sesión en el sistema.

Encrypted password

La contraseña cifrada del usuario (si el valor es  `!`, La cuenta está bloqueada).

Date of last password change

La fecha del último cambio de contraseña, como número de días desde 01/01/1970. Un valor de  `0`  significa que el usuario debe cambiar la contraseña en el siguiente acceso.

Minimum password age

El número mínimo de días después de un cambio de contraseña que debe pasar antes de que el usuario pueda cambiarla nuevamente.

Maximum password age

El número máximo de días que deben transcurrir antes de que se requiera un cambio de contraseña.

Password warning period

El número de días antes de que caduque la contraseña, durante los cuales se advierte al usuario que se debe cambiarla.

Password inactivity period

El número de días después de que caduca una contraseña durante el cual el usuario debe actualizarla. Después de este período, si el usuario no cambia la contraseña, la cuenta se deshabilitará.

Account expiration date

La fecha, como número de días desde el 01/01/1970 en que se deshabilitará la cuenta de usuario. Un campo vacío significa que la cuenta de usuario nunca caducará.

A reserved field

Un campo reservado para uso futuro.

### El archivo  `/etc/gshadow`

`/etc/gshadow`  es un archivo legible solo por root y por usuarios con privilegios de root que contiene contraseñas cifradas para grupos, cada uno en una línea separada:

```bash
developer:$6$7QUIhUX1WdO6$H7kOYgsboLkDseFHpk04lwAtweSUQHipoxIgo83QNDxYtYwgmZTCU0qSCuCkErmyR263rvHiLctZVDR7Ya9Ai1::
```

Cada línea constante de cuatro campos delimitados por dos puntos:

Group name

El nombre del grupo.

Encrypted password

La contraseña cifrada para el grupo (se usa cuando un usuario que no es miembro del grupo, desea unirse al grupo usando el comando  `newgrp`, si la contraseña comienza con  `!`. Nadie puede acceder al grupo con  `newgrp`).

Group administrators

Una lista delimitada por comas de los administradores del grupo (pueden cambiar la contraseña del grupo y pueden agregar o eliminar miembros del grupo con el comando  `gpasswd`).

Group members

Una lista delimitada por comas de los miembros del grupo.

Ahora que hemos visto dónde se almacena la información de usuarios y grupos, hablemos de las herramientas de línea de comandos más importantes para actualizar estos archivos.

### Agregar y eliminar cuentas de usuario

En Linux, puede agregar una nueva cuenta de usuario con el comando  `useradd`  y puede eliminar una cuenta de usuario con el comando  `userdel`.

Si desea crear una nueva cuenta de usuario llamada  `frank`  con una configuración predeterminada, puede ejecutar lo siguiente:

```bash
# useradd frank
```
Después de crear el nuevo usuario, puede establecer una contraseña usando  `passwd`:

```bash
# passwd frank
Changing password for user frank.
New UNIX password:
Retype new UNIX password:
passwd: all authentication tokens updated successfully.
```
Tip

Recuerde que siempre puede usar la utilidad  `grep`  para filtrar la contraseña y las bases de datos de grupo, mostrando solo la entrada que se refiere a un usuario o grupo específico. Para el ejemplo anterior puedes usar

`cat /etc/passwd | grep frank`

o

`grep frank /etc/passwd`

para ver información básica sobre la nueva cuenta  `frank`.


Las opciones más importantes que se aplican al comando  `useradd`  son:

`-c`

Crea una nueva cuenta de usuario con comentarios personalizados (por ejemplo, nombre completo).

`-d`

Crea una nueva cuenta de usuario con un directorio de inicio personalizado.

`-e`

Crea una nueva cuenta de usuario estableciendo una fecha específica en la que se deshabilitará.

`-f`

Crea una nueva cuenta de usuario estableciendo el número de días después de que caduque la contraseña durante los cuales el usuario debe actualizar la contraseña.

`-g`

Crea una nueva cuenta de usuario con un GID específico

`-G`

Crea una nueva cuenta de usuario agregándola a múltiples grupos secundarios.

`-m`

Crea una nueva cuenta de usuario con su directorio de inicio.

`-M`

Crea una nueva cuenta de usuario sin su directorio de inicio.

`-s`

Crea una nueva cuenta de usuario con un shell de inicio de sesión específico.

`-u`

Crea una nueva cuenta de usuario con un UID específico.

Una vez que se crea la nueva cuenta de usuario, puede usar los comandos  `id`  y  `groups`  para averiguar su UID, GID y los grupos a los que pertenece.Las opciones más importantes que se aplican al comando  `useradd`  son:

`-c`

Crea una nueva cuenta de usuario con comentarios personalizados (por ejemplo, nombre completo).

`-d`

Crea una nueva cuenta de usuario con un directorio de inicio personalizado.

`-e`

Crea una nueva cuenta de usuario estableciendo una fecha específica en la que se deshabilitará.

`-f`

Crea una nueva cuenta de usuario estableciendo el número de días después de que caduque la contraseña durante los cuales el usuario debe actualizar la contraseña.

`-g`

Crea una nueva cuenta de usuario con un GID específico

`-G`

Crea una nueva cuenta de usuario agregándola a múltiples grupos secundarios.

`-m`

Crea una nueva cuenta de usuario con su directorio de inicio.

`-M`

Crea una nueva cuenta de usuario sin su directorio de inicio.

`-s`

Crea una nueva cuenta de usuario con un shell de inicio de sesión específico.

`-u`

Crea una nueva cuenta de usuario con un UID específico.

Una vez que se crea la nueva cuenta de usuario, puede usar los comandos  `id`  y  `groups`  para averiguar su UID, GID y los grupos a los que pertenece.

```bash
# d frank
uid=1000(frank) gid=1000(frank) groups=1000(frank)
# groups frank
frank : frank
```

TIP
Recuerde verificar y eventualmente editar el archivo  `/etc/login.defs`, que define los parámetros de configuración que controlan la creación de usuarios y grupos. Por ejemplo, puede establecer el rango de UID y GID que se puede asignar a las nuevas cuentas de usuarios y grupos, así como especificar que no necesita usar la opción  `-m`  para crear el directorio de inicio del nuevo usuario y si el sistema debería crea automáticamente un nuevo grupo para cada nuevo usuario.

Si desea eliminar una cuenta de usuario, puede usar el comando `userdel`. En particular, este comando actualiza la información almacenada en las bases de datos de la cuenta, eliminando todas las entradas que se refieren al usuario especificado. La opción `-r` también elimina el directorio de inicio del usuario y todos sus contenidos, junto con la cola de correo del usuario. Otros archivos, ubicados en otro lugar, deben buscarse y eliminarse manualmente.

```bash
# userdel -r frank
```
Como antes, usted necesita autorización de root para eliminar cuentas de usuario.

### El directorio  `skel`

Cuando agrega una nueva cuenta de usuario, incluso al crear su directorio de inicio, el directorio de inicio recién creado se llena con archivos y carpetas que se copian del directorio de skel (por defecto  `/etc/skel`). La idea detrás de esto, es simple: un administrador del sistema quiere agregar nuevos usuarios que tengan los mismos archivos y directorios en su hogar. Por lo tanto, si desea personalizar los archivos y carpetas que se crean automáticamente en el directorio de inicio de las nuevas cuentas de usuario, debe agregar estos nuevos archivos y carpetas al directorio de skel.


Tip

Tenga en cuenta que los archivos de perfil que generalmente se encuentran en el directorio de skel son archivos ocultos. Por lo tanto, si desea enumerar todos los archivos y carpetas en el directorio skel que se copiarán en el directorio de inicio de los usuarios (recién creados), debe usar el comando  `ls -Al`.


### Agregar y eliminar grupos

En cuanto a la gestión de grupos, puede agregar o eliminar grupos utilizando los comandos  `groupadd`  y  `groupdel`.

Si desea crear un nuevo grupo llamado  `desarrollador`, puede ejecutar el siguiente comando como root:

```bash
# groupadd -g 1090 developer
```
La opción  `-g`  de este comando crea un grupo con un GID específico.

Si desea eliminar el grupo  `desarrollador`, puede ejecutar lo siguiente:

 **#groupdel developer**
 
Warning

Recuerde que cuando agrega una nueva cuenta de usuario, el grupo primario y los grupos secundarios a los que pertenece deben existir antes de iniciar el comando  `useradd`. Además, no puede eliminar un grupo si es el grupo principal de una cuenta de usuario.


### El comando  `passwd`

Este comando se usa principalmente para cambiar la contraseña de un usuario. Cualquier usuario puede cambiar su contraseña, pero solo el usuario root puede cambiar la contraseña de cualquier usuario.

Dependiendo de la opción  `passwd`  utilizada, puede controlar aspectos específicos del envejecimiento de la contraseña:

`-d`

Elimina la contraseña de una cuenta de usuario (estableciendo así una contraseña vacía y convirtiéndola en una cuenta sin contraseña).

`-e`

Fuerza a la cuenta de usuario a cambiar la contraseña.

`-l`

Bloquea la cuenta de usuario (la contraseña cifrada tiene el prefijo de un signo de exclamación).

`-u`

Desbloquea la cuenta de usuario (elimina el signo de exclamación).

`-S`

Muestra información sobre el estado de la contraseña para una cuenta específica.

Estas opciones están disponibles solo para root. Para ver la lista completa de opciones, consulte las páginas del manual.
