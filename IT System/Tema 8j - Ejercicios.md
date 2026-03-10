#### - - Solucionario - -
## Práctica 1: Establecer conexiones DHCP
---
### 1. Preparar los equipos "PT-Empty"
Los dispositivos que llevan la etiqueta "Empty" (`Switch4 (PT-Empty)` y `Router2 PT-Empty`) vienen completamente vacíos por dentro, sin puertos donde enchufar los cables.

1. Para modificar los puertos necesitamos apagar los equipos primero, mediante la pestaña de configuración: `Physical > Apagar el equipo`. Las luces deben ponerse rojas.

2. A la izquierda se encuentra la lista de módulos, arrastra puertos de red, el cableado estándar requiere de módulos `Gigabit Ethernet`, con estos será suficiente.
	-  `PT-ROUTER-NM-1CGE` - Router
	-  `PT-SWITCH-NM-1CE` - Switch
	
3. Vuelve a encender los equipos.

### 2. Conectar el cableado y el AP
Para establecer conexión estándar, se utiliza el cable de cobre directo (discontinuo negro).

1. Conecta dos ordenadores `PC0` y `PC1` a los puertos del Switch.
2. Conecta `AccessPoint0` al Switch.
3. Conecta el Switch al `Router2`

### 3. Configurar el portátil para el Access Point
Los portátiles de Packet Tracer no tienen placas de Wi-Fi por defecto, hay que añadírselo.

1. `Laptop0 > Physical > Apagar el equipo`
2. Sustituimos el puerto de red por `WPC300N` (antena de wifi)
3. Encender el equipo

Al encender el dispositivo, automáticamente se conectará a la red.

### 4. Configurar el Router y el DHCP por CLI
1. `Router2 > CLI`
2. Pulsa `Enter`
3. Comandos:

```Cisco CLI
// Se asume que está conectado por gigabitEthernet 0/0
enable
configure terminal

// La puerta de enlace será 192.168.0.254
interface gigabitEthernet 0/0
ip address 192.168.0.254 255.255.255.0
no shutdown
exit

// Crear el servidor DHCP para que asigne dinámicamente IPs a los ordenadores
ip dhcp pool RED_LOCAL
network 192.168.0.0 255.255.255.0
default-router 192.168.0.254
exit
```

### 5. Activar el DHCP en los equipos
1. En cada dispositivo (PC0, PC1, Laptop0)
2. `Desktop > IP Configuration`
3. Cambia el botón Static => DHCP
4. En un par de segundos aparecerá un mensaje de éxito y se le asignará automáticamente una IP

## Práctica 2: Ampliar la red (Internet)
---
Se quiere aplicar un concepto más complejo llamado VLSM (Máscara de Subred de Longitud Variable). Es un concepto de optimización para no desperdiciar direcciones IP.

