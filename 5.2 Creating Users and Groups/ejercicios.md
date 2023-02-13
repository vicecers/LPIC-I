## Ejercicios guiados

1. Para cada una de las siguientes entradas, indique el archivo al que hace referencia:

-   `developer:x:1010:frank,grace,dave`
    
-   `root:x:0:0:root:/root:/bin/bash`
    
-   `henry:$1$.AbCdEfGh123456789A1b2C3d4.:18015:20:90:5:30::`
    
-   `henry:x:1000:1000:User Henry:/home/henry:/bin/bash`
    
-   `staff:!:dave:carol,emma`

2. Observe el siguiente resultado para responder las siguientes siete preguntas:


**cat /etc/passwd | tail -3**
```bash
dave:x:1050:1050:User Dave:/home/dave:/bin/bash
carol:x:1051:1015:User Carol:/home/carol:/bin/sh
henry:x:1052:1005:User Henry:/home/henry:/bin/tcsh
```
***cat /etc/group | tail -3***
```bash
web_admin:x:1005:frank,emma
web_developer:x:1010:grace,kevin,christian
dave:x:1050:
```
**cat /etc/shadow | tail -3**
```bash
dave:$6$AbCdEfGh123456789A1b2C3D4e5F6G7h8i9:0:20:90:7:30::
carol:$6$q1w2e3r4t5y6u7i8AbcDeFgHiLmNoPqRsTu:18015:0:60:7:::
henry:!$6$123456789aBcDeFgHa1B2c3d4E5f6g7H8I9:18015:0:20:5:::
```
**cat /etc/gshadow | tail -3**
```bash
web_admin:!:frank:frank,emma
web_developer:!:kevin:grace,kevin,christian
dave:!::
```

-   -   ¿Cuál es el ID de usuario (UID) y el ID de grupo (GID) de  `carol`?
        
    
-   ¿Qué shell está configurado para  `dave`  y  `henry`?
    
-   ¿Cuál es el nombre del grupo principal de  `henry`?
    
-   ¿Cuáles son los miembros del grupo  `web_developer`? ¿Cuáles de estos son administradores de grupo?
    
-   ¿Qué usuario no puede iniciar sesión en el sistema?
    
-   ¿Qué usuario debe cambiar la contraseña la próxima vez que inicie sesión en el sistema?
    
-   ¿Cuántos días deben pasar antes de que se requiera un cambio de contraseña para  `carol`?

## Ejercicios exploratorios

1.  Trabajando como root, ejecute el comando  `useradd -m dave`  para agregar una nueva cuenta de usuario. ¿Qué operaciones realiza este comando? Suponga que  `CREATE_HOME`  y  `USERGROUPS_ENAB`  en  `/etc/login.defs`  están configuradas en  `yes`.
    
2.  Ahora que ha creado la cuenta  `dave`, ¿puede este usuario iniciar sesión en el sistema?
    
3.  Identifique el ID de usuario (UID) y el ID de grupo (GID) de  `dave`  y todos los miembros del grupo  `dave`.
    
4.  Cree los grupos  `sys_admin`,  `web_admin`  y  `db_admin`  e identifique sus ID de grupo (GID).
    
    Agregue una nueva cuenta de usuario llamada `carol` con UID 1035 y configure `sys_admin` como su grupo principal y `web_admin` y `db_admin` como sus grupos secundarios.
    
5.  Elimine las cuentas de usuario  `dave`  y  `carol`  y los grupos  `sys_admin`,  `web_admin`  y  `db_admin`  que haya creado previamente.
    
6.  Ejecute el comando  `ls -l /etc/passwd /etc/group /etc/shadow /etc/gshadow`  y describa el resultado que le da en términos de permisos de archivo. ¿Cuál de estos cuatro archivos está sombreado (shadowed) por razones de seguridad? Suponga que su sistema usa contraseñas ocultas.
    
7.  Ejecute el comando  `ls -l /usr/bin/passwd`. ¿Qué bit especial se establece y cuál es su significado?	
