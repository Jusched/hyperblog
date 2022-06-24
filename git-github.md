# git init
Inicializar el repositorio en la carpeta donde estemos posicionados

# git config --global user.name/email
Configurar quien somos en el repositorio

# git status
Estado del repositorio actual con todos los commit que estan en staging y los untracked files. 

# git rm --cached/force
Remueve el archivo del staging. Básicamente le dice a Git que deje de trackear el historial de cambios de estos archivos,
por lo que pasaran a un estado untracked.
git rm --force: Elimina los archivos de Git y del disco duro. Git siempre guarda todo, por lo que podemos acceder al registro de la existencia de los archivos, de modo que podremos recuperarlos si es necesario (pero debemos usar comandos más avanzados).

# git reset --soft/hard
Devuelve en el tiempo con los cambios todavia en staging para el proximo commit. 
Hard devuelve absolutamente todo y reversa cambios. 

# git rm vs git reset
Git rm lo elimina mas solo tenemos que volver en el tiempo para recuperar el ultimo commit. 
git reset nos ayuda a volver en el tiempo. Pero no como git checkout que nos deja ir, mirar, pasear y volver. Con git reset volvemos al pasado sin la posibilidad de volver al futuro. Borramos la historia y la debemos sobreescribir. No hay vuelta atrás.

# git reset HEAD
git reset HEAD: Este es el comando para sacar archivos del área de staging. No para borrarlos ni nada de eso,
solo para que los últimos cambios de estos archivos no se envíen al último commit, a menos que cambiemos de opinión y
los incluyamos de nuevo en staging con git add, por supuesto.
El ultimo commit, es considerado **HEAD**
--------------------------------------------------------------------------------------------------------------------------------------------------
# git add
Pasamos del directorio de trabajo, a la zona de "preparacion" o staging para que sean enviados al repositorio local. 

# git commit
Pasamos de la zona de "preparacion" o staging al repositorio local. 

# git clone *url*
Se trae una copia de los archivos del repositorio remoto al repositorio local y el directorio de trabajo. 

# git push 
Enviamos todo del repositorio local al repositorio remoto. 

# git fetch
Trae documentos del repositorio remoto al local sin crear copias en mi directorio de trabajo.
con **git merge** combino este documento del repositorio local con mi directorio de trabajo. 

# git merge
Este funciona en la rama donde este, sea la principal o una secundaria. 
Despues de esto, los cambios de las ramas que se mencionen en el commit se combinan junto
A los cambios de la rama actual para formar un archivo unificado. 

# git pull
Combina fetch y merge. 

# branches
Creamos una nueva rama con copias de la rama principal que podemos modificar mas los cambios no estaran reflejados alli. 

# conflictos
Estos ocurren cuando se modifican las mismas lineas de codigo. Cuando esto sucede, se deben de solucionar aceptando
o rechazando cambios al codigo realizados en las otras ramas. 
Despues de hacer esto, el cambio conflictivo sigue en la otra rama a la que se le pidio merge. 

# git pull origin master --allow-unrelated-histories
Esto se debe de hacer cuando en el repositorio existen archivos que no tenemos nosotros.
------------------------------------------------------------------------------------------------------------------------------
# git log --all --graph --decorate --oneline
Toda la historia del archivo en el git

# alias arbol="comando"
Para crear un atajo a la ejecucion del comando

# git push origin --tags
Para hacer push a los tags y en donde dice "branch" en github, aparecera el tag. 

# borrar tags equivocados/malhechos
git tag para verlos, git tag -d "tag" para borrarlo 
Se borra en git mas no en github
Para solucionarlo: git push origin :refs/tags/"tag"
-----------------------------------------------------
# git show-branch -all
Historia de los branches
**gitk** para verlo de manera visual viendo que se le añade y quita en cada version

# git push origin "branch"
Para cargar un branch especifico que hayamos usado 
-----------------------------------------------------------
**Como traer proyectos inicializados anteriormente**
## git clone "url repo"
Clona automaticamente todo, si el repo es publico, no pide contraseña
Si fuera privado, pediria usuario y contraseña

# Agregar colaboradores o personas con acceso a hacer **Push**
Settings del *repo* y collaborators.
Se puede usar el email o el nombre de usuario
Una vez hecho, ya se pueden hacer push desde el usuario nuevo. 
======================================================================
# Flujo de trabajo profesional
**En el Master solo se envia lo que esta listo para produccion, se trabaja en branches**
*No se deben de enviar archivos binarios como imagenes pues pesan mucho*

Es posible que los cambios en imagenes no se vean reflejados por lo que es necesario usar algo como Ctrl + Shift + R
Lo importante de trabajar en branches es que los demas pueden tener su trabajo para despues combinarlo en el main

