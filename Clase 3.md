# Clase 3

* Al comienzo de la clase vimos lo que es una imagen, y esta es una plantilla de instrucciones para asi poder crear un contenedor de docker, tambien se puede crear una imagen basada en otra, es decir crear una imagen de alguien mas pero luego proceder con la personalización  de la misma. Una imagen esta compuesta de:

    a) Sistema de ficheros
    b) Parametros para ejecutarla
    c) No tiene estado
    d) Nunca cambia

* Tambien vimos que los contenedores son una instancia ejecutable de una imagen. Y estos se pueden crear, iniciar detenet, mover o eliminar un contenedor. Tambien un contenedor se define por su imagen, asi como por las opciones de configuracion que le proporcione cuando lo cree o lo inicie.Un contenedor esta compuesto de:

    a) Instancias en ejecucion de una imagen
    b) Tiene estados
    c) Cambia durante su ejecucion
    
# Creacion de direcctorios y carpeta

1. Lo que primero que hacemos es crear una carpeta donde queremos crear nuestro docker y para eso lo hacemos con el siguiente comando: 

    (mkdir mi-primer-dockerfile)
    
2. Luego de creada dicha carpeta lo que hacemos es ingresar a la misma, para ello lo hacemos con este comando: 

    (cd mi-primer-dockerfile)
    
3. Luego creamos un documento vacio para entrar a modificarlo lo hacemos con este comando: 

    (vim Dockerfile)
    
    Nota: para editar estos archivos se debe             presionar la tecla i, y para salir despues de         modificado se le da la tecla esp y luego :wq, con     esto guardamos los cambios.

4. Despues que crear el archivo de Dockerfile le vamos agregar la ruta del directorio la cual seria la siguiente:

    (FROM nginx
    COPY static-html-directory /usr/share/nginx/html)
    
5. Luego procedemos a crear el directorio del html y para que esto se pueda realizar lo hacemos con este comando: 

    (mkdir static-html-directory)
    
6. Luego de creado dicha directorio lo que hacemos es ingresar a la misma, para ello lo hacemos con este comando: 

    (cd static-html-directory/)
    
7. Luego procedemos a modificar el archivo index.html y le colocamos cualquier mensaje que deseemos, para esto se ejecuta este comando: 

    (vim index.html)
    
8. Ya despues de crear las carpetas y las rutas lo que vamos hacer es a proceder con la creacion del docker y para ello lo debemos de realizar con este comando: 

    (docker image build -t some-content-nginx .)
    
9. Para validar que ya instala adecuadamente nuestro docker lo hacemos con este comando:

    (docker image ls)
    
10. Ya como lo instalamos adecuadamente lo que vamos hacer es ponerlo a correr para que asi nos muestre el mensaje que agreagamos en el index.html, para que nos muestre este le colocamos el siguiente comando:

    (docker run --name some-nginx -d -p 8080:80 some-     content-nginx)
    
11. Ya luego lo que podemos hacer es mirar este mismo mensaje que agregamos pero en cualquier navegador que deseemos y para ello lo primero que hacemos es ver la ip de nuestra maquina virtual con este comando: 

    (ip a s)
    
    Nota: siempre se debe de seleccionar la direccion     ip que esta en en enp0s3.
    
12. Ya despues que sabemos cual es la direccion ip de nuestra maquina virtual lo que hacemos es agregarle el puerto 8080 asi como se ve a continuacion: 

    (http://192.168.20.106:8080/)
  
> Y ya por ultimo aca dejamos la refenrecias de esta instalación para una guia en un futuro:
 
* (https://docs.docker.com/engine/reference/commandline/commit/)
* (https://issuu.com/johanse/docs/seccion-4-imagenes-y-contenedores.pptx)
* (https://docs.docker.com/get-started/overview/)
    
# Creacion de docker en la web

1. Lo primero que se debe de ralizar es crear la cuenta en la siguiente pagina: 

* (https://hub.docker.com/signup?next=%2F%3Fref%3Dlogin)

2. Ya despues de creado nuestro usaurio lo que hacemos es loguearnos en nuestra maquina virtual con el siguiente comando: 

    (docker login)
    
    Nota: debemos colocar el usuario adecuadamente o     luego no nos dejara subir bien el archivo que         queremos.
    
3. Despues de iniciar sesion desde nuestra maquina virtual a docher web, lo que debemos hacer es darle la ruta a nuestro archivo de a donde va a subir y le colocamos el nombre que deseemos a la carpeta donde va quedar almacenado, para ello se hace con este comando: 

    (docker tag some-content-nginx                        atecristian11/fedesoft-web)
    
4. Y ya cuando estamos seguros que lo deseamos subir a nuestro repositorio web lo que hacemos es ejecutar este comando: 

    (docker push atecristian11/fedesoft-web)
    
5. Si por depronto hicimos algo mal en el proceso y deseamos eliminarle el tag, lo podemos hacer con este comando:

    (docker image rm atecristian11:fedesoft-web)
    
6. Tambien podemos clonar docker de otras personas y para hacer esto es muy sencillo lo unico que debemos hacer es ejecutar este comando: 

    (docker pull jsgiraldoh/fedesoft-web)
    
7. Si ya despues de descargar este archivo de otra persona lo quieres poner a correr lo que deberias de hacer es ejecutar este comando: 

    (docker run --name fedesoft-web -d -p 8081:80         jsgiraldoh/fedesoft-web)
    
8. Si ya lo que queremos hacer es detener este docker lo realizamos con este comando: 

    (docker stop --name fedesoft-web -d -p 8081:80        jsgiraldoh/fedesoft-web)
    
9. Y ya por ultimo si lo que queremos es clonar un archivo desde nuestro propio repositorio de docker lo podemos hacer realidad con este comando:

    (docker pull atecristian11/fedesoft-web)
    

> Y ya por ultimo aca dejamos mi docker con el ejercicio realizado en la clase:
 
* (https://hub.docker.com/repository/docker/atecristian11/fedesoft-web)
    
