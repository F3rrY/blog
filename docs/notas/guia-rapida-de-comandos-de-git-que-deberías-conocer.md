---
title: Guía rápida de comandos de Git que deberías conocer
parent: Notas
nav_order: 1
---

## Guía rápida de comandos de Git que deberías conocer

{: .highlight }
Vaya por delante que este es un post **vivo**, es decir, lo iré actualizando en función de las necesidades y los comandos que vaya utilizando. Tampoco pretendo poner todos y cada uno de los comandos existentes, sino más bien quiero que sea una guía con aquellos comandos más útiles y situaciones que nos podemos ir encontrando en el día a día. Te animo a que, si crees que falta alguno, lo comentes en las redes en la publicación que haga en las redes o en mi correo electrónico. En la [página principal][HomeUrl] tenéis los datos de contacto.

Todos los que nos dedicamos al mundo del desarrollo, sabemos lo importante que es tener un sistema de control de versiones para ir guardando los cambios que se van haciendo conforme vas desarrollando el proyecto. No solo nos sirve para tener una trazabilidad de todos los cambios que se han ido haciendo (tanto a ti como los miembros del equipo), sino que es un seguro para poder evitar desastres y poder volver a una versión anterior si algo falla. Y, de todos los que hay (SVN Tortoise, Mercurial, etc.), sin duda alguna **Git** es el más popular y extendido entre el mundo del desarrollo de software.

Va a ser un post orientado a todos los niveles, ya sea para iniciados como para usuarios avanzados. Además, en cada comando haré una explicación y un ejemplo para que sea más ilustrativo.

### git init

Git init es el comando que se utiliza para **crear un nuevo repositorio** de Git. Cuando hacemos `git init`, se crea un nuevo directorio oculto llamado `.git` en el directorio actual, que contiene todos los archivos necesarios para gestionar el repositorio.

```
git init nombre-del-repositorio
```

### git add

git add es un comando utilizado para **añadir archivos** al `stage`, que es la zona donde están los archivos antes de hacer un commit. Cuando hacemos `git add`, estamos diciendo a Git que queremos incluir esos archivos en el próximo commit, pero sin hacer el commit. Aquí es importante indicar que no siempre suben cambios en el repositorio, ya que con git add, puedes añadir archivos (o carpetas) **aunque estos no hayan sufrido cambios**.

Este ejemplo añade a la rama un archivo o carpeta al stage
```
git add nombre-del-archivo-o-carpeta
```

### git clone

Git clone es un comando utilizado para **clonar un repositorio remoto** en tu máquina local. Cuando hacemos `git clone`, lo que estamos haciendo es crear una copia exacta del repositorio remoto en nuestro equipo, incluyendo todos los archivos, ramas e historial de commits. Este comando es muy útil cuando por ejemplo te incorporas a un equipo de un entorno empresarial y necesitas descargar el proyecto en tu máquina local y empezar a trabajar.

Este ejemplo clona un repositorio remoto en tu máquina local
```
git clone 
```

Además, puedes especificar el nombre de la carpeta donde quieres que se guarde el proyecto (si no lo haces, se guardará con el nombre del repositorio).
```
git clone url-del-repositorio nombre-de-la-carpeta
```

También puedes clonar una rama específica del repositorio remoto (en lugar de clonar todo el repositorio).
```
git clone -b nombre-de-la-rama url-del-repositorio
```

### git branch

Git branch es un comando utilizado para **listar, crear o eliminar** las ramas de un repositorio de Git. Este comando es realmente útil cuando trabajas en equipo, ya que permite que cada grupo de trabajo modifique el proyecto en ramas independientes sin afectar a la rama principal. Entonces, una vez se han hechos los cambios, pueden fusionar (merge) su rama con la rama principal para que se actualice con los cambios realizados. De hecho, esta es la forma óptima de trabajar en entornos empresariales, y os encontraréis con ramas de todo tipo: ramas de nuevos desarrollos (features), ramas de corrección de errores (bugfix), ramas de pruebas (testing), etc.

En este ejemplo, se listan todas las ramas del repositorio local
```
git branch
```

Si quieres ver todas las ramas del repositorio remoto, puedes usar la opción `-r` (remote)
```
git branch -r
```

Si quieres ver todas las ramas, incluidas las que están en el repositorio remoto, puedes usar la opción `-a` (all)
```
git branch -a
```

