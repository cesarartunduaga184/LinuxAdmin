# Permisos de Archivos y Directorios

Los permisos en Linux controlan el acceso a los archivos y directorios. Cada archivo y directorio tiene asociado un conjunto de permisos que determinan quién puede **leer**, **escribir** o **ejecutar** el archivo o directorio. Estos permisos pueden ser otorgados a tres tipos de categorías: **propietario**, **grupo** y **otros**.

## **Conceptos de Propietario, Grupo y Otros**
- **Propietario (Owner):** Se refiere al usuario que creó el archivo o directorio. Tiene control total sobre el archivo por defecto.
- **Grupo (Group):** Se refiere a un conjunto de usuarios que comparten permisos sobre el archivo o directorio.
- **Otros (Others):** Se refiere a todos los demás usuarios que no son ni el propietario ni miembros del grupo.

## Cada usuario puede tener uno o más de los siguientes permisos
- **`r` (read):** Permiso de lectura, permite ver el contenido del archivo o listar el contenido del directorio.
- **`w` (write):** Permiso de escritura, permite modificar el contenido del archivo o añadir/eliminar archivos en el directorio.
- **`x` (execute):** Permiso de ejecución, permite ejecutar el archivo (si es un script o un programa), o acceder al contenido si es un directorio.

## Representación de Permisos
- Los permisos se representan con un conjuto de caracteres, por ejemplo: `-rwxr-xr--`. Este conjunto de caracteres se divide en cuatro partes:
- **Tipo de archivo:** El primer caracter indica el tipo de archivo. Los valores más comunes, son:
  - `-`: archivo regular
  - `d`: directorio
  - `l`: enlace simbólico
- **Permisos del propietario:** Los siguientes tres caracteres representan los permisos del propietario, `rwx` en este caso
- **Permisos del grupo:** Los tres caracteres siguientes representan los permisos del grupo, `r-x` en este caso
- **Permisos de otros:** Los últimos tres caracteres representan los permisos de otros usuarios, `r--` en este caso.

## Ejemplo de salida del comando `ls -l`:

```bash
-rw-r--r-- 1 usuario grupo 1234 jun 1 12:34 archivo.txt
```
- Los permisos `-rw-r--r--`, lo podemos desglosar de la siguiente manera
  - `-`: Archivo regular
  - `rw-`: Permisos de lectura y escritura para el propietario
  - `r--`: Lectura para el grupo
  - `r--`: Sólo lectura para otros (no pueden escribir ni ejecutar).

## Tipos de notaciones de permisos

### Notación simbólica
  - `r`: lectura
  - `w`: escritura
  - `x`: ejecusión
  - `+`: agregar permiso
  - `-`: quitar permiso
  - `=`: asignar permiso
       
- **Ejemplos:**
  ```bash
  chmod u+x archivo    # Agrega permiso de ejecución al propietario
  chmod g-w archivo    # Quita permiso de escritura al grupo
  chmod o=r archivo    # Asigna permiso de lectura a otros
  chmod a+rw archivo   # Agrega permisos de lectura y escritura a todos
  ```

### Notación octal
  - `4`: lectura
  - `2`: escritura
  - `1`: ejecución
  - `0`: sin permiso

Los permisos se combinan sumando estos valores. Por ejemplo `7`(lectura, ecritura y ejecución), es la suma de: `4` (lectura) + `2`(escritura) + `1`(ejecución).

Podes encontrar una calculadora de permisos [aqui](https://chmod-calculator.com/).

- **Ejemplos:**
  ```bash
  chmod 755 archivo  # Propietario: 7 (rwx), Grupo: 5 (rx), Otros: 5 (rx)
  chmod 644 archivo  # Propietario: 6 (rw), Grupo: 4 (r), Otros: 4 (r)
  chmod 600 archivo  # Propietario: 6 (rw), Grupo: 0 (sin permisos), Otros: 0 (sin permisos)
  ```


## Uso de los Comandos `chmod`, `chown` y `chgrp`

- **`chmod`:** Se utiliza para cambia los permisos de un archivo o directorio. Este comando se puede usar tanto con notación simbólica como octal.
  - **Uso básico:**
    ```bash
    chmod [permisos] archivo
    ```
  - **Ejemplo:**
    - Cambiar los permisos del archivo a `script.sh`:
    ```bash
    ls -l script.sh                 # Verificar los permisos actuales
    -rw-rw-r--  1 usuario grupo
    chmod 754 script.sh             # Cambio de permisos
    ls -l script.sh                 # Verificar los nuevos permisos
    -rwxr-xr--  1 usuario grupo
    ```

- **`chown`:** Cambia el propietario de un archivo o directorio.
  - **Uso básico:**
    ```bash
    chown usuario archivo
    ```
  - **Ejemplo:**
    - Cambiar el propietario de un archivo a `juan`:
    ```bash
    chown juan script.sh
    ```

- **`chgrp`:** Cambia el grupo de un archivo o directorio.
  - **Uso básico:**
    ```bash
    chgrp grupo archivo
    ```
  - **Ejemplo:**
    - Cambiar el grupo de un archivo a `desarrollo`:
    ```bash
    chgrp desarrollo test.py
    ```