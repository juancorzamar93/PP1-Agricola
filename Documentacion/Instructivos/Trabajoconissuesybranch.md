# Issues Branchs

## 1) Identificar la ISSUE

Es necesario que todas las modificaciones al codigo (documentacion, frontend, backend) estén referenciadas a una issue en GitHub. No se debe trabajar por fuera de las issues. Si no se puede identificar la issue hay dos alternativas: O bien crearla como nueva (si o si referida a una US-User Story existente, con el número de TK siguiente a las ya existentes en esa US) y cuidando de no generar issues duplicadas, o bien consultar en el grupo de WhatsApp.<br/>
Al momento de buscar las issues conviene hacerlo desde la vista del proyecto, empezando por la vista de [User Stories]

## 2) Ingresar a la issue elegida

Para ello hacer click en la issue del proyecto, ahi muestra un resumen, ir al link de la derecha "Open in new tab" y abrirá la issue completa en una nueva pestaña. En la issue, en el panel lateral, en "Development" hacer click en "Create a branch". Ahi propone un nombre automático, por ejemplo **Branch name = 1-us-01-redactar-un-informe-principal**, si se lo modifica no tocar la primera parte (el numero de issue para GitHub y el numero de issue para nosotros). Puede convenir acortar un poco el nombre para facilitar su lectura y escritura, y puede convenir colocarle un numero al final para referencias diferentes ramas de la misma TK. **No usar** ramas anteriores, siempre usar una **nueva** rama, renombrar con un numero al final para tener siempre una nueva. 
Luego en **Repo destination = https://github.com/mumido/PP1_Grupo_21**, y apretar "Change branch source" y seleccionar en "Branch source" a **develop**. Luego hacer click en **[x] Checkout locally**, y finalmente apretar el botón "Create branch". En ese momento se habrá creado una nueva rama para hacer los cambios deseados.
## 3) Trabajar sobre la rama en local

A continuación se describen los comandos para trabajar en consola local en nuestras computadoras. Cuando se empieza a trabajar en la issue es importante verificar que todo esté bien antes de hacer nada. Hay que estar ubicados en la rama de desarrollo "main" y hacer un **pull** antes de pasarse a la rama particular. Si se vuelve a trabajar otro dia en el mismo tema, antes de subir los cambios, igualmente conviene volver a traer la "main" por las dudas otro compañero haya hecho cambios que afecten en lo que estoy trabajando.

    $ cd <al directorio base donde se ubica el repo local>
    $ git checkout develop
    $ git pull
    $ git status
        En la rama develop
        Tu rama está actualizada con 'origin/develop'.
        nada para hacer commit, el árbol de trabajo está limpio

Si hay algún tipo de error en lo anterior (archivos en color rojo) lo mas coneveniente es renombrar ese directorio (por las dudas) y volver a clonar desde cero el repo. En lo que sigue se usa el ejemplo de la tarea "1-us-01-redactar-un-informe-principal", eso será diferente en cada caso, igualmente verificar siempre que se está trabajando sobre la issue correcta (en base al número de la tknn), ya que en algún momento pueden haber varias ramas particulares que estén activas.

    $ git fetch origin
    $ git branch
        * develop
        1-us-01-redactar-un-informe-principal

    $ git checkout 1-us-01-redactar-un-informe-principal
        Rama '1-us-01-redactar-un-informe-principal' configurada para hacer seguimiento a la rama remota '1-us-01-redactar-un-informe-principal' de 'origin'.
        Cambiado a nueva rama '1-us-01-redactar-un-informe-principal'

    $ git pull
    $ git status
        En la rama 1-us-01-redactar-un-informe-principal
        Tu rama está actualizada con '1-us-01-redactar-un-informe-principal'.
        nada para hacer commit, el árbol de trabajo está limpio

    $ git branch
        * 1-us-01-redactar-un-informe-principal
        develop

Luego se hacen todos los cambios deseados en los archivos. Puede convenir COPIAR los ARCHIVOS a un directorio trabajo EXTERNO, luego EDITAR ARCHIVOS, y finalmente COPIAR los ARCHIVOS MODIFICADOS devuelta al directorio donde está el repo. Luego se cierra el commit:

    $ git add ....     <-- para agregar archivos modificados
    $ git rm ....      <-- para borrar archivos
    $ git mv ....      <-- para cambiar de lugar archivos
    $ git add -A       <-- incorpora modif., agregados, borrados todo a la vez
    $ git status
         Cambios a ser confirmados:
         ....... verificar que todo esté bien y todos los archivos en color verde
    $ git commit -m '... mensaje ....'

