# 3. Operaciones básicas con Git

- [Realización de commits y revert](#realización-de-commits-y-revert)
- [Trabajo con ramas (branching)](#trabajo-con-ramas-branching)
- [Resolución de conflictos en merges](#resolución-de-conflictos-en-merges)

## Realización de Commits y Revert

Un commit en Git es una captura del estado actual de los archivos en un repositorio.

Se utiliza para registrar los cambios realizados en el proyecto con un mensaje descriptivo.

### Hacer un Commit

1. Agregar los archivos al área de preparación:

   ```bash
   git add <archivo>
   ```
   o para añadir todos los cambios:

   ```bash
   git add .
   ```
2. Crear un commit con un mensaje:

   ```bash
   git commit -m "Mensaje descriptivo del cambio"
   ```

### Revertir un Commit

Si es necesario deshacer un commit:

- Para crear un nuevo commit que revierta los cambios de uno anterior:

  ```bash
  git revert <ID_DEL_COMMIT>
  ```
- Para deshacer el último commit sin borrar los cambios:

  ```bash
  git reset --soft HEAD~1
  ```
- Para eliminar completamente el último commit y los cambios asociados:

  ```bash
  git reset --hard HEAD~1
  ```

## Trabajo con Ramas (Branching)

Las ramas permiten desarrollar nuevas características sin afectar la versión principal del proyecto.

### Crear y Cambiar de Rama

1. Crear una nueva rama:

   ```bash
   git branch <nombre_de_rama>
   ```
2. Cambiar a la nueva rama:

   ```bash
   git checkout <nombre_de_rama>
   ```
   o con el comando combinado:

   ```bash
   git checkout -b <nombre_de_rama>
   ```

### Fusionar Ramas (Merge)

Para fusionar los cambios de una rama en otra:

```bash
git checkout main
git merge <nombre_de_rama>
```

## Resolución de Conflictos en Merges

Cuando Git no puede fusionar automáticamente los cambios, se genera un conflicto.

### Identificar Conflictos

Después de un merge fallido, Git marca los archivos con conflictos. Para verlos:

```bash
git status
```

### Resolver Conflictos

1. Editar manualmente los archivos afectados.
2. Eliminar los marcadores de conflicto (`<<<<<<<`, `=======`, `>>>>>>>`).
3. Agregar los archivos corregidos:

   ```bash
   git add <archivo>
   ```
4. Finalizar el merge con un commit:

   ```bash
   git commit -m "Conflictos resueltos"
   ```

## Recursos y referencias

- [Git Gud](https://nic-hartley.github.io/git-gud/)
- [Learn Git Branching](https://learngitbranching.js.org/?locale=es_ES)
- [Visualizing Git](https://git-school.github.io/visualizing-git/)
- [Explain Git with D3](https://onlywei.github.io/explain-git-with-d3/)
- [Git reset y revert (freecodecamp)](https://www.freecodecamp.org/espanol/news/la-guia-definitiva-para-git-reset-y-git-revert/)
