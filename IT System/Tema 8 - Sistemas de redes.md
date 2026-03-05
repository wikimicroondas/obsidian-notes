## Cisco Packet Tracer

### CLI
`Example 1: Enable dhcp`
`router-config:` 192.168.0.254
-- enable dhcp --
dhcp pull
config-network 192.168.0.254 255.255.255.0

`Example 2: How to make internet`
~ ~ 4

## Octetos
0.0.0.0 - 255.255.255.255
Dirección de protocolo de Internet (IP)

| IPs           | Clase | Octetos |
| ------------- | ----- | ------- |
| 255.0.0.0     | A     | /8      |
| 255.255.0.0   | B     | /16     |
| 255.255.255.0 | C     | /24     |
|               |       |         |

## Redes
### Ejercicio 1
	192.168.0.0/24
- `/24` - Tres octetos reservados | 255.255.255.0
- `Network:` 192.168.0.0
- `Broadcast:` 192.168.0.255
- `IPs útiles:` 192.168.0.1 - 192.168.0.254

El rango de IPs útiles se calcula dentro del primer octeto, delimitado excluyendo la IP Broadcast y Network.
1 mín - 254 máx

### Ejercicio 2
	192.168.0.0/8
- `/8` - Un octeto reservado | 255.0.0.0
- `Network:` 192.0.0.0
- `Broadcast:` 192.255.255.255
- `IPs:` 192.0.0.1 - 192.255.255.254

Con cualquier máscara podemos controlar cualquier red.