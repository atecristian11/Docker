# Clase 2

1. Ya lo que se hizo en la segunda clase fue el comienzo de la instalación de docker en las maquinas, asi que lo primero que hicimos fue descargar moba para asi podernos conectar a la maquina virtual de ubuntu por ssh, ya despues de realizar este proceso ahora si comenzamos con la instalación de la herramienta docker engine y lo primero que hicimos fue realizar una actualización al sistema con este comando:

    (sudo apt-get update)
  
  
2. Luego lo que procedemos a realizar es la instalación de paquetes para permitir el uso de un repositorio sobre HTTPS y para esto utilizamos este comando:

    (sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common)
  
  
3. Despues de estos pasos lo que procedemos hacer es lo siguiente agregamos la clave GPG oficial de Docker con este comando: 

    (curl -fsSL https://download.docker.com/linux/ubuntu/gpg     | sudo apt-key add -)
 
 
4. Luego seguimos con el proceso y agregamos los repositorios estables de docker con este comando: 

    (sudo add-apt-repository \
    "deb [arch=amd64] https://download.docker.com/linux         /ubuntu \
    $(lsb_release -cs) \ stable"
    )


5. Despues debemos de actualizar los paquetes relacionados con los repositorios del sistema con este comando: 

    (sudo apt-get update)
    
    
6. Y por ultimo lo que hacemos es instalar la versión para la comunidad, conocido como el docker ce con este comando:

    (sudo apt-get install docker-ce docker-ce-cli               containerd.io)


# Verificaciión de la instalación de docker

* Lo primero que hacemos es mirar que version de docker nos instalo con este comando:

    (docker --version)
    
* Luego obtenemos la información de la instalación de docker en el sistema con este comando:

    (docker info)  
    
* Despues de ver que la instalación fue un exito procedemos con la agregación del usuario nuestro al grupo de docker para asi poder realizar modificaciones sin necesidad de colocar el comando sudo y para hacer esto realidad lo hacemos con este comando:

    (sudo usermod -aG docker ubuntu)
    
* Y por ultimo lo que hacemos es crear nuestro primer contenedor con el siguiente comando:

    (docker container run hello-world)


> Y ya por ultimo aca dejamos la refenrecias de esta instalación para una guia en un futuro:

* (https://docs.docker.com/engine/install/ubuntu/)
* (https://www.youtube.com/watch?v=3p-6Zi6g_jc)


# Intalación de docker compose

1. Lo primero que hacemos es descargar la versión estable y actual de docker compose con este comando:

    (sudo curl –L "https://github.com/docker/compose             /releases/download/1.25.5/docker-compose-$(uname             -s)-$(uname -m)" -o /usr/local/bin/docker-compose)

2. Despues procedemos dandole permisos de ejecución a este aplicativo que acabamos de instalar y para realizar eso lo hacemos con este comando:

    (sudo chmod +x /usr/local/bin/docker-compose)
    
3. Y por ultimo lo que hacemos es probar que la instalación alla culminado de la manera adecuada y eso se hace con este comando:

    (docker-compose --version)

> Y ya por ultimo aca dejamos la refenrecias de esta instalación para una guia en un futuro:

* (https://docs.docker.com/compose/install/)


# Estructura de comandos basicos

1. Lo primero que debemos hacer cuando ya terminamos con todo este proceso de instalación de todos los docker es mirar la ayuda de este mismo para mirar lo uqe hacen los comandos, y para esto utilizamos este comando:

    (docker --help | more)
    
2. Asi como le pedimos ayuda al docker tambien se puede hacer lo mismo con el modulo del sistema de este, para poder ingresar a este lo que debemos hacer es ejecutar este comando: 

    (docker system --help)
    
3. Tambien podemos ver la información del sistema de docker y para ello lo que debemos hacer es ejecutar este comando: 

    (docker system info)
    
4. Para mirar el status del docker lo podemos hacer con este comando: 

    (sudo systemctl status docker)

5. Para que cada vez que iniciemos la maquina virtual y queramos que el docker se inicie de inmediato lo que hacemos es ejecutar este comando:

    (Sudo docker-compose up -d)
    
6. Y ya por ultimo tambien podemos revisar los recursos de docker con este comando:

    (docker system df)

> Y ya por ultimo aca dejamos la refenrecias de esta instalación para una guia en un futuro:

* (https://mmorejon.io/curso/integrando-docker-a-su-infaestructura-y-servicios/)
* (https://www.youtube.com/watch?v=hohMvLG54bg)


# Clonación de docker y conexión con el mismo

1. Para clonar un proyecto de git lo que se debe de hacer es tener instalado y configurado en el equipo git bash, ya con esto ejecutamos dicha terminar y le colocamos el siguiente comando para que la clone a nuestro equipo local:

    (git clone https://github.com/jsgiraldoh/Codimd.git)
    
2. Luego de que esta ya esta clonada en nuestros equipos lo que acceso es acceder a esta carpeta que clonamos y para ello debemos de utilizar este comando: 

    (cd Codimd)
    
3. Luego de este comando ya lo que se hace es descargar los elementos que estaban en este docker para que asi pueda funcionar el mismo desde la web.

4. Ya para acceder al docker lo que hacemos es abrir cualquier navegador que tengamos y escribimos la dirección ip de nuestra maquina virtual en el mismo, luego le ponemos dos puntos(:) y el puerto 3000, asi de esta forma ya nos cargara la pagina para que agreguemos las notas que deseemos del mismo, a continuación se coloca el ejemplo de la dirección ip:

    (192.168.20.106:3000)