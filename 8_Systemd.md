# Introducción a `systemd`

`systemd` es un gestor de servicios moderno, utilizado en la mayoría de las distribuciones Linux actuales, como Ubuntu, Fedora y Debian, es el primer proceso que se ejecuta al iniciar el sistema y es el último en detenerse durante el apagado. Es responsable de inicializar el espacio de usuario durante el arranque, así como de gestionar procesos, servicios, dispositivos montados y recursos del sistema de manera eficiente.

## Conceptos importantes

### Unidades (Units)

Una unidad en `systemd` es una representación de un recurso que `systemd` puede gestionar. Cada unidad está definida por un archivo de configuración y existen diferentes tipos de unidades según el recurso que representan:

- **Service Unit (`.service`):** Gestiona servicios del sistema, como servidores web o bases de datos.
- **Target Unit (`.target`):** Agrupa otras unidades para alcanzar un estado específico del sistema, como el multiusuario o el modo gráfico.
- **Mount Unit (`.mount`):** Gestiona puntos de montaje de sistemas de archivos.
- **Socket Unit (`.socket`):** Gestiona sockets para la comunicación entre procesos.
- **Timer Unit (`.timer`):** Gestiona tareas programadas, similar a `cron`.
- **Device Unit (`.device`):** Gestiona dispositivos de hardware.
- **Path Unit (`.path`):** Supervisa cambios en el sistema de archivos.

### Archivos de Unidad (Unit Files)

Los archivos de unidad son archivos de texto que contienen la configuración necesaria para que `systemd` gestione servicios y otros recursos. Estos archivos se encuentran generalmente en:

- `/etc/systemd/system/`: Archivos definidos por el usuario.
- `/lib/systemd/system/`: Archivos proporcionados por el sistema o los paquetes instalados.

Un archivo de unidad tiene una estructura definida por secciones, como `[Unit]`, `[Service]`, y `[Install]`, que agrupan diferentes configuraciones y propiedades.

**Ejemplo de Archivo de Unidad: `/etc/systemd/system/mi_servicio.service`**

```ini
[Unit]
Description=Mi Servicio Personalizado
After=network.target

[Service]
ExecStart=/usr/bin/mi_programa
Restart=always
User=nobody
Group=nogroup

[Install]
WantedBy=multi-user.target
```

- **[Unit]**
  - `Description`: Proporciona una breve descripción del servicio.
  - `After`: Especifica que este servicio debe iniciarse después de `network.target`.

- **[Service]**
  - `ExecStart`: Comando que inicia el servicio.
  - `Restart`: Configura `systemd` para reiniciar el servicio automáticamente si falla.
  - `User` y `Group`: Especifican el usuario y grupo bajo los cuales se ejecuta el servicio.

- **[Install]**
  - `WantedBy`: Define el objetivo al que pertenece el servicio. `multi-user.target` indica que el servicio debería iniciarse en un entorno multiusuario.

## **Gestión de Servicios con `systemctl`**

`systemctl` es una herramienta de línea de comandos y es mediante la cual se puede interactuar con `systemd`. Permite iniciar, detener, reiniciar y obtener el estado de los servicios, así como habilitar o deshabilitar servicios para que se inicien automáticamente durante el arranque del sistema.

### Estado del Servicio

**Comando:**
```bash
sudo systemctl status ssh
```
- Este comando muestra el estado actual del servicio `ssh`, incluyendo su estado de actividad (**activo, inactivo, fallido**) y los logs recientes.

### Iniciar un Servicio

**Comando:**
```bash
sudo systemctl start apache2
```
- Inicia el servicio `apache2`. No lo habilita para que se inicie automáticamente al arrancar el sistema.

### Detener un Servicio

**Comando:**
```bash
sudo systemctl stop apache2
```
- Detiene el servicio `apache2`.

### Reiniciar un Servicio

**Comando:**
```bash
sudo systemctl restart apache2
```
- Reinicia el servicio `apache2`, deteniéndolo y luego iniciándolo nuevamente.

### Habilitar un Servicio para que se Inicie Automáticamente

**Comando:**
```bash
sudo systemctl enable apache2
```
- Configura el servicio `apache2` para que se inicie automáticamente al arrancar el sistema.

### Deshabilitar un Servicio

**Comando:**
```bash
sudo systemctl disable apache2
```
- Evita que el servicio `apache2` se inicie automáticamente al arrancar el sistema.

## **Recargar la Configuración de `systemd`**

Después de crear o modificar un archivo de unidad, es necesario recargar la configuración de `systemd` para que los cambios surtan efecto.

**Comando:**
```bash
sudo systemctl daemon-reload
```
- Este comando informa a `systemd` sobre los cambios en los archivos de unidad y recarga su configuración.

## Ejemplos Prácticos

### Crear y Gestionar un Servicio Personalizado

**Paso 1: Crear el archivo de unidad**
```ini
[Unit]
Description=Mi Servicio Personalizado
After=network.target

[Service]
ExecStart=/usr/bin/mi_programa
Restart=always
User=nobody
Group=nogroup

[Install]
WantedBy=multi-user.target
```

**Paso 2: Guardar este contenido en `/etc/systemd/system/mi_servicio.service`.**

**Paso 3: Recargar `systemd`**
```bash
sudo systemctl daemon-reload
```

**Paso 4: Iniciar el servicio**
```bash
sudo systemctl start mi_servicio
```

**Paso 5: Habilitar el servicio para que se inicie automáticamente**
```bash
sudo systemctl enable mi_servicio
```

**Paso 6: Verificar el estado del servicio**
```bash
sudo systemctl status mi_servicio
```

## Herramienta `journalctl`

**`journalctl`** es una herramienta de línea de comandos utilizada para consultar los logs del sistema registrados por systemd. Los logs incluyen mensajes del kernel, mensajes de inicio de servicios y cualquier otra información registrada por los servicios y aplicaciones del sistema. `journalctl` permite filtrar y ordenar los logs, proporcionando una poderosa herramienta de diagnóstico y auditoría del sistema.

### Parámetros Comunes:

**Ver todos los logs del sistema.**
```bash
journalctl
```

**Ver los logs relacionados con una unidad específica**
```bash
journalctl -u apache2
```

**Siguir los logs en tiempo real.**
```bash
journalctl -f
```

**Ver los logs desde una fecha específica.**
```bash
journalctl --since "2023-01-01":
```

**Ver los logs hasta una fecha y hora específica.**
```bash
journalctl --until "2023-01-01 12:00:00"
```

**Filtrar los logs por nivel de prioridad.**
```bash
journalctl -p err  # Muestra solo los logs con prioridad de error
```

**Filtrar los logs por ID de proceso.**
```bash
journalctl _PID=1234
```

## Comandos Útiles de `systemctl`

### Listar Unidades Activas

**Comando:**
```bash
systemctl list-units --type=service --state=active
```
- Lista todas las unidades de servicio activas en el sistema.

### Más Información sobre un Servicio

**Comando:**
```bash
systemctl show apache2
```
- Muestra información detallada sobre el servicio `apache2`, incluyendo sus propiedades y configuraciones actuales.

### Ver los Logs de un Servicio

**Comando:**
```bash
journalctl -u apache2
```
- Muestra los logs generados por el servicio `apache2`.

## **Conclusión**

`systemd` es una herramienta fundamental para la gestión de servicios en sistemas Linux modernos. Su estructura basada en unidades y archivos de configuración permite una administración flexible y eficiente de recursos del sistema. Con el conocimiento de `systemd` y `systemctl`, se puede gestionar, automatizar y supervisar servicios de manera efectiva, mejorando así la estabilidad y el rendimiento del sistema.