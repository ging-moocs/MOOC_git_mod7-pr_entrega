
<img  align="left" width="150" style="float: left;" src="https://www.upm.es/sfs/Rectorado/Gabinete%20del%20Rector/Logos/UPM/CEI/LOGOTIPO%20leyenda%20color%20JPG%20p.png">

<br/><br/><br/>

# Módulo 7: Contribuir a repositorios de terceros con pull-request, integración automática, y comandos Git: branch, clone, fetch, merge, pull y push - Entrega P2P: Pull Request

Versión: 28 de enero de 2024

## Objetivos
 * Usar dos repositorios remotos, uno como respaldo del repositorio de trabajo local y otro como repositorio central donde las contribuciones se envían con pull-request. 
 * Practicar con ramas remotas de diversos tipos
 * Realizar integraciones de desarrollos sencillos.

## Descripción de la práctica

En esta práctica vamos a duplicar el repositorio [https://github.com/ging-moocs/MOOC_git_mod7-cal_2com](https://github.com/ging-moocs/MOOC_git_mod7-cal_2com) en nuestra cuenta de GitHub, de nuevo usando el botón de "Fork". Este repositorio tiene 2 commits en la rama master. El primer commit añade los ficheros README.md y LICENSE, y el segundo commit añade el fichero calculator.html con una calculadora que tiene solo el botón x^2.

Primero vamos a crear una organización o una segunda cuenta con un nombre diferente (<tu_cuenta_2>) en GitHub. A continuación duplicamos el repositorio (https://github.com/<mi_usuario_de_github>/MOOC_git_mod7-cal_2com), ya clonado en la primera cuenta, en esta última.

Luego clonamos el repositorio "MOOC_git_mod7-cal_2com" de <tu_cuenta_2> en un repositorio local y creamos un nuevo commit en la rama "master" del repositorio local que añada al fichero calculator.html una cabecera HTML (&lt;h1&gt;) al comienzo del body con el texto "Calculadora de <nombre y apellidos>".

Copiamos la rama "inverse" del repositorio [https://github.com/ging-moocs/https://github.com/ging-moocs/MOOC_git_mod7-cal_branches](https://github.com/ging-moocs/https://github.com/ging-moocs/MOOC_git_mod7-cal_branches) a nuestro repositorio local. Esta rama tiene 3 commits, el primero y el segundo son los mismos que los dos primeros de la rama master de "cal_2com" y el tercero añade el botón 1/x a la calculadora.

Integramos primero la rama master en la rama inverse. La integración debe incorporar el título &lt;h1&gt; de la rama master y los dos los botones x^2 y 1/x de la rama inverse.

Integramos a continuación también la rama inverse en la rama master (con FF)y subimos ambas ramas al repositorio origen de la clonación en la segunda cuenta.

Una vez subidas envíe la integración realizada en la rama master con pull-request desde este repositorio al repositorio en la primera cuenta, del que copiamos este Fork. Aceptamos el pull-request y lo integramos en el repositorio en GitHub en la primera cuenta.

## Tareas a realizar

### Paso 1: Copiar repositorio

Primero vamos a copiar el repositorio [https://github.com/ging-moocs/MOOC_git_mod7-cal_2com](https://github.com/ging-moocs/MOOC_git_mod7-cal_2com) en su cuenta de GitHub usando el botón de Fork.

### Paso 2: Copiar repositorio desde una segunda cuenta

A continuación, creamos una segunda cuenta (<tu_cuenta_2>) en GitHub y copiamos el repositorio de la primera cuenta (https://github.com/<tu_cuenta>/MOOC_git_mod7-cal_2com) en esta segunda cuenta usando el botón de Fork. El nombre de esta cuenta puede ser cualquiera que desees.

### Paso 3: Clonar el repositorio

Clonamos el repositorio <tu_cuenta_2>/MOOC_git_mod7-cal_2com (de cuenta en GitHub) en nuestro ordenador local.

```
$ git clone git@github.com:<tu_cuenta_2>/MOOC_git_mod7-cal_2com
```

### Paso 4: Añadir cambios 

Entramos en el directorio de trabajo del nuevo repositorio clonado y añadir al fichero calculator.html, al principio del bloque &lt;body&gt; de HTML, un título &lt;h1&gt; con su nombre y apellidos. 

```
$ cd MOOC_git_mod7-cal_2com 
```
Creamos un nuevo commit "Título con autor" con esta modificación.

```
$ git add calculator.html
$ git commit -m "Título con autor"
```

### Paso 5: Copiar rama remota

Copiamos la rama remota inverse del repositorio [https://github.com/ging-moocs/MOOC_git_mod7-cal_branches](https://github.com/ging-moocs/MOOC_git_mod7-cal_branches) como una rama local con git fetch y la refspec correspondiente utilizando el comando: git fetch ..…

```
$ git fetch git@github.com:ging-moocs/MOOC_git_mod7-cal_branches inverse:inverse
```
Podemos comprobar que la rama "inverse" está disponible en local con el comando siguiente:
```
$ git branch -v
```

### Paso 6: Integrar la rama "inverse" en "master"

A continuación vamos a integrar en la rama "inverse", copiada en el repositorio local, la rama "master" con (git merge) e identificamos el nuevo commit con el mensaje "Integrar inverse y master". 

Primero nos cambiamos a la rama "inverse"

```
$ git checkout inverse
```

A continuación integramos la rama "master" en "inverse"

```
$ git merge -m "Integrar inverse y master" master
```

Al hacer la integración surgirán conflictos que debemos resolver manualmente con el editor de texto. La integración debe incorporar el título y los dos botones x^2 y 1/x. Una vez resueltos los conflictos añadimos los ficheros modificados al commit y continuamos con el proceso de integración

```
$ git add .
$ git merge --continue
```

Podemos comprobar el grafo de commits con el siguiente comando:

```
$ git log --graph
```
### Paso 8: Integrar "inverse" en "master"

Integramos en "master" la rama "inverse" del repositorio local (integrada en el paso anterior) con git merge también. Primero tenemos que cambiarnos a la rama "master".

```
$ git checkoutmaster
$ git merge inverse
```


### Paso 8: Subir los cambios a Github

Subimos al repositorio origin (origen de la clonación en la segunda cuenta) las dos ramas locales ("master" e "inverse") con git push.

```
git push --all 
```

### Paso 9: Crear Pull Request

A continuación, enviamos un Pull Request de la rama master desde el repositorio MOOC_git_mod7-cal_2com de la segunda cuenta al repositorio MOOC_git_mod7-cal_2com de la primera cuenta.

Se deben utilizar las facilidades de GitHub para enviar un Pull Request, porque es la única forma de hacerlo.

### Paso 10: Aceptar Pull Request

Por último, aceptamo el Pull Request desde la primera cuenta. Github permite aceptar el merge asociado a un Pull Request directamente en Github.  

También se puede clonar el repositorio de la primera cuenta en local. Descargar la rama master asociada al pull-request con "git fetch …" e integrarla en la rama master del repositorio local. Volver a subir la rama master ya integrada al repositorio en la primera cuenta.

Utilizar los comandos ya vistos en los pasos anteriores y en las transparencias. 



## Descargar el código del proyecto

El proyecto debe clonarse en el ordenador desde el que se está trabajando:

```
$ git clone git@github.com:ging-moocs/MOOC_git_mod7-pr_entrega
```
A continuación se debe acceder al directorio de trabajo y abrir el fichero index.html con el editor de la elección del alumno.

```
$ cd MOOC_git_mod7-pr_entrega
```
## Prueba de la práctica 

Para ayudar al desarrollo, se provee una herramienta de autocorrección que prueba las distintas funcionalidades que se piden en el enunciado. Para utilizar esta herramienta debes tener node.js (y npm) ([https://nodejs.org/es/](https://nodejs.org/es/)) y Git instalados. Primero ejecute los siguientes comandos **en un directorio diferente al de la práctica**:

```
$ git clone git@github.com:ging-moocs/MOOC_git_mod7-pr_entrega
$ cd MOOC_git_mod7-pr_entrega
$ npm install
```

A continuación, en el directorio `MOOC_git_mod7-pr_entrega`, guarde en un fichero llamado 'git_account' tu nombre de usuario de GitHub

```
echo "mi_nombre_de_usuario_en_github" >> git_account
```

y en otro llamado 'git_account2' el nombre del usuario o organización creado para esta entrega

```
echo "mi_2_nombre_de_usuario_en_github" >> git_account2
```


Existe [una presentación](https://docs.google.com/presentation/d/e/2PACX-1vRYA9npW0Xg_c6_SWg2jAU7L2ti83-GY1VYKTzM1U5AgsW-0BC3xbwi__gsrsZ50Md0ja2HyadNzEPn/pub?start=false&loop=false&delayms=5000&slide=id.gf07f9a5896_4_1897) al principio del curso sobre cómo trabajar con el autocorector y poder corregir las prácticas con facilidad. Consulta esa presentación si tienes alguna duda.
Para instalar y hacer uso de la herramienta de autocorrección en el ordenador local, ejecuta los siguientes comandos en el directorio del proyecto:

```
$ npx autocorector                    ## Pasa los tests al fichero a entregar
............................      ## en el directorio de trabajo
... (resultado de los tests)
```

Se puede pasar la herramienta de autoorrección tantas veces como se desee sin ninguna repercusión en la calificación.

## Instrucciones para la Entrega y Evaluación.

Una vez satisfecho con su calificación, el alumno puede subir su entrega con el siguiente comando:
```
$ npx autocorector --upload
```

**RÚBRICA:** La resolución de cada uno de estos puntos dará un el % indicado de la nota total: 
*	**10%**:  Existe el repositorio "MOOC_git_mod7-cal_2com" en cuenta 2
*	**10%**:  Existe el repositorio "MOOC_git_mod7-cal_2com" en cuenta 1 y es el origen del Fork del repo de cuenta 2
*	**10%**:  La rama master del repo de cuenta 2 tiene como tercer commit "Título con autor"
*	**10%**:  El repo de cuenta 2 tiene una rama inverse integrada con master
*	**10%**:  La rama master del repo de cuenta 2 tiene como último commit "1/x button"
*	**20%**:  Que el fichero calculator.html de este último commit funciona, tiene el título requerido y los botones x^2 y 1/x
*	**30%**:  Que el repositorio MOOC_git_mod7-cal_2com en cuenta_1 tiene una rama master con los mismos commits de master del repo MOOC_git_mod7-cal_2com de cuenta 2