Se suben los cambios al repo (se puede subir mas de un commit)

    $ git push -u origin 1-us-01-redactar-un-informe-principal 
        Username for 'https://github.com': ...........
        Password for 'https://......@github.com':  ... PAT(Personal Access Token) ....

Para ver como generar ese token PAT ver https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token


## 4) Incorporar estos cambios en rama "develop"

En este momento, los cambios que se hicieron solamente están en esa rama '1-us-01-redactar-un-informe-principal'. Para que pasen a la rama "develop" es necesario que se haga un pull-request. Para ello, entar al [repo en Github](https://github.com/mumido/PP1_Grupo_21) al enlace donde está la [cantidad de branchs](https://github.com/mumido/PP1_Grupo_21/branches), y debe aparecer la rama particular (aparece dos veces, como una rama del usuario y como una rama activa). Apretar el botón "New pull request" en cualquiera de esas dos. Nos pasará a una pantalla donde el título es lo mismo que pusimos en el commit (se puede editar, pero mejor dejarlo asi), y se debe selecionar la rama **base: develop**, y luego se pueden agregar comentarios a este pull-request, y apretar el botón "Create pull request".

Entar al [repo en Github](https://github.com/mumido/PP1_Grupo_21) al tercer enlace superior "Pull requests". Debe aparecer este nuevo "pull request" con el título del commit, entrar al mismo. Debe verse el mensaje **"This branch has no conflicts with the base branch"** (sino consultar al grupo). Si todo esta bien, desplegar el botoncito de la derecha de "Merge pull request" y seleccionar la segunda opción **"Squash and merge"**, y luego apretar ese botón "Squash and merge". Luego el boton **"Confirm squash and merge"**, y debe terminar con el mensaje "Pull request successfully merged and closed".

El pull request fue cerrado, se pueden ver todos los [pull request cerrados](https://github.com/mumido/PP1_Grupo_21/pulls?q=is:pr+is:closed). En esa vista se pueden ver las "linked issue" en la columna "Reviews", y si se va a esa issue, en "Development" se ve el pull-request con su nombre. La issue donde se estuvo trabajando puede dejarse abierta o cerrarse con "Close issue" (en otro momento se le puede hacer un "Reopen"). En el proyecto Kanban la issue sigue estando tal cual estaba, no hay cambios en labels ni status de la issue del proyecto.

Para verificar que todo esté bien, entar al [repo en Github](https://github.com/mumido/PP1_Grupo_21) al enlace donde está la [cantidad de commits](https://github.com/mumido/PP1_Grupo_21/commits/main) y verificar que con mi usuario aparezcan 1 commit con el comentario que puse en el commit.

Finalmente, la rama que se usó se debe borrar. Para hacerlo, ir al enlace de las [ramas](https://github.com/mumido/PP1_Grupo_21/branches) y apretar el ultimo iconito de Trash. Alternativamente, se puede entrar en el pull-request (cerrado) que corresponde y apretar el botón "Delete branch". En el repo local (en nuestra computadora) esa rama todavía existe, si se quiere borrar hay que hacer un "git branch -d nnnnn" (ver mas abajo).


## 5) Hacer el merge con la rama principal "main"

Para esto hay que hacer un nuevo pull-request para la incorporación de cambios de "develop" a "main". Esto se hará solamente al momento de finalizar los SPRINTs.


Entar al [repo en Github](https://github.com/mumido/PP1_Grupo_21) al tercer enlace superior "Pull requests". Debe aparecer este nuevo "pull request" con el título del commit, entrar al mismo. Debe verse el mensaje **"This branch has no conflicts with the base branch"** (sino consultar al grupo). Si todo esta bien apretar el botón "Merge pull request". Luego el boton "Confirm merge", y debe terminar con el mensaje "Pull request successfully merged and closed".


## 6) Volver a la rama "develop" y actualizarla en local

Al final, para que nos quede todo bien en nuestra computadora local:

    $ cd <al directorio base donde se ubica el repo>
    $ git checkout develop
    $ git pull                <-- debe traer el ultimo commit que hice
    $ git status

Finalmente se debe borrar la rama temporal de trabajo local (que ya no se va a usar). Por ejemplo, a continuación hay una rama extra en local que ya fueron subidas anteriomente, ahora se borran, y al final solo queda activa la rama "develop":

    $ git branch
        1-us-01-redactar-un-informe-principal
        * develop
    $ git branch -d 1-us-01-redactar-un-informe-principal
    $ git branch
        * develop
 