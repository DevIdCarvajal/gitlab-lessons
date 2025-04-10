# 6. Buenas prácticas y resolución de problemas

- [Estrategias para un historial limpio y ordenado](#estrategias-para-un-historial-limpio-y-ordenado)
- [Manejo de errores comunes en Git](#manejo-de-errores-comunes-en-git)
- [Consejos para colaborar en proyectos grandes](#consejos-para-colaborar-en-proyectos-grandes)

## Estrategias para un historial limpio y ordenado

A medida que los proyectos crecen y más personas colaboran en ellos, es fundamental seguir buenas prácticas para mantener un historial limpio y facilitar el trabajo en equipo.

Un historial de commits bien estructurado facilita la revisión de código, la depuración y la colaboración. Algunas estrategias clave incluyen:

### 1. Escribir mensajes de commit claros y significativos

- Un buen mensaje de commit debe describir **qué se ha cambiado y por qué**.
- Formato recomendado:

  ```
  Tipo del cambio: Breve descripción (50 caracteres máx.)
  
  Explicación opcional en detalle si es necesario (máx. 72 caracteres por línea).
  ```
  Ejemplo:

  ```
  fix: corregido bug en la validación de formulario
  
  Se solucionó un error en la función validateForm() que impedía el envío
  del formulario cuando se introducían caracteres especiales.
  ```

### 2. Hacer commits pequeños y con un solo propósito

- Evitar mezclar múltiples cambios en un solo commit.
- Esto facilita la reversión y comprensión del historial.

### 3. Usar rebase en lugar de merge cuando sea posible

- `git rebase` permite mantener un historial más lineal eliminando commits de fusión innecesarios.
- Uso recomendado para actualizar ramas de trabajo:

  ```bash
  git checkout feature-branch
  git rebase main
  ```
- No debe usarse en ramas compartidas por varios desarrolladores.

### 4. Limpiar el historial con git commit --amend y git rebase -i

- **Modificar el último commit** si se olvidó incluir un archivo o mejorar el mensaje:

  ```bash
  git commit --amend
  ```
- **Fusionar y reordenar commits** interactivamente:

  ```bash
  git rebase -i HEAD~3
  ```
  *(Esto abre una lista de los últimos 3 commits para editarlos antes de subirlos a remoto.)*

## Manejo de errores comunes en Git

Incluso los desarrolladores más experimentados se encuentran con problemas en Git, así que también es importante saber cómo manejar errores comunes para evitar problemas mayores.

Aquí se presentan soluciones a algunos de estos errores frecuentes:

### 1. Se olvidó añadir un archivo al último commit

Si aún no se ha hecho `push`:

```bash
git add file.txt
git commit --amend --no-edit
```
*(Esto añade el archivo al último commit sin cambiar su mensaje.)*

Si ya se hizo `push`, puede usarse `--force-with-lease` con precaución:

```bash
git push --force-with-lease
```

### 2. Se hizo commit en la rama equivocada

Si aún no se han subido los cambios:

```bash
git checkout right-branch
git cherry-pick <ID_DEL_COMMIT>
git checkout wrong-branch
git reset --hard HEAD~1
```
*(Esto mueve el commit a la rama correcta y elimina el de la incorrecta.)*

### 3. Se quiere deshacer un `git add` antes de hacer commit

```bash
git reset HEAD <file>
```
*(Esto saca el archivo del área de staging sin borrar los cambios.)*

### 4. Cómo recuperar un archivo eliminado con Git

Si se eliminó un archivo por error y aún no se hizo commit:

```bash
git checkout -- <file>
```
Si ya se hizo commit y se quiere recuperar:

```bash
git log -- <file>
git checkout <ID_DEL_COMMIT> -- <file>
```

### 5. Cómo deshacer un merge antes del commit

Si se ejecutó `git merge` pero aún no se hizo commit:

```bash
git merge --abort
```
Si ya se hizo commit y se quiere deshacer:

```bash
git reset --hard HEAD~1
```

## Consejos para colaborar en proyectos grandes

En equipos grandes, la coordinación es clave para evitar conflictos y mejorar la productividad. Aquí se presentan algunos consejos:

### 1. Seguir una estrategia de ramas bien definida

- **Git Flow**: Usar ramas como `develop`, `feature/*`, `release/*`, `hotfix/*`.
- **GitHub/GitLab Flow**: Uso de `main` y ramas de feature con `merge requests`.

### 2. Sincronizar frecuentemente con la rama principal

Antes de hacer un `push`, asegurarse de que la rama de trabajo está actualizada:

```bash
git fetch origin
git rebase origin/main
```
*(Esto evita conflictos y mantiene el historial limpio.)*

### 3. Revisar el código con Merge Requests antes de fusionar cambios

- Pedir revisiones de código en GitLab para mejorar la calidad.
- Usar `git diff` para verificar cambios antes de subirlos:
  ```bash
  git diff
  ```

### 4. Resolver conflictos de manera organizada

Si hay un conflicto en un `merge` o `rebase`:
- Usar `git status` para identificar archivos en conflicto.
- Editar los archivos y eliminar los marcadores (`<<<<<<<`, `=======`, `>>>>>>>`).
- Agregar los cambios y finalizar el merge:

  ```bash
  git add .
  git commit -m "Resolver conflictos en archivo.txt"
  ```

### 5. Evitar commits con información sensible

Antes de hacer `push`, revisar si se han incluido credenciales o datos privados:

```bash
git diff --staged | grep "password"
```
Si se subió algo sensible, eliminarlo del historial con:

```bash
git filter-branch --force --index-filter \
'git rm --cached --ignore-unmatch sensitive_file.txt' \
--prune-empty --tag-name-filter cat -- --all
git push origin --force --all
```
*(Debe tenerse en cuenta que esto reescribe el historial y puede causar problemas en equipos grandes.)*
