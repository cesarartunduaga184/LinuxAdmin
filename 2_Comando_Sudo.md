# Comando `sudo`
El comando `sudo` (*superuser do*) permite a usuarios autorizados ejecutar comandos con privilegios de superusuario (**root**) de manera temporal. Esto es crucial para tareas administrativas que requieren permisos elevados, como la instalación de software o la modificación de archivos de sistema. La configuración de `sudo` se gestiona principalmente a través del archivo `/etc/sudoers`.
  
### Uso básico:
  
```bash
sudo comando
```
  
#### Ejemplo:
- Actualizar el sistema:
```bash
sudo apt update && sudo apt upgrade
```
  
### Editar un archivo protegido:

```bash
sudo nano /etc/hosts
```

## Archivo `/etc/sudoers`

El archivo `/etc/sudoers` define las reglas que determinan qué usuarios pueden utilizar `sudo` y qué comandos pueden ejecutar. Editar este archivo directamente puede ser riesgoso, ya que un error en la sintaxis puede impedir el uso de `sudo`. Por eso, se recomienda usar el comando `visudo`, que verifica la sintaxis antes de guardar los cambios.

### Uso de `visudo`

```bash
sudo visudo
```
- Este comando abre el archivo `/etc/sudoers` en el editor de texto predeterminado (generalmente `nano` o `vi`). `visudo` garantiza que el archivo no tenga errores de sintaxis antes de guardarlo.

## Estructura del archivo `/etc/sudoers`

El archivo `/etc/sudoers` tiene una estructura específica que define los permisos de los usuarios. A continuación se explican las más comunes:

### Permitir a un usuario específico usar `sudo`

Para permitir que un usuario ejecute cualquier comando como superusuario, se debe añadir una línea como la siguiente:

```bash
usuario ALL=(ALL:ALL) ALL
```
#### Ejemplo:

```bash
juan ALL=(ALL:ALL) ALL
```
- Esto permite al usuario `juan` ejecutar cualquier comando como superusuario.

### Permitir a un grupo usar `sudo`

Para permitir que todos los miembros de un grupo ejecuten comandos como superusuario, se debe añadir una línea como la siguiente:

```bash
%grupo ALL=(ALL:ALL) ALL
```

#### Ejemplo:

```bash
%produccion ALL=(ALL:ALL) ALL
```
- Esto permite que todos los miembros del grupo `produccion` puedan usar `sudo` para cualquier comando.
      
### Restricción de comandos específicos

Se puede restringir el uso del comando `sudo` sólo a comandos específicos, por ejemplo, para permitir que un usuario sólo pueda reiniciar el sistema:

```bash
juan ALL=(ALL) /sbin/reboot
```
- Esto permite que el usuario `juan` ejecute solo el comando `/sbin/reboot` con `sudo`.

## Configuraciones avanzadas

#### `NOPASSWD`
Se usa para permitir que un usuario ejecute comandos `sudo` sin tener que ingresar su contraseña:

```bash
juan ALL=(ALL:ALL) NOPASSWD:ALL
```
- Esto permite que el usuario `juan` ejecute el comando `sudo` sin necesidad de introducir su contraseña.
