# Instalación de Programas en Ubuntu

La mayoría de las distribuciones de Linux, ofrecen múltiples formas de instalar software, desde el uso de gestores de paquetes y tiendas de aplicaciones, hasta la compilación de software desde el código fuente. A continuación, se detallan las diferentes maneras de instalar programas en Ubuntu, con ejemplos prácticos para cada método.

## Uso de APT (Advanced Package Tool)

**APT** es el gestor de paquetes predeterminado en Ubuntu. Utiliza repositorios de software para descargar e instalar paquetes.

### Parámetros más utilizados:
- `list`: lista los paquetes según los nombres
- `search` busca en las descripciones de los paquetes
- `show` muestra detalles del paquete
- `install` instala paquetes
- `reinstall` reinstalar paquetes
- `remove` elimina paquetes
- `autoremove` Elimina automáticamente todos los paquetes sin utilizar
- `update` actualiza la lista de paquetes disponibles
- `upgrade` actualiza el sistema instalando/actualizando paquetes
- `full-upgrade` actualiza el sistema eliminando/instalando/actualizando paquetes
- `edit-sources` edita el fichero de información de fuentes
- `satisfy` satisfacer cadenas de dependencias

## Repositorios

Los repositorios son servidores que almacenan colecciones de software. En Ubuntu, los repositorios contienen paquetes de software que pueden ser descargados e instalados en el sistema usando herramientas de gestión de paquetes, por ejemplo **APT**. Los repositorios aseguran que el software esté actualizado, sea compatible con el sistema operativo y sea seguro.

## Actualizar los repositorios
Antes de instalar cualquier paquete, es una buena práctica actualizar la lista de paquetes disponibles en los repositorios. Para esto, ejecutamos el siguiente comando:
```bash
sudo apt update
```

## Paquetes

Los paquetes son archivos que contienen software y toda la información necesaria para su instalación y configuración. Un paquete incluye los archivos binarios del programa, las dependencias requeridas, scripts de instalación y metadatos. Los paquetes facilitan la instalación y actualización de software, ya que permiten a los gestores de paquetes manejar automáticamente las dependencias y las actualizaciones del sistema.

## Instalar un paquete

Para instalar un paquete, se utiliza el siguiente comando:
```bash
sudo apt install nombre_del_paquete
```
### Ejemplo:
Para instalar el `firefox`, ejecutamos el siguiente comando:
```bash
sudo apt install firefox
```

## Buscar paquetes

Para buscar un paquete específico en los repositorios, se utiliza el comando.
```bash
apt search nombre_del_paquete
```
### Ejemplo:

Para buscar paquetes relacionados con `python`:
```bash
apt search python
```

## Eliminar un paquete

Para eliminar un paquete, se utiliza el comando:
```bash
sudo apt remove nombre_del_paquete
```

### Ejemplo:

Para eliminar `firefox`, ejecutamos:
```bash
sudo apt remove firefox
```

## Limpiar paquetes no necesarios

Después de eliminar paquetes, se pueden quedar archivos residuales que no son necesarios. Para limpiar estos archivos, se utiliza:
```bash
sudo apt autoremove
```

## Actualizar Todos los Paquetes 

Para actualizar todos los paquetes instalados a sus versiones más recientes, ejecutamos el comando:
```bash
sudo apt upgrade
```
- Este comando instala las versiones más recientes de todos los paquetes instalados, respetando las dependencias.

## Uso de Snap

**Snap** es un sistema de empaquetado y despliegue de software desarrollado por **Canonical** para Ubuntu y otras distribuciones de Linux. Los paquetes **Snap** incluyen todas las dependencias necesarias para ejecutar el software, lo que simplifica la instalación.

## Instalar un paquete Snap

Para instalar un paquete `Snap`, se utiliza el siguiente comando.
```bash
sudo snap install nombre_del_paquete
```

### Ejemplo:

Para instalar el editor de texto Visual Studio Code, ejecutamos:
```bash
sudo snap install code --classic
```
- La opción `--classic` permite que el paquete tenga acceso a los recursos del sistema de forma similar a las aplicaciones tradicionales.

## Buscar paquetes Snap

Para buscar un paquete Snap, se utiliza:
```bash
snap find nombre_del_paquete
```

### Ejemplo:

Para buscar paquetes relacionados con `spotify`:
```bash
snap find spotify
```

## Eliminar un paquete Snap

Para eliminar un paquete Snap, se utiliza:
```bash
sudo snap remove nombre_del_paquete
```

### Ejemplo:

Para eliminar Visual Studio Code:
```bash
sudo snap remove code
```

