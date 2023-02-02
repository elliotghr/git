# GITHUB

## Introducción

Git es un software de control de versiones distribuido y descentralizado que permite a un equipo de desarrolladores trabajar sobre el mismo código.

Se denomina "distribuido" porque cada miembro del equipo dispone de una copia completa del código.

Los miembros del equipo pueden enviarse código, recibirlo y desarrollar funcionalidades de forma conjunta y separada del servidor central.

Algunas ventajas de usarlo:

- Es el estándar actual.
- Código colaborativo, versionado y distribuido.
- Recuperación de archivos.
- Mayor control.
- Shorcuts y plugins.
- Mejora la productividad.

## Configuración inicial

### Configurando Git por primera vez

    # (la bandera --global permite una configuración en todo el SO, esta config estará en todas las carpetas)

    git --version
    git config --global user.name "Jonathan MirCha"
    # (correo electrónico en github)

    git config --global user.email jonmircha@gmail.com
    git config --global user.ui true
    git config --global init.defaultBranch main
    # (para listar la configuración)

    git config --list

    # (asignando visual studio code como editor de configuración de git)

    git config --global core.editor "code --wait"
    # (para poder editar esta configuración en VSCode)
    git config --global -e

    # (para estandarizar los saltos de línea en windows)

    git config --global core.autocrlf true

    # (para estandarizar los saltos de línea en linux/mac)

    git config --global core.autocrlf input

    # (ver todas las opciones de la configuración en la terminal)

    git config -h

    # (ver todas las opciones de la configuración en el navegador)

    git help config

## Inicializar Git en un directorio local

    mkdir carpeta
    cd carpeta
    touch README.md
    touch .gitignore
    # (para empezar a trackear carpeta)
    git init
    code .

## Flujo básico

El flujo de Git, consta de tres estados locales, es decir en la computadora donde se esta trabajando y uno más de forma remota cuando accedemos al codigo centralizado en plataformas como GitHub, Gitlab, Bitbucket, etc.

Dichos estados son modified, staged, committed y remote. A cada uno de ellos le corresponde un área de trabajo:

1.- Working Directory: Es el área correspondiente al estado modified y es la carpeta local de tu computadora donde almacenas los archivos de tu proyecto.
2.- Staging Area: Es el área correspondiente al estado staged también se le llama index por que es el área donde git indexa y agrega los cambios realizados en los archivos previos a comprometerlos en su registro.
3.- Local Repository: Es el área correspondiente al estado committed, donde los cambios ya se han registrado en el repositorio de git también se le llama HEAD por que indica en qué cambio se encuentra el puntero del repositorio.
4.- Remote Repository: Es el área correspondiente al estado remote y es el directorio remoto donde almacenamos los archivos del proyecto en alguna plataforma web como GitHub, GitLab, BitBucket. Git denomina origin al repositorio remoto.

![git-flow](/assets/git-flow.png)

    # agregar los cambios de un archivo al staged
    git add archivo/directorio
    # agregar todos los cambios de todos los archivos al staged
    git add .


    # los cambios son comprometidos en el repositorio
    # debes escribir el mensaje del cambio
    # cuando se abra el archivo de configuración
    # al terminar guarda y cierra el archivo
    # para que los cambios tengan efecto
    git commit
    # es un shortcut del comando anterior
    # escribes y confirmas el mensaje del cambio en un sólo paso
    git commit -m "mensaje descriptivo del cambio"


    # se agrega el origen remoto de tu repositorio de GitHub
    git remote add origin https://github.com/usuario/repositorio.git
    # la primera vez que vinculamos el repositorio remoto con el local
    git push -u origin master
    # para las subsecuentes actualizaciones, sino cambias de rama
    git push


    #para descargar los cambios del repositorio remoto al local
    git pull

## Para reemplazar la rama master por main en GitHub

    # Paso 1 
    # Crea la rama local main y pásale el historial de la rama master
    git branch -m master main

    # Paso 2
    # Haz un push de la nueva rama local main en el repositorio remoto de GitHub
    git push -u origin main


    # Paso 3
    # Cambia el HEAD actual a la rama main
    git symbolic-ref refs/remotes/origin/HEAD refs/remotes/origin/main

    Paso 4
    Cambia la rama default de master a main en tu repositorio de GitHub .

    Para hacerlo, sigue las instrucciones de este enlace.

    # Paso 5
    # Elimina la rama master del repositorio remoto
    git push origin --delete master

## Ayuda

    # ayuda en la terminal
    git comando -h
    # ayuda en el navegador
    git help comando

## Ignorar archivos

En el archivo .gitignore incluimos todo lo que NO queramos incluir en nuestro repositorio. Lo podemos crear manualmente o con gitignore.io.

    # esto es un comentario
    archivo.ext
    carpeta
    /archivo_desde_raiz.ext
    # ignorar todos los archivos que terminen en .log
    *.log
    # excepto production.log
    !production.log
    # ignorar los archivos terminados en .txt dentro de la carpeta doc,
    # pero no en sus subcarpetas
    doc/*.txt
    # ignorar todos los archivos terminados en .txt dentro de la carpeta doc
    # y también en sus subcarpetas
    doc/**/*.txt
    # podemos hacer uso de la siguiente app para agregar archivos a ignorar dependiendo de la tecnología
    [gitignore-link](https://www.toptal.com/developers/gitignore)