En este ejemplo, se crea una nueva rama llamada "feature/crud-entidades"
```
git branch feature/crud-entidades
```

Y si quieres eliminar una rama que ya no necesitas, añades la opción `-d` (delete) y el nombre de la rama. Ojo, para eliminar la rama, no puedes estar en ella, tienes que estar en otra rama. En este ejemplo, se elimina la rama llamada "feature/crud-entidades"
```
git branch -d feature/crud-entidades
```


### git checkout

Git checkout es un comando utilizado para **cambiar de rama** o **restaurar archivos** en un repositorio de Git. Imaginad que hemos terminado el desarrollo de la rama anterior (feature/crud-entidades) y estamos en otra rama haciendo otra cosa, y recibimos un aviso de que el departamento de testing ha encontrado un caso de uso no contemplado. Pues necesitamos ir a la rama anterior para poder desarrollar el caso de uso. Y para ello, haríamos `git checkout`. Es importante tener en cuenta que, al cambiar de rama, cualquier cambio no guardado en la rama actual se perderá, por lo que siempre recomendable hacer un `commit` (o un `stash`) antes de cambiar de rama.

En este ejemplo cambiamos a la rama llamada "feature/crud-entidades"
```
git checkout feature/crud-entidades
```

{: .highlight }
Hay un comando que sirve para crear la rama y entrar en ella directamente, que es `git checkout -b nombre-de-la-rama`. Este comando crea la rama y automáticamente pasa a ser el área de trabajo. Lo comento porqué muchos lo desconocen y, para crear una rama nueva y luego entrar en ella hacen dos comandos: `git branch nombre-de-la-rama` y luego `git checkout nombre-de-la-rama`. Pues con `git checkout -b nombre-de-la-rama`, haces todo en un solo comando.


### git status

Git status es un comando utilizado para **ver el estado actual del repositorio**. Cuando hacemos `git status`, nos muestra información sobre:
- qué archivos han sido modificados
- qué archivos están en el stage
- qué archivos son nuevos que todavía no se han añadido al stage

La verdad que es un comando muy útil para saber qué cambios se han hecho en el repositorio y qué archivos están listos para subir en el próximo `commit`.

Este ejemplo muestra el estado actual del repositorio
```
git status
```

### git commit

Git commit es un comando utilizado para **guardar los cambios realizados en tu repositorio local** (importante, los archivos siguen en local, no están en el repositorio). Cuando hacemos `git commit`, lo que estamos haciendo es decir: Ok, pues estos ficheros están bien y pueden subir, y entonces se crea un checkpoint en la rama con los ficheros; pero insisto, los ficheros aún no han subido en el repositorio, sino que están ahí guardados pero pendientes de subir (para ello usaremos el siguiente comando de la lista). Cada commit tiene un único identificador, nunca puede haber dos commits con el mismo ID. Además, el parámetro `-m` permite escribir un título (que ha de ser el titular, sin entrar en detalles) para describir los cambios realizados.

Este ejemplo hace un commit con el mensaje "Añadir nombre a la entidad"
```
git commit -m "Añadir nombre a la entidad"
```

### git pull

Git pull es un comando utilizado para **actualizar tu repositorio local con los cambios realizados en el repositorio remoto**. Cuando hacemos `git pull`, lo que estamos haciendo es descargar los cambios que se ha hecho en el repositorio remoto y fusionarlos con nuestra rama actual en el repositorio local. Es importante hacer un `git pull` antes de empezar a trabajar en una rama, para asegurarnos de que tenemos la versión más reciente del código y evitar conflictos al hacer un `push` más adelante.


### git push

Git push es un comando utilizado para **subir los cambios guardados en tus commits que tienes en tu repositorio local al repositorio definitivo**. Cuando hacemos `git push`, todos los cambios que teníamos guardados en los commits previos en repositorio local se suben y se guardan en nuestro repositorio remoto. **Atención** ya que es importante indicar que para poder hacer un push, **primero hay que hacer un commit** (ya que si no, no hay nada que subir, lógicamente). Además, si es la primera vez que haces un push a un repositorio remoto, tendrás que especificar el nombre del repositorio remoto y la rama a la que quieres subir los cambios.

Este ejemplo hace un push a la rama main del repositorio.
```
git push origin main
```

