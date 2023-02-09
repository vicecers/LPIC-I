
## Ejercicios Guiados
1. Considere la siguiente lista:

$ **ls -lh**
```bash
total 60K
drwxr-xr-x  2   frank   frank   4.0K    Apr 1   2018    Desktop
drwxr-xr-x  2   frank   frank   4.0K    Apr 1   2018    Documents
drwxr-xr-x  2   frank   frank   4.0K    Apr 1   2018    Downloads
-rw-r--r--  1   frank   frank     21    Sep 7   12:59   emp_name
-rw-r--r--  1   frank   frank     20    Sep 7   13:03   emp_salary
-rw-r--r--  1   frank   frank   8.8K    Apr 1   2018    examples.desktop
-rw-r--r--  1   frank   frank     10    Sep 1   2018    file1
-rw-r--r--  1   frank   frank     10    Sep 1   2018    file2
drwxr-xr-x  2   frank   frank   4.0K    Apr 1   2018    Music
drwxr-xr-x  2   frank   frank   4.0K    Apr 1   2018    Pictures
drwxr-xr-x  2   frank   frank   4.0K    Apr 1   2018    Public
drwxr-xr-x  2   frank   frank   4.0K    Apr 1   2018    Templates
drwxr-xr-x  2   frank   frank   4.0K    Apr 1   2018    Videos
```
* ¿Qué representa el caracter `d` en la salida?
* ¿Cuál sería la diferencia en la salida si se usara `ls` sin argumentos?
2. Considere el siguiente comando:
```bash
$ cp /home/frank/emp_name /home/frank/backup
```
* ¿Qué pasaría con el archivo `emp_name` si este comando se ejecuta con éxito?
* Si `emp_name` era un directorio, ¿qué opción debería agregarse a `cp` para ejecutar el comando?
* Si  `cp`  ahora se cambia a  `mv`, ¿qué resultados espera?

3. Considere el listado:
``` bash
$ ls
file1.txt file2.txt file3.txt file4.txt
```
¿Qué  _wildcard_  ayudaría a eliminar todo el contenido de este directorio?

4. Según el listado anterior, ¿qué archivos se mostrarían con el siguiente comando?
```bash
$ls file*.txt
```
5. Complete el comando agregando los dígitos y caracteres apropiados entre corchetes que listarían todo el contenido anterior:
```bash
$ ls file[].txt
```
## Ejercicios Exploratorios
1.  En su directorio de inicio, cree los archivos llamados  `dog`  y  `cat`.
2. Aún en su directorio de inicio, cree el directorio llamado `animal`. Mueva `dog` y `cat` a `animal`.
3.  Vaya a la carpeta  `Documents`  que se encuentra en su directorio de inicio y dentro, cree el directorio  `backup`.
4. Copie  `animal`  y su contenido en  `backup`.
5. Cambie el nombre de `animal` en `backup` a `animal.bkup`.
6. El directorio `/home/lpi/bases de datos` contiene varios archivos incluyendo: `db-1.tar.gz`, `db-2.tar.gz` y `db-3.tar.gz`. *(cree el directorio y los archivos)* ¿Qué único comando puede usar para listar solo los archivos mencionados anteriormente?
7. Copie  `animal`  y su contenido en  `backup`.
```bash
$ ls
cne1222223.pdf cne12349.txt cne1234.pdf
```
Con el uso de un solo carácter globbing, ¿qué comando eliminaría solo los archivos pdf?
