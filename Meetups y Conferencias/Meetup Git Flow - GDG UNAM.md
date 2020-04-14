# Git Flow

Daniel Castillo / Meetup GDG UNAM - 04/03/2020

---

## ¿Qué es Git Flow?

Es un modelo de trabajo para la creación y organización de branches. Nos sirva para tener un guía de organización para tener buenas prácticas en el control de versiones.

- Permite ubicar las diferentes versiones de nuestro software
- Permite dar mantenimiento a diferentes versiones del software
- Maniene organizado el trabajo remoto
- Puedes hacer experimentos sin afectar el código que ya sirve
- Asegura la estabilidad de tu software en producción

## Modelos de Trabajo para Git

### Git Flow (2011)

| Pros                                                         | Contras                                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| El fluio de trabajo más popular                              | El historial de git se vuelve ilegible                       |
| Asegura un estado limpio de las ramas durante su ciclo de vida | La diferencia entre la rama master y develop se considera redundante y digiculta el CD y CI |
| Nombra las ramas de manera sistemática, más fáciles de comprender |                                                              |
| Tiene extensiones y herramientas para CLI                    |                                                              |
| Ideal para mantener múltiples versiones en producción        |                                                              |

## 

### GitHub Flow(2011)

- Ideal si quieres mantener una sola versión en producción
- Para CD y CI



- El código en producción se puede volver inestable fácilmente
- No resuelve algo acerca de los ambientes, versiones e incidentes

| Pros                                                     | Contras                                                      |
| -------------------------------------------------------- | ------------------------------------------------------------ |
| Ideal si quieres mantener una sola versión en producción | El código en producción se puede volver inestable fácilmente |
| Idel para CD y CI                                        | No resuelve algo acerca de los ambientes, versiones e incidentes |




### GitLab Flow (2014)

| Pros                                                         | Contras                                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Combina el desarrollo basado en funcionalidades (FDD) con el segumiento de incidentes | Es más complejo que GitHub Flow                              |
| Acepta proyectos que no pasan a producción al agregar una funcionalidad (SaaS y apps móbiles) | Se puede volver tan complejo como Git Flow cuando das mantenimiento a multiples versiones |
| El historial de Git será más limpio y legible                |                                                              |



### One Flow (2015)

| Pros                                                     | Contras                                                      |
| -------------------------------------------------------- | ------------------------------------------------------------ |
| El historial de git es limpio y fácil de leer            | No es recomendable para proyectos con CI/CD                  |
| Es flexible de acuerdo a las desiciones del equipo       | No es recomendable cuando necesitas más de una versión en producción |
| Es bueno cuando necesitas una sola versión en producción |                                                              |



## Configuración de Git Flow

*git-flow (AVH edition)*

**Para Mac OS:**

```shell
brew install git-flow-avh
```

o bien

```shell
wget --no-check-certificate -q -O -https://github.com/petervanderdoes/gitflow-avh/raw/develop/contrib/gitflow-installer.sh install stable | sudo bash
```

**Para Linux:**

```shell
sudo apt install git-flow
```

**Para Windows:**

```shell
wget -q -O --no-check-certificate https://raw.github.com/petervanderdoes/gitflow-avh/develop/contrib/gitflow-installer.sh install stable | bash
```



## Inicialización de Git Flow

**Usando git flow:**

```shell
git flow init
```

**Usando git:**

```shell
git branch develop
git push -u origin develop
```



**Git Flow comienza con 2 ramas principales:**

- `master`: contiene el código del software en producción
- `develop`: contiene los últimos cambios de desarrollo en el código (rama de integración). Cuando el código alcanza un punto estable, pasa al master con un merge y tag

## Ramas de soporte

Las ramas de soporte son ramas de apoyo y de tiempo de vida limitado, entre sus ventajas están:

- Programación paralela en un equipo de trabajo
- Seguimiento de nuevas funcionalidades
- Preparar un nuevo lanzamiento para producción
- Arreglar rápidamente problemas de producción en vivo

### Rama `feature`

**Creada desde:** `develop`

**Regresa a:** `develop`

**Convención de nombre:** todo menos `master`, `develop`, `release-*`, `hotfix-*` o `bugfix-*`

- Usadas para desarrollar nuevas funcionalidades para un nuevo lanzamiento
- Puede ser lanzada a un repo remoto para respaldo/colaboración
- Es independiente de la versión del lanzamiento en la que nos encontremos

#### Iniciar `feature`

**Usando  git flow:**

```shell
git flow feature start feature_branch
```

**Usando git:**

```shell
git checkout develop
git checkout -b feature_branch
```

#### Cerrar `feature`

**Usando git flow:**

```shell
git flow feature finish feature_branch
git push origin develop
```

**Usando git:**

```shell
git checkout develop
git merge --no-ff feature_branch
git branch -d feature_branch
git push origin develop
```



### Rama `release`

**Creada desde:** `develop`

**Regresa a:** `develop` y `master`

**Convención de nombre:** `release-*`, `release/*`

#### Iniciar `release`

**Usando git flow:**

```shell
git flow release start 0.1.0 #versión del release
```

**Usando git:**

```shell
git checkout develop
git checkout -b release/0.1.0 #versión del release
```

#### Cerrar `release`

**Usando git flow:**

```shell
git flow release finish 0.1.0 # versión del release
git push origin master
git push origin develop
```

**Usando git:**

```shell
git checkout master
git merge --no-ff release/0.1.0 # versión del release
git tag -a 0.1.0
git checkout develop
git merge --no-ff release/0.1.0
git branch -d release/0.1.0
git push origin master
git push origin develop
```



### Rama `Hotfix`

**Creada desde:**  `master`

**Regresa a:** `develop` y `master`

**Convención de nombre:** `hotfix-*`, `hotfix/*`

- Parecido a las ramas `release`, pero sin planear
- Corrigen errores no esperados que surgen en producción y necesitan corregirse urgentemente
- Es la única rama que surge de `master`
- Tan pronto como se corriga, debe de mezclarse con `master` y `develop` (o la rama `release` actual).

#### Iniciar `hotfix`

**Usando git flow:**

```shell
git flow hotfix start hotfix_branch
```

**Usando git:**

```shell
git checkout master
git checkout -b hotfix_branch
```

#### Cerrar `hotfix`

**Usando git flow:**

```shell
git flow hotfix finish hotfix_branch
git push origin master
git push origin develop
```

**Usando git:**

```shell
git checkout master
git merge --no-ff hotfix_branch
git tag -a 1.2.1 # versión del tag
git checkout develop
git merge --no-ff hotfix_branch
git branch -d hotfix_branch
```



### Rama Bugfix

**Creada desde:** `develop `o alguna rama `feature`

**Regresa a:** la rama de dónde salió

**Convención de nombre:** `bugfix-*`, `bugfix/*`

- Sirven para agregar cambios a nuestro código que no tienen que ver con nuevas funcionalidades
- Corrigen problemas previstos antes del lanzamiento
- Una vez finalizada la correción, se mezclan con la rama de donde provienen

#### Iniciar `bugfix`

**Usando git flow:**

```shell
git flow bugfix start bugfix_branch
```

**Usando git:**

```shell
git checkout develop
git checkout -b bugfix_branch
```

#### Cerrar `bugfix`

**Usando git flow:**

```shell
git flow bugfix finish bugfix_branch
git push origin develop
```

**Usando git:**

```shell
git checkout develop
git merge --no-ff bugfix_branch
git push origin develop
```