{: .highlight }
Por cierto, el nombre `origin` es el nombre por defecto que Git asigna al repositorio remoto cuando clonas un repositorio en tu máquina local. Además, `main` es el nombre por defecto de la rama principal en muchos repositorios (antes era `master`, pero ahora se está cambiando a `main` en muchos casos).

### git merge

Git merge es un comando utilizado para **fusionar dos ramas** en un repositorio de Git. Cuando hacemos `git merge`, lo que estamos haciendo es combinar los cambios realizados en una rama con otra rama. Para ello, primero tendremos que ir a la rama de destino (donde quieres que se fusionen los cambios) mediante `git checkout nombre-de-la-rama` y luego aplicar el git merge. Este comando es muy útil cuando hemos terminado de trabajar en una rama y queremos integrar los cambios realizados en la rama principal.

Es importante tener en cuenta que al hacer un merge, **pueden surgir conflictos** si los mismos archivos han sido modificados en las dos ramas. En ese caso, tendremos que resolver los conflictos manualmente antes de poder completar el merge.

Si por ejemplo hemos terminado nuestro desarrollo del crud de entidades y queremos integrarlo en la rama principal, tendremos que ir a la rama principal con el siguiente comando:
```
git checkout main
```
Y luego hacer el merge de la rama "feature/crud-entidades"
```
git merge feature/crud-entidades
```

### Conflictos

Un conflicto ocurre cuando dos (o varias) personas han hecho cambios en la misma línea (o bloque) de código de un mismo archivo y han subido los cambios al repositorio remoto. Obviamente, el repositorio no sabe cuáles son los cambios que han de conservarse, con lo que, te avisa de que hay un conflicto y que debe ser resuelto.

Para resolver un conflicto, hay que abrir el archivo en cuestión y buscar las líneas marcadas con `<<<<<<<`, `=======` y `>>>>>>>`  Estas líneas indican las partes del código que han sido modificadas por cada persona. Entonces, hay que decidir cuáles son los cambios que se quieren conservar y eliminar estas líneas de conflicto. Una vez resuelto, se guardan los cambios en tu repositorio local con `git commit` y finalmente se hace `git push` para subir los cambios al repositorio remoto.

Se pueden evitar los conflictos? Naturalmente, pero para ello se necesita una buena disciplina de trabajo en equipo y que cada uno sepa qué ficheros tocar sin que "moleste" a nadie. Normalmente, si queréis ahorraros problemas de conflictos antes de subir los cambios al repositorio remoto con `git push`, siempre es recomendable el siguiente orden:
1. `git commit` (para guardar los cambios en tu repositorio local)

```
git commit -m "Últimos cambios entidad"
```

2. `git pull` de la rama de destino (para obtener los últimos cambios del repositorio remoto)
```
git pull origin main
```

3. Mergear los cambios con `git merge` de la rama de destino (main) en tu rama actual (feature/crud-entidades) para asegurarte de que tienes la versión más reciente del código y evitar conflictos al hacer el push más adelante.
```
git checkout feature/crud-entidades
git merge main
```
En este punto, si hay conflictos, ya te saldrá la alerta y tendrás que resolverlos. Obviamente, si hay conflictos, no se debe hacer `git push` hasta que no estén resueltos.

4. Si todo es correcto, ya puedes hacer `git push` para subir los cambios al repositorio remoto con la garantía de que no habrá conflictos.
```
git push origin main
```

### git log

Git log es un comando utilizado para **ver el historial de commits** en un repositorio de Git. Cuando hacemos `git log`, nos muestra una lista de todos los commits realizados en el repositorio, junto con información como el autor, la fecha y el mensaje del commit. Este comando es muy útil para revisar los cambios realizados en el proyecto y para encontrar un commit específico si necesitamos volver a una versión anterior del código.

Este ejemplo muestra el historial de commits en el repositorio
```
git log
```

Si quieres ver el historial de commits de una rama específica, puedes usar la opción `nombre-de-la-rama` para filtrar los commits por esa rama.
```
git log nombre-de-la-rama
```

Hay varias opciones para ver el log, por ejemplo, si queremos ver un log más compacto, podemos usar la opción `--oneline`, que muestra cada commit en una sola línea con su identificador y mensaje.
```
git log --oneline
```

Además, si quiers ver un log gráfico que muestre las ramas y los merges, puedes usar la opción `--graph`.
```
git log --graph --oneline --all
```


[HomeUrl]: https://ferranm.net