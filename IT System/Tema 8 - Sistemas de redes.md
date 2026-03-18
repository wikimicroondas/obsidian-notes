# IPs Privadas

| IP             | Clase | Rango completo                |
| -------------- | ----- | ----------------------------- |
| 10.0.0.0/8     | A     | 10.0.0.0 - 10.255.255.255     |
| 172.16.0.0/12  | B     | 172.16.0.0  - 172.31.255.255  |
| 169.254.0.0/16 | B     | 169.254.0.0 - 169.254.255.255 |
| 192.168.0.0/16 | C     | 192.168.0.0 - 192.168.255.255 |
### Calcular el rango de ip
Cortar los bits y asignar 1 o 0. Restar `Network` y `Broadcast`
## Octetos
0.0.0.0 - 255.255.255.255
Dirección de protocolo de Internet (IP)

| IPs           | Clase | Octetos |
| ------------- | ----- | ------- |
| 255.0.0.0     | A     | /8      |
| 255.255.0.0   | B     | /16     |
| 255.255.255.0 | C     | /24     |

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

# Cisco Packet Tracer

### CLI
`Example 1: Enable dhcp`
`router-config:` 192.168.0.254
-- enable dhcp --
ip dhcp pool
config-network 192.168.0.254 255.255.255.0

`Example 2: How to make internet`
~ ~ 4
## Práctica 1
---
1. Se establece una red, compuesta por dos ordenadores y un portátil. Los ordenadores están conectados a un Switch PT-Empty, mientras que el portátil está conectado a un AccessPoint P-T (a su vez conectado a al mismo Switch).
2. Este Switch está conectado a un Router PT-Empty.
3. El Router está configurado mediante CLI para habilitar DHCP con la IP `192.168.0.254`.
4. El comando destacado para este proceso es "dhcp pull".

## Práctica 2
---
1. Con la red anterior se plantea hacer "internet".
2. Se clona el router, quitando las IPs.
3. Se desconoce el procedimiento, en palabras del profesor "Quiero adaptar la máscara para no perder IPs".
4. En la imagen se aprecia una conexión Serial DTE con una anotación `100.0.0.0/30`.

## Práctica 3
---
1. Se quiere crear otra red o internet clonando el Router PT-Empty.
2. Teniendo la network `200.0.0.0/30`.