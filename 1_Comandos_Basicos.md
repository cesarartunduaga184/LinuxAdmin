# Comandos Básicos de la Terminal

## Qué es y por qué usar la terminal
- La **terminal** es una interfaz de línea de comandos (**CLI**) que permite a los usuarios interactuar con el sistema operativo utilizando comandos de texto. Aunque puede parecer intimidante al principio, la terminal ofrece varias ventajas:
- **Eficiencia:** Los comandos pueden ser más rápidos que las operaciones gráficas.
- **Control Completo:** Permite un control más granular del sistema.
- **Automatización:** Facilita la creación de scripts para automatizar tareas repetitivas.

## Comandos básicos
A continuación se muestran algunos de los comandos esenciales en Ubuntu, incluyendo los parámetros más usados:

#### `ls`: Listar el contenido de un archivo o directorio.
  
```bash
ls -l  # Lista archivos y carpetas de manera detallada
ls -a  # Lista todos los archivos, incluyendo archivos ocultos (aquellos que comienzan con un punto).
```

#### `cd`: Cambiar de directorio.

```bash
cd ..  # Subir un nivel.
cd -  # Volver al directorio anterior.
cd /home/usuario  # Moverse al directorio del usuario
```

#### `pwd`: Muestra el directorio de trabajo actual.

```bash
pwd
```

#### `mkdir`: Crea un nuevo directorio.

```bash
mkdir nuevo_directorio
```

#### `rm`: Elimina archivos o directorios.

```bash
rm archivo_a_eliminar
rm -rf directorio_a_eliminar
```
- `-r`: Elimina recursivamente, se usa para eliminar directorios no vacíos.
- `-f`: Fuerza la eliminación.

#### `cp`: Copia archivos o directorios.

```bash
cp -rv origen destino
```
- `-r`: Copia recursivamente, útil cuando se realiza copia de directorios.
- `-v`: Muestra un detalle del proceso.

#### `mv`: Mueve o renombra archivos o directorios.

```bash
mv archivo_origen archivo_destino
mv nombre_archivo nuevo_nombre
```

#### `touch`: Crea un archivo vacío.

```bash
touch nuevo_archivo.txt
```

#### `cat`: Muestra el contenido de un archivo.

```bash
cat -n archivo.txt
```
- `-n`: Numera las líneas.

#### `less`: Comando para visualizar el contenido de un archivo de manera paginada. Permite avanzar hacia atrás y hacia adelante.

```bash
less archivo.txt
```

#### `more`: Permite visualizar el contenido de un archivo de manera paginada, pero solo permite avanzar hacia adelante.

```bash
more archivo.txt
more -d archivo.txt
```
- `-d`: Muestra mensajes de ayuda.

#### `echo`: Muestra un mensaje en la terminal o redirige texto a un archivo.

```bash
echo "Hola, mundo"  # Muestra el mensaje "Hola. mundo" en la terminar
echo "Hola, mundo" > archivo.txt  # Envía el mensaje a archivo.txt 
```

#### `sudo`: Ejecuta un comando con privilegios de superusuario.

```bash
sudo apt install vim  # Comando para instalar el editor de texto vim
```

#### `apt`: Gestiona paquetes en sistemas basados en Debian.

```bash
sudo apt update  # Actualiza la lista de paquetes
sudo apt upgrade  # Actualiza los paquetes instalados
sudo apt install nombre_paquete  # Instala un nuevo paquete
```

#### `df`: Muestra el uso del disco.

```bash
df -h
```
- `-h` Muestra la salida en formato legible para humanos.

#### `du`: Muestra el uso del disco y directorios.

```bash
du -sh directorio
```
- `-h`: Formato legible para humanos.
- `-s`: Muestra un resumen.

#### `chown`: Cambia el propietario de un archivo o directorio.

```bash
chown usuario directorio  # usuario es el nuevo propietario de directorio
```

#### `ps`: Muestra los procesos en ejecución.

```bash
ps
```

#### `kill`: Envía una señal a un proceso.

```bash
kill -9 pid
```
- `-9`: Mata el proceso inmediatamente.

#### `top`: Muestra los procesos en ejecución y el uso de recursos en tiempo real.

```bash
top
```

#### `htop`: Una versión mejorada de `top`, requiere instalación.

```bash
sudo apt install htop
htop
```

#### `grep`: Busca patrones en archivos.

```bash
grep -i "patrón" archivo.txt
grep -r "patrón" directorio/
```
- `-i`: No distingue entre mayúsculas y minúsculas.
- `-r`: Busca recursivamente dentro de un directorio.

#### `find`: Busca archivos y directorios.

```bash
find /ruta -name "archivo.txt"
find /ruta -type d
```
- `-name`: Busca por nombre.
- `-type`: Filtra por tipo.


