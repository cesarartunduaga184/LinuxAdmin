# Configuración de Red

## Conceptos básicos de red (IP, DNS, Gateway)
  
### IP (Internet Protocol)

Dirección única asignada a cada dispositivo en la red:

- **IPv4:** Formato `192.168.1.1`
- **IPv6:** Formato `2001:0db8:85a3:0000:0000:8a2e:0370:7334`
- **DNS (Domain Name System):** Sistema que traduce nombres de dominio (como `www.ejemplo.com`) en direcciones IP.
- **Gateway:** Dispositivo que conecta redes diferentes, generalmente el router que conecta una red local a Internet.

## Configuración de interfaces de red

### Comandos importantes:

- **`ifconfig`:** Muestra o configura las interfaces de red (este comando esta obsoleto, fue reemplazado por `ip`).

```bash
ifconfig
```

- **`ip`:** Comando moderno para gestión de interfaces de red.

```bash
ip addr show
```

### Habilitar o deshabilitar una interfaz de red:

```bash
sudo ip link set eth0 up
sudo ip link set eth0 down
```

### Herramientas de diagnóstico de red

- `ping`: Comprueba la conectividad con otro dispositivo.
```bash
ping www.google.com
```

- `netstat`: Muestra conexiones de red, tablas de enrutamiento, estadísticas de interfaz, etc.
```bash
netstat -tuln
```
- `-t`: Conexiones TCP
- `-u`: Conexiones UDP
- `-l`: Muestra los sockets a la escucha
- `-n`: No realiza resolución de nombres

- `traceroute`: Rastrea la ruta que toma un paquete hasta el destino.

```bash
traceroute www.google.com
```

- `nslookup`: Consulta servidores DNS para obtener información de nombres de dominio.
```bash
nslookup www.ejemplo.com
```