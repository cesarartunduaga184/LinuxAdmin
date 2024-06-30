# Comandos Básicos de la Terminal

## Qué es y por qué usar la terminal
- La **terminal** es una interfaz de línea de comandos (**CLI**) que permite a los usuarios interactuar con el sistema operativo utilizando comandos de texto. Aunque puede parecer intimidante al principio, la terminal ofrece varias ventajas:
- **Eficiencia:** Los comandos pueden ser más rápidos que las operaciones gráficas.
- **Control Completo:** Permite un control más granular del sistema.
- **Automatización:** Facilita la creación de scripts para automatizar tareas repetitivas.

## Comandos básicos
A continuación se muestran algunos de los comandos esenciales que todo usuario debe conocer:

- **`ls`:** Lista el contenido de un archivo o directorio.
  ```bash
  ls -l  # Lista archivos y carpetas de manera detallada
  ls -a  # Lista todos los archivos, incluyendo archivos ocultos (aquellos que comienzan con un punto).
  ```

- **`cd`:** Cambia de directorio.
  ```bash
  cd /ruta/al/directorio  #Cambia al directorio especificado.
  cd ..  # Sube un nivel en la jerarquía de directorios.
  cd ~   # Cambia al directorio home del usuario.
  ```
  
- **`pwd`:** Muestra la ruta completa del directorio actual.
  ```bash
  pwd
  ```

- **`cp`:** Copia archivos o directorios.
  ```bash
  cp archivo /directorio/destino  # Copia un archivo a la ubicación especificada.
  cp -r directorio /directorio/destino  # Copia un directorio y su contenido de manera recursiva.
  
- **`mv`:** Mueve o renombra archivos o directorios.
  ```bash
  mv archivo /directorio/destino  # Mueve un archivo a la ubicación especificada.
  mv antiguo_nombre nuevo_nombre  # Cambia el nombre de un archivo o directorio.
  ```
  
- **`rm`:** Elimina archivos o directorios.
  ```bash
  rm archivo  # Elimina el archivo especificado.
  rm -r directorio  # Elimina un directorio y su contenido de manera recursiva
  ```
  
- **`mkdir`:** Crea un nuevo directorio.
  ```bash
  mkdir nuevo_directorio
  ```

## Visualización de contenido

- **`cat`:** Muestra el contenido de un archivo.
  ```bash
  cat archivo
  ```

- **`less` y `more`:** Muestra el contenido de un archivo página por página.
  ```bash
  less archivo
  more archivo
  ```

## Búsqueda de archivos

- **`find`:** Busca archivos y directorios.
  ```bash
  find /ruta -name "nombre_del_archivo"  # Busca un archivo por su nombre en la /ruta especificada.
  find /ruta -type d -name "nombre_del_directorio"  # Busca un directorio (-d) por su nombre en la /ruta especificada.
  ```
  
- **`grep`:** Busca texto dentro de archivos.
  ```bash
  grep "texto_a_buscar" archivo  # Busca el texto especificado dentro del archivo.
  grep -r "texto_a_buscar" directorio  # Busca el texto especificado dentro de los archivos del directorio.
  ```
  
## Ejemplos Prácticos

### Navegación y gestión de archivos:
   ```bash
   cd ~/Documentos  # Navegar al directorio Documentos

   ls -l  # Listar con detalles todos los archivos y carpetas

   mkdir proyectos  # Crear una nueva carpeta llamada 'proyectos'
 
   cd proyectos  # Moverse al directorio 'proyectos'
 
   cat hola.txt  # Mostrar el contenido del archivo hola.txt
 
   cp hola.txt hola_copia.txt  # Hacer una copia de un archivo
 
   mv hola_copia.txt /directorio/destino  # Mover el archivo copiado a otra ubicación
   ```

### Búsqueda y visualización de contenido:
   ```bash
   find . -name "hola.txt"  # Buscar el archivo llamado hola.txt en el directorio actual (.)
 
   grep "contraseña" hola.txt  # Buscar una palabra dentro de un archivo
 
   less hola.txt  # Mostrar el contenido de un archivo de forma paginada
   ```

## Fuentes para consultar cómo usar los comandos de la terminal de Linux:

- **Manuales de Linux**
  - Los manuales de Linux son una excelente fuente de información sobre comandos específicos. Se acceder a estos manuales directamente desde la terminal utilizando el comando  `man` seguido del nombre del comando que quieres consultar. Por ejemplo:
    ```bash
    man ls
    ```
    
- **Documentación oficial de Ubuntu**
  - La documentación oficial de Ubuntu incluye una guía detallada sobre los comandos de terminal. Toda la documentación está disponible [aquí](https://help.ubuntu.com/community/UsingTheTerminal).