#### `ssh`: Se conecta a un servidor remoto mediante el protocolo SSH.

```bash
ssh usuario@servidor -p puerto
```
- `-p`: Especifica el puerto, por defecto se conecta al 22.

#### `scp`: Copia archivos entre hosts mediante SSH.

```bash
scp archivo.txt usuario@servidor:/ruta/destino
scp -r directorio/ usuario@servidor:/ruta/destino
```
- `-r`: Copia recursivamente, en el caso de copiar un directorio.

#### `wget`: Descarga archivos de la web.

```bash
wget -c http://url/archivo.zip
```
- `-c`: Continúa una descarga interrumpida.

#### `curl`: Transfiere datos desde un servidor.

```bash
curl -O http://url/archivo.zip
```
- `-O`: Guarda el archivo con el nombre original.

#### `tar`: Archiva, comprime y descomprime archivos.

```bash
tar -cvf archivo.tar directorio/
tar -xvf archivo.tar
tar -czvf archivo.tar.gz directorio/
tar -xzvf archivo.tar.gz
```
- `-c`: Crea un archivo tar.
- `-x`: Extrae un archivo tar.
- `-z`: Comprime con gzip.
- `-v`: Muestra un detalle del proceso.

#### `zip`/`unzip`: Comprime y descomprime archivos zip.

```bash
zip -r archivo.zip directorio/
unzip archivo.zip
```
- `-r`: Comprime recursivamente.

#### `alias`: Crea un alias para un comando.

```bash
alias ll='ls -lah'
```

#### `unalias`: Elimina un alias previamente definido.

```bash
unalias ll
```

#### `uname`: Muestra información del sistema.

```bash
uname -a
```
- `-a`: Muestra toda la información disponible.

#### `free`: Muestra el uso de la memoria (RAM y Swap).

```bash
free -h
```
- `-h`: Formato legible para humanos.

#### `history`: Muestra el historial de comandos ejecutados.

```bash
history
```

#### `whoami`: Muestra el nombre del usuario actual.

```bash
whoami
```

#### `hostname`: Muestra o cambia el nombre del host.

```bash
hostname
sudo hostname nuevo_nombre
```

#### `ifconfig`: Muestra o configura las interfaces de red.

```bash
ifconfig
sudo ifconfig eth0 up
```

#### `netstat`: Muestra conexiones de red, tablas de enrutamiento, estadísticas de interfaz, etc.

```bash
netstat -tuln
```
- `-tuln`: Muestra puertos abiertos y servicios.

#### `ping`: Verifica la conectividad de red con otro host.

```bash
ping google.com
```

#### `traceroute`. Muestra la ruta que toman los paquetes a un host.

```bash
traceroute google.com
```

#### `nslookup`: Consulta información DNS.

```bash
nslookup google.com
```

#### `dig`: Consulta información DNS avanzada.

```bash
dig google.com
```

#### `iptables`: Configura reglas del firewall.

```bash
sudo iptables -L
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
sudo iptables -D INPUT -p tcp --dport 22 -j ACCEPT
```
- `-L`: Lista reglas.
- `-A`: Añade regla.
- `-D`: Elimina regla.

#### `service`: Administra servicios del sistema.

```bash
sudo service apache2 start
sudo service apache2 stop
sudo service apache2 restart
```
- `start`: Inicia un servicio.
- `stop`: Detiene un servicio.
- `restart`: Reinicia un servicio.
- **Esta herramienta es auntigua y se recomienda usar `systemctl` en su lugar.**

#### `systemctl`: Administra servicios y la inicialización del sistema.

```bash
sudo systemctl start apache2
sudo systemctl stop apache2
sudo systemctl restart apache2
sudo systemctl status apache2
```
- `start`: Inicia un servicio.
- `stop`: Detiene un servicio.
- `restart`: Reinicia un servicio.
- `status`: Muestra el estado de un servicio.

#### `journalctl`: Muestra los logs del sistema.

```bash
journalctl -xe
```
- `-xe`: Modo detallado de errores.

#### `crontab`: Edita tareas programadas del sistema.

```bash
crontab -e
crontab -l
```
- `-e`: Edita crontab.
- `-l`: Lista crontab.

#### `exit`: Sale de la terminal actual.

```bash
exit
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

## Fuentes para consulta

### Manuales de Linux

Los manuales de Linux son una excelente fuente de información sobre comandos específicos. Se acceder a estos manuales directamente desde la terminal utilizando el comando  `man` seguido del nombre del comando que quieres consultar. Por ejemplo:

```bash
man ls
```
    
### Documentación oficial de Ubuntu

La documentación oficial de Ubuntu incluye una guía detallada sobre los comandos de terminal. Toda la documentación está disponible [aquí](https://help.ubuntu.com/community/UsingTheTerminal).