## Uso de Flatpak

Flatpak es otro sistema de empaquetado que permite instalar aplicaciones en varias distribuciones de Linux, asegurando que las aplicaciones funcionen de manera consistente.

## Instalar Flatpak

Primero, es necesario instalar `flatpak`. 
```bash
sudo apt install flatpak
```

## Añadir un repositorio Flatpak

Para poder instalar aplicaciones, es necesario añadir un repositorio. **Flathub** es el repositorio más común. Para esto, ejecutamos el siguiente comando
```bash
sudo flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

### Instalar un paquete Flatpak

Para instalar un paquete `flatpak`, se utiliza el comando:
```bash
flatpak install flathub nombre_del_paquete
```
### Ejemplo:

Para instalar Spotify:
```bash
flatpak install flathub com.spotify.Client
```

## Ejecutar un paquete Flatpak

Para ejecutar una aplicación Flatpak instalada, se utiliza:
```bash
flatpak run nombre_del_paquete
```

### Ejemplo:

Para ejecutar Spotify:
```bash
flatpak run com.spotify.Client
```

## Eliminar un paquete Flatpak

Para eliminar un paquete Flatpak, se utiliza `flatpak uninstall`.
```bash
flatpak uninstall nombre_del_paquete
```

### Ejemplo:
Para eliminar Spotify:
```bash
flatpak uninstall com.spotify.Client
```

## Uso de la Tienda de Software de Ubuntu

La Tienda de Software de Ubuntu es una interfaz gráfica que permite a los usuarios buscar, instalar y gestionar software fácilmente.

## Buscar e instalar software

- Abrir la Tienda de Software de Ubuntu desde el menú de **Aplicaciones**.
-  Utilizar la barra de búsqueda para encontrar el software deseado.
- Seleccionar el software y hacer clic en **Instalar**.

## Gestionar software instalado

- Abrir la **Tienda de Software** de Ubuntu.
- Ir a la sección de **Instalado** para ver y gestionar el software instalado.
- Para eliminar un programa, seleccionar el programa y hacer clic en **Eliminar**.

## Instalación de programas desde un archivo `.deb`

Los archivos `.deb` son paquetes Debian que pueden instalarse directamente.

## Descargar un archivo `.deb`

Supongamos que deseamos instalar `Google Chrome`. Primero, debemos descargar el archivo `.deb` desde el sitio oficial:

- https://www.google.com/intl/es_es/chrome/browser-tools/

## Instalar el archivo `.deb`

Para instalar el archivo `.deb`, utiliza `dpkg`:
```bash
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

### Si hay dependencias faltantes, debemos ejecutar:
```bash
sudo apt --fix-broken install
```

## En resumen

### APT (Advanced Package Tool)
- **Definición:** Es un gestor de paquetes tradicional utilizado en Debian y Ubuntu.
- **Funcionamiento:** Instala software desde repositorios que contienen paquetes `.deb`.
- **Dependencias:** Gestiona dependencias automáticamente, instalando las necesarias desde los repositorios.
- **Integración:** Muy integrado con el sistema, los paquetes instalados son específicos de la distribución.
- **Ejemplo:**
  ```bash
  sudo apt install firefox
  ```

### Snap
- **Definición:** Sistema de empaquetado desarrollado por Canonical.
- **Funcionamiento:** Instala software en forma de paquetes autónomos llamados "snaps".
- **Dependencias:** Incluye todas las dependencias necesarias dentro del paquete, lo que lo hace más grande.
- **Integración:** Funciona en múltiples distribuciones Linux. Los snaps están aislados del sistema base mediante **sandboxing**.
- **Ejemplo:**
  ```bash
  sudo snap install code --classic
  ```

### Flatpak
- **Definición:** Sistema de empaquetado que permite instalar aplicaciones en varias distribuciones Linux.
- **Funcionamiento:** Instala software en forma de paquetes autónomos llamados `flatpaks`.
- **Dependencias:** Incluye las dependencias en el paquete, asegurando compatibilidad entre distribuciones.
- **Integración:** También utiliza **sandboxing** para aislar aplicaciones del sistema base. Requiere añadir repositorios (ej. **Flathub**).
- **Ejemplo:**
  ```bash
  flatpak install flathub com.spotify.Client
  ```

#### Mantener el sistema actualizado es esencial para garantizar la seguridad y estabilidad del entorno Linux. Los repositorios proporcionan acceso a una amplia gama de software, mientras que las actualizaciones protegen contra vulnerabilidades y aseguran que el software funcione de manera óptima.