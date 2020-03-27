# git

## Comandos Básicos

### Comandos Iniciales

#### Configurar git

Configurar username:

```shell
git config --global user.name "Username"
```

Configurar mail:

```shell
git config --global user.mail "mail@mail.com"
```

Ver configuraciones

```shell
git config --global -l
```



#### Iniciar git

```shell
git init
```



#### Ver la situación del proyecto

```shell
git status
```



#### Agregar todos los archivos pendientes al stage

```shell
git add .
```

```shell
git add --all
```

```shell
git add A
```



#### Confirmar cambios y agregar al branch

```shell
git commit -m "Message"
```



#### Ver modificaciones desde el último commit

```shell
git diff
```



#### Regresar al último commit

``` shell
git checkout .
```



#### Ver historial de commits

```shell
git log
```

-- o -- 

```sh
git log --oneline
```



#### Agregar al stage un único archivo

```shell
git add file.txt
```



#### Remover del stage un archivo

```shell
git reset file.txt
```



#### Remover del stage un tipo de archivo

```shell
git reset *.txt
```



### Comandos útiles

#### Establecer alias ("atajos") en git para escribir menos

```shell
git config --global alias.l "command"
```

Por ejemplo:

```shell
git config --global alias.l "log"
```

En este caso, al escribir

```shell
git l
```

sería el equivalente a 

```shell
git log
```



#### Corregir mensaje de commit anterior

```shell
git commit --amend -m "Corrección del mensaje"
```



#### Cambiar nombre a un archivo, guardando el registro

```shell
git mv nombre-original.txt nombre-modificado.txt
```



#### Eliminar archivos, guardando el registro

```shell
git rm archivo.txt
```



##### Regresar a un commit específico

```shell
git reset "id del commit"
```

En este caso, se regresa al commit, sin deshacer los cambios que se habían hecho



```shell
git reset -soft "id del commit a regresar"
```



Regresar archivos eliminados

```shell
git reset -hard "id del commit a regresar"
```



#### Ver histórico de todos los cambios en commits

```shell
git reflog
```



## Ignorar archivos en registro

 Para ignorar determinados archivos, se debe de crear un archivo en la carpeta raíz, llamado .gitignore en el que se introduzcan los nombres o extensiones de los archivos a ignorar. 

Por ejemplo:

```
.classpath
.project
/node_modules
.etc
```



## Branches

### FAST FOrWARD

El Fast Forward es el método de manejo de ramas en las que una no causa conflicto sobre la master

#### Crear nueva rama

```shell
git branch nombre_de_rama
```



#### Moverte a ramas

```shell
git checkout nombre_de_rama
```



#### Integrar rama a master

Debemos ubicarnos en la rama master

```shell
git checkout master
```

Y partir de aquí, podemos hacer el merge

```shell
git merge nombre_de_rama_a_combinar
```



#### Eliminar rama

``` shell
git branch -d nombre_de_rama_a_eliminar
```



#### Crear rama y moverte al mismo tiempo

```shell
git checkout -b nombre_de_nueva_rama
```



### Conflictos en Merge

Cuando se presentan conflictos al hacer merge entre ramas, una vez hecho el merge se debe definir la estructura final de hacer un commit



## Tags

#### Crear tag

```shell
git tag nombre_de_tag
```



#### Ver tags activos en branch

```shell
git tag
```



#### Eliminar etiquetas

```shell
git tag -d nombre_de_etiqueta
```



#### Agregar una descripción de la etiqueta

```shell
git tag -a nombre_de_etiqueta -m "Descripción de etiqueta"
```



#### Agregar etiqueta a commit previo

``` shell
git tag -a nombre_de_etiqueta id_de_commit -m "Descripción"
```





