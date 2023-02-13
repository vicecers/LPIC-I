## *Ejercicios guiados*

1. Considere la siguiente salida del comando `id`:
```bash
 $ id emma 
uid = 1000 ( emma ) gid = 1000 ( emma ) grupos = 1000 ( emma ) ,4 ( adm ) ,5 ( tty ) , 10 ( uucp ) , 20 ( dialout ) , 27 ( sudo ) .46 ( plugdev ) ```

¿En qué archivos se almacenan los siguientes atributos?
  

* UID y GID
Grupos
* Además, ¿en qué archivo se almacena la contraseña del usuario?

2. ¿Cuál de los siguientes tipos de criptografía se usa de manera predeterminada para almacenar contraseñas localmente en un sistema Linux?
-   Asimétrico -   Hash unidireccional -   Simétrico -   ROT13




3. Si una cuenta tiene un ID de usuario (UID) enumerada bajo 1000, ¿Qué tipo de cuenta es esta?

4.  ¿Cómo puede obtener una lista de los inicios de sesión activos en su sistema y también un recuento de ellos?

5. Usando el comando `grep`, obtuvimos el resultado siguiente con la información sobre el usuario `emma`
```bash 
$ grep emma /etc/passwdemma:x:1000:1000:Emma Smith,42 Douglas St,555.555.5555,:/home/emma:/bin/ksh 
```

Complete los espacios en blanco del gráfico con la información apropiada usando la salida del comando anterior.
||
|--|
|Username|
|Password|
|UID|
|Primary GID|
|GECOS|
|Home Directory
|Shell|
||

## *Ejercicios exploratorios*

1. Compare los resultados de  `last`  con  `w`  y  `who`. En comparación, ¿Qué detalles faltan a cada uno de los comandos ?

2. Intente emitir los siguientes comandos `who` y `w -his`.
   *   ¿Qué información se ha eliminado de la salida del comando  `w`  con las opciones “no header” (`-h`) y “short” (`-s`)?
   *   ¿Qué información se ha agregado en la salida del comando  `w`  con la opción “ip address” (`-i`)?
   
  3. ¿Cúal archivo es el que almacena el hash de contraseña unidireccional de una cuenta de usuario?
  
  4. ¿Qué archivo contiene la lista de grupos de los que es miembro una cuenta de usuario? ¿Qué lógica podría usarse para compilar una lista de grupos de los que es miembro una cuenta de usuario?

5.  Por defecto uno o más (1+) de los siguientes archivos no son legibles por usuarios normales y sin privilegios. ¿Cuáles son?
	 -   `/etc/group`
    
	-   `/etc/passwd`
    
	-   `/etc/shadow`
    
	-   `/etc/sudoers`
	  
6. ¿Cómo puede cambiar el shell de inicio de sesión del usuario actual al Korn Shell (`/usr/bin/ksh`) en modo no interactivo?

7. ¿Por qué el directorio de inicio del usuario `root` no está ubicado dentro del directorio `/home`?
