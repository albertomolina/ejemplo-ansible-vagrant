# Ejemplo de balanceo con DNS

Utilizando entradas tipo A duplicadas en un servidor DNS es posible
realizar de forma muy sencilla un balanceo de carga entre varios equipos, esto
se conoce como DNS round robin [1]

En este caso vamos a realizar un balanceo de carga entre dos servidores web,
para lo que creamos un escenario con tres equipos:

* nodo1: 10.1.1.101 <- Servidor web
* nodo2: 10.1.1.102 <- Servidor web
* dns: 10.1.1.103 <- Servidor DNS

## Levantar el escenario

Simplemente ejecutamos la instrucción (habrá que instalar previamente
tanto vagrant como ansible):

```
$ vagrant up
```

Que levanta y configura los tres nodos.

## Prueba de funcionamiento

Si no ha habido errores durante la ejecución de los playbooks, se puede
comprobar que se realiza el balanceo www.example.com entre nodo1 y nodo2,
repitiendo la consulta DNS con dig:
```
$ dig @10.1.1.103 www.example.com
```

También puede verse de forma mucho más clara a través del navegador, para lo
cual es necesario añadir la dirección IP como servidor DNS primario la dirección
10.1.1.103 y podremos comprobar como se balancean las peticiones entre los dos
servidores web nodo1 y nodo2 (es necesario forzar la recarga, CTRL+F5 por
ejemplo).

[1] http://en.wikipedia.org/wiki/Round-robin_DNS
