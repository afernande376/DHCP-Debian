# Instalación y configuración de ISC-DHCP-SERVER en Debian
***



  
  
![Debian](/fotos/debian.png) 

## Índice  
[1. Introducción](#introducción)  
[2. Configuracíon de red del equipo](#configuración-de-la-tarjeta-que-debe-escuchar)  
[3. Instalación del servidor](#3-instalación-del-servidor)  
[4. Configuración de tarjeta en la que escucha](4-configuración-de-la-tarjeta-que-debe-escuchar)
[5. Fichero de configuración principal](#5-fichero-de-configuración-principal)



## 1. Introducción
En este documento vamos a instalar un servidor DHCP en Debian. El nombre del software es **isc-dhcp-server**. 

## 2. Configuración de red del equipo 
El equipo donde vayamos a realizar la instalación deberá tener configurada una dirección ip **estática**, es decir, **fija** que habrás configurado manualmente. 

Para verificar que la configuración de red se ha aplicado deberás utilizar el comando ``ip addr``. Además deberás **anotar el nombre de la interfaz de red** porque la utilizaremos más adelante. 

```
ip address
```

## 3. Instalación del servidor 

1. Cambiar al usuario `root` o ejecutar los comandos con `sudo`.
```
su - 
```

2. Ejecutar el comando de instalación del paquete **isc-dhcp-server**.
```
apt install isc-dhcp-server
```

## 4. Configuración de la tarjeta que debe escuchar

Para indicarle al servicio cuál es la tarjeta de red a través de la cual se recibirán las peticiones DHCP, se debe modificar el archivo `/etc/default/dhcp/isc-dhcp-server` editándolo por ejemplo con el editor de textos **nano**. 

```
nano /etc/default/isc-dhcp-server
```

Buscaremos dentro del archivo el parámetro `INTERFACESv4` y modificaremos el valor susituyéndolo por el de nuestra tarjeta:
```
...
INTERFACESv4="enp0s3"
...
```

## 5. Fichero de configuración principal

El fichero de configuración principal lleva por nombre `/etc/dhcp/dhcpd.conf` y consta de configuraciones ejemplo que debemos ajustar a nuestras preferencias.

![dhcpd.conf](/fotos/dhcpdconf.png)