# Proceso
git checkout master
git merge header
-m "Agregando x del proyecto"

Y asi con los demas branches. Esto generalmente lo hace el CTO, Product Manager

# Como funciona IRL
Los PR son la base de la colaboración a proyectos Open Source, si tienen pensando colaborar en alguno
es muy importante entender esto y ver cómo se hace en las próximas clases. Por lo general es forkear el proyecto,
implementar el cambio en una nueva rama, hacer el PR y esperar que los administradores del proyecto hagan el 
merge o pidan algún cambio en el código o commits que hiciste.

Los que hacen esto son generalmente los lideres de equipo o DevOps

Pull requests en github sirven para hacer merge en cambios que se puedan hacer facilmente, puede tener reviewers,
encargados, labels...
Una vez hecho el request, los demas pueden verlo. 
Una vez haya sido arreglado los cambios de uno de los archivos, se pide el merge. 
Si le damos a aprobar siendo reviewer, solo hace que ya haya realizado su labor de verificar. 
Un colaborador debe de hacer el merge. 
Algunos branchs pueden ser arreglos urgentes por lo que una vez realizado el merge, se puede eliminar el branch. 

# Resumen pull request (PR)
Son pausas antes de hacer el merge para hacer code review para hacer un trabajo completo. 

# Pull request desde open source
**Fork** es tomar una copia del estado actual del proyecto y clonarlo. SOLO GITHUB.
Hacemos las modificaciones y mandamos un PR
Podemos solo comentar o cerrar el PR

Para no quedarnos atras en el fork, es bueno crear otro branch dedicado a los cambios del open source. 

# Ignorando archivos
Si queremos que algo no se suba con push a git ni se vea en el status, creamos un .gitignore
*.jpg (Ignora todos los .jpg)

# github pages funciona para montar paginas web pero solo funciona con repos publicos

# rebase
reescribe la historia del repo, cambiando la historia donde comenzo la rama.
**Solo** debe de ser usado de manera local. 
*git rebase master (estando en una rama aparte)
-------------------------------------------------------
# stash
Guarda los cambios de un archivo en un "stash" temporal mientras me alisto para subir los cambios y revierte los cambios. 
Muy util cuando estoy probando algo

# git clean
Borra archivos 
git clean --dry-run 
Muestra la lista de archivos que seran borrados
*git clean -f*
No le importan las carpetas, le importan los archivos
**NO** afecta archivos en .gitignore

# cherry pick
git cherry-pick "hash del commit"
Es una mala practica porque estoy modificando la historia
--------------------------------------------------------------
# Emergencias
Imagina que borraste todo y jodiste todo. 
## git reflog
Mostrar absolutamente todo lo que ha pasado. 
Despues, agarramos el ultimo commit donde todo estaba bien
Y despues
## git reset --**HARD** (hash)
Para restaurar todo lo que se jodio. 
Desaparece tambien del log todos los cambios malos. 
SOLO DEBE DE HACERSE EN CASOS EXTREMOS

# git ammend
Si el commit quedo con algo faltante
Se hace primero el git add
Despues, git commit -- amend  para solucionarlo
Añade los cambios actuales con los del commit anterior
----------------------------------------------------------------------
# git grep
Buscar en commits y archivos
git grep color -->use la palabra color
git grep la --> donde use la palabra la
git grep -n color–> en que lineas use la palabra color
git grep -n platzi --> en que lineas use la palabra platzi
git grep -c la --> cuantas veces use la palabra la
git grep -c platzi --> cuantas veces use la palabra platzi
git grep -c “<p>”–> cuantas veces use la etiqueta <p>

git log-S “cabecera” --> cuantas veces use la palabra cabecera en
todos los commits.

grep–> para los archivos
log --> para los commits.

# comandos colaborativos
git shortlog muestra los commits de cada miembro
git shortlog -sn = muestra cuantos commit han hecho cada miembros del equipo.
git shortlog -sn --all = muestra cuantos commit han hecho cada miembros del equipo hasta los que han sido eliminado
git shortlog -sn --all --no-merge = muestra cuantos commit han hecho cada miembros quitando los eliminados sin los merges
git blame ARCHIVO = muestra quien hizo cada cosa linea por linea
git blame -c ARCHIVO lo mismo pero mas bonito
git COMANDO --help = muestra como funciona el comando.
git blame ARCHIVO -Linea_inicial,linea_final= muestra quien hizo cada cosa linea por linea indicándole desde que linea ver ejemplo -L35,50
**git branch -r **= se muestran todas las ramas remotas
git branch -a = se muestran todas las ramas tanto locales como remotas