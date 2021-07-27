# Clase 4

1. Lo primero que vamos hacer es crear la carpeta para crear alli nuestro nuevo docker y para eso lo podemos hacer con este comando: 

    (mkdir proxy)
    
2. Luego lo que porcedemoa a realizar es a crear y editar el arcjivo compose y para esto lo hacemos con el siguiente comando: 

    (vim docker-compose.yml)
    (version: '3'
    services:
    web:
    image: dockercloud/hello-world
    lb:
    image: dockercloud/haproxy
    links:
      - web
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
    ports:
      - 80:80)
    
3. Ya despues de creado lo que hacemos es activar este contenedor y para ello lo hacemos con este comando:

    (docker-compose up -d)
    
4. O si queremos ver el estado del mismo lo podemos realizar con este comando:

    (docker-compose ps)
    
5. Tambien si ya no necesitamos que este servicio este activo lo podemos bajar y para ello lo que hacemos es ejecutar este comando:

    (docker-compose down)
    
6. Tambien lo que podemos realizar es mirar los logs que se estan elaborando al momento que acceden a nuestra url y para ello lo que hacemos es ejecutar este comando:

    (docker logs -f proxy_web_1)
 
7. Tambien lo que podemos hacer es crear varios contenedores al tiempo y automaticamente para asi evitar que si alguno falla los otros continuen funcionando sin problemas y para que esto funcione lo hacemos con este comando:

    (docker-compose up --scale web=5 -d)
    
8. Tambien hay otra manera de detener el contenedor y para ello lo hacemos por el id y asi se cierra solo uno en especifico y para esto lo que hacemos es ejecutar este comando: 

    (docker stop id )
    
    Nota: El contenedor es como el recipiente,           ejemplo podria ser el chasis de una torre y la       imagen es lo intangible que vendria siendo como       el sistema operativo de la maquina.

9. Y por ultimo para acceder a este proyecto que creamos lo hacemos con la direccion ip de nuestra maquina virtual y se le agrega el puerto 80, como se ve a continuacion: 

    (http://192.168.20.108:80/)
    
> Y ya por ultimo aca dejamos la refenrecias de esta instalación para una guia en un futuro:

* (https://jsgiraldoh.io/Blog/Archivo-docker-compose)
* (https://mmorejon.io/curso/integrando-docker-a-su-infaestructura-y-servicios/)
* (https://issuu.com/johanse/docs/seccion-12-archivo-docker-compose.pptx)
* (https://www.youtube.com/watch?v=HhhFpa4ZrpA)


# Nuevo proyecto con Jenkins

1. Lo que primero debemos realizar para crear nuestro nuevo proyecto es crear una carpeta nueva con el nombre del mismo y esto se hace con este comando:

    (mkdir jenkins)
    
2. Despues lo que hacemos es clonar el proyecto desde un git de otra persona y para ello lo hacemos con este comando: 

    (git clone https://github.com/jsgiraldoh/Jenkins)
    
3. Luego de que ya terminamos de clonar este proyecto lo que hacemos es mirar la configuracion de el docker de este mismo y esto se realiza con este comando: 

    (cat docker-compose-jenkins.yml)
    
4. Si depronto no sabemos en que ruta estamos dentro del sistema operativo lo que hacemos es ejecutar el siguiente comando y este no la muestra:

    (pwd)
    
5. Ya despues que terminamos todo el proceso de instalacion lo que ahora necesitamos es ejecutar el mismo y para ello lo hacemos con este comando:

    (docker-compose -f docker-compose-jenkins.yml up     -d)
    
6. Para poder modificar el proyecto debemos de cambiarle el propietario root que es el que tiene asignada esta carpeta en el momento y le debemos colocar el personal y para esto se ejecuta el siguiente comando: 

    (sudo chown cristhian:cristhian jenkins_home/)
    
7. Despues de que ya le cambiamos el propietario lo que hacemos es darle permisos de ejecucion a todos los usuarios y para esto lo que hacemos es ejecutar este comando:

    (sudo chmod 2777 jenkins_home/)
    
8. Luego si ya no necesitamos mas utilizar este contenedor lo que podemos hacer es bajarlo o detenerlo y para esto lo que hacemos es ejecutar este comando:

    (docker-compose -f docker-compose-jenkins.yml         down)
    
9. Despues que elaboramos este proceso ya lo que sigue es solicitar la calve del contenedor de jenkins para asi poder acceder al mismo desde la web y para que el nos de esta clave debemos de ejecutar este comando:

    (docker logs -f jenkins)
    
    Nota: la clave que nos sale al ejecutar este         comando es similar a esta                             "17464bf00b0a4a55948dd0990da13417" pero sin la       comillas
    
10. Luego lo que necesitamos es acceder a este contenedor que creamos desde la web y para ello lo hacemos desde cualquier navegador colocando la ip de nuestra maquina virtual y al final se coloca el puerto 8090, tal como lo vamos a ver a continuacion:

    (http://192.168.20.112:8090/)
    
11. Despues de acceder a este le colocamos la clave que anteriormente se mostro y ya despues de ponerla le damos clic a la opcion que dice instalar lo plugin sugeridos y alli comienza con la descarga de estos.

12. Luego de que finaliza la descarga lo que hace es solicitar un usuario, contraseña y correo, colocamos estos datos y le damos siguiente y guardar.

13. Y por ultimo ya cuando llenamos estos datos nos indica la url del jenkins y lo que hacemos es poner la url de nuestra maquina virtual nuevamente con el puerto 8090 (http://192.168.20.108:8090/) y le damos guardar y finalizar y ya con esto concluimos la creacion de este nuevo proyecto.
