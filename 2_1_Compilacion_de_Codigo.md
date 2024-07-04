# Compilación e Instalación desde el Código Fuente

Compilar e instalar software desde el código fuente permite tener control total sobre el proceso de instalación, incluyendo la optimización y personalización del software. Este método es útil cuando el software no está disponible en formato binario para tu distribución o cuando se desea aplicar parches específicos.

## Pasos para la compilación e instalación desde el código fuente

### 1. Instalar las herramientas de compilación

Antes de compilar, se debe instalar las herramientas de desarrollo necesarias, como `build-essential`, que incluye compiladores y bibliotecas básicas:

```sh
sudo apt-get update
sudo apt-get install build-essential
```
- Puede ser necesario instalar bibliotecas adicionales. Es importante leer la documenta brindada por la fuente.

### 2. Descargar el código fuente

El código fuente generalmente se distribuye en archivos comprimidos (`.tar.gz`, `.tar.bz2`), que deben descargarse desde el sitio del proyecto:

```sh
wget https://example.com/software.tar.gz
```
- `wget`es una herramienta de línea de comandos utilizada para descargar archivos de sitios web.

### 3. Descomprimir el código fuente

Una vez descargado el archivo comprimido, se debe descomprimir para poder acceder al código fuente. Para esto, hacemos uso de la herramienta `tar`. Luego debemos ubicarnos en la carpetada que fue descomprimida:

```sh
tar -xf software.tar.gz
cd software
```

### 4. Configuración del entorno de compilación

La mayoría de los proyectos de software incluyen un script `configure`, el cual se encarga de configurar el entorno de compilación para cada sistema. Ejecutamos el script:

```sh
./configure
```

- Además, este script verifica las dependencias y las bibliotecas necesarias, creando archivos de configuración para el proceso de compilación.

### 5. Compilación del software

Para compilar el software, se hace uso del comando `make`. Este comando utiliza los archivos de configuración generados por el script `configure` para compilar el código fuente:

```sh
make
```

### 6. Instalación del software

Después de la compilación, se instala el software en el sistema:

```sh
sudo make install
```
- Este comando copia los archivos compilados en los directorios correspondientes del sistema (generalmente `/usr/local`).

## Ejemplo Práctico

Para este ejemplo compilaremos e instalaremos el editor de texto `leafpad` desde el código fuente.

### 1. Instalación de herramientas de compilación

Antes de compilar, debemos asegurarnos de que las herramientas de desarrollo necesarias están instaladas en el sistema:

```sh
sudo apt update
sudo apt install build-essential libgtk2.0-dev
```
- `build-essential` instala el compilador **GCC** y las herramientas de desarrollo necesarias.
- `libgtk2.0-dev`es una biblioteca de desarrollo necesaria para la interfaz gráfica de `leafpad`.

### 2. Descargar del código fuente

Descargamos el archivo comprimido con el código fuente de `leafpad`:

```sh
wget https://download.savannah.gnu.org/releases/leafpad/leafpad-0.7.6.tar.gz
```
- Este comando descarga el archivo `leafpad-0.7.6.tar.gz` en el directorio actual.

### 3. Descomprimir el código fuente

Descomprimimos el archivo descargado (para acceder al código fuente), y luego nos movemos al directorio creado:

```sh
tar -xf leafpad-0.7.6.tar.gz
cd leafpad-0.7.6
```

### 4. Configurar el entorno de compilación

Ejecutamos script `configure`:

```sh
./configure
```
- Este script verifica las dependencias, las bibliotecas necesarias y configura el entorno de compilación. Si faltan dependencias, el script nos lo reportará y podremos instalarlas.

### 5. Compilación del software

Hacemos uso de `make` para compilar el software. Este comando utiliza los archivos de configuración generados por `configure` para compilar el código fuente:

```sh
make
```
- `make` compila el código fuente y genera los archivos binarios necesarios para la instalación.

### 6. Instalación del software

Después de compilar el software, lo instalamos en el sistema. Para esto, ejecutamos:

```sh
sudo make install
```
- Este comando copia los archivos compilados en los directorios correspondientes del sistema (generalmente `/usr/local`), haciendo que `leafpad` esté disponible para su uso.

#### 7. Verificación de la Instalación
Para verificar que `leafpad` se ha instalado correctamente, ejecutamos el siguiente comando:

```sh
leafpad --version
```
- Este comando mostrará la versión de `leafpad` instalada, confirmando que el proceso de compilación e instalación fue exitoso.

## Notas

### Dependencias Adicionales
En algunos casos, puede ser necesario instalar dependencias adicionales antes de ejecutar el script `configure`. Estas dependencias se pueden instalar utilizando `apt` o cualquier otra herramienta de gestión de paquetes.

### Documentación
Es muy importante leer la documentación proporcionada con el código fuente, para obtener información específica sobre las opciones de configuración y las dependencias, ya que este proceso puede variar según el software a instalar y sus requisitos de compilación. Para leer la documentación, ejecutamos:
```sh
./configure --help
```

### Desinstalación
Si en algún momento necesitamos desinstalar `leafpad` (o cualquier otro software que hayamos instalado con este método), debemos navegar al directorio del código fuente y ejecutar:

```sh
sudo make uninstall
```