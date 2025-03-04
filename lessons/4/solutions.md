# Soluciones

## Ejercicio 1: Creación de una rama y realización de una Merge Request

1. Clona el repositorio en tu máquina local (si no lo tienes ya):

   ```bash
   git clone <URL_DEL_REPOSITORIO>
   cd <nombre_del_repositorio>
   ```
2. Crea una nueva rama para una nueva funcionalidad:

   ```bash
   git checkout -b feature/new-feature
   ```
3. Crea un archivo nuevo `new_feature.txt` y agrega algún contenido.
4. Añade los cambios al área de preparación y haz un commit:

   ```bash
   git add new_feature.txt
   git commit -m "Añadir nueva funcionalidad"
   ```
5. Sube la rama a GitLab:

   ```bash
   git push origin feature/new-feature
   ```
6. Entra en GitLab y abre una Merge Request desde `feature/new-feature` hacia `main`.
7. Asigna la Merge Request a un compañero para su revisión.
8. Una vez aprobada, fusiónala con `main`.
9. Finalmente, elimina la rama en local y en remoto:
   ```bash
   git branch -d feature/new-feature
   git push origin --delete feature/new-feature
   ```

## Ejercicio 2: Revisión de código en una Merge Request

1. Un compañero creará una Merge Request.
2. Accede a la sección *Merge Requests* en GitLab.
3. Revisa los cambios en la pestaña *Changes*.
4. Comenta cualquier mejora en el código.
5. Si todo está correcto, aprueba la Merge Request.
6. Fusiona la Merge Request con la rama principal.

## Ejercicio 3: Creación y gestión de Issues

1. Entra en la sección *Issues* en GitLab.
2. Crea un nuevo Issue con un título claro y descripción detallada.
3. Asigna el Issue a un compañero y añade una etiqueta: `bug`, `functionality`, etc.
4. Resuelve el Issue en una nueva rama (`fix/nombre_del_issue`).
5. Sube los cambios y abre una Merge Request con la referencia `Closes #<número_del_issue>`.
6. Fusiona la Merge Request y verifica que el Issue se cierra automáticamente.
