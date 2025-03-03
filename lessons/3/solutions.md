# Soluciones

## Ejercicio 1: Realización de commits y revert

1. Crea un nuevo archivo `notas.txt` y escribe en él una lista de tareas pendientes.
2. Añádelo al stage y realiza un commit con un mensaje apropiado:

   ```bash
   git add notas.txt
   git commit -m "Añadir archivo de notas"
   ```
3. Modifica el archivo `notas.txt`, agregando más tareas.
4. Realiza otro commit con un mensaje apropiado:

   ```bash
   git commit -m "Actualizar lista de tareas"
   ```
5. Usa `git log --oneline` para ver el historial de commits.
6. Revierte el último commit sin perder los cambios en el archivo:

   ```bash
   git reset --soft HEAD~1
   ```
7. Vuelve a confirmar el cambio y súbelo al repositorio.

## Ejercicio 2: Trabajo con ramas (branching)

1. Crea una nueva rama llamada `new-feature`:

   ```bash
   git checkout -b new-feature
   ```
2. En esta rama, crea un archivo `feature.txt` y escribe una breve descripción de una nueva característica.
3. Añádelo al stage y realiza un commit.
4. Cambia de vuelta a la rama `main`:

   ```bash
   git checkout main
   ```
5. Fusiona la rama `new-feature` en `main`:

   ```bash
   git merge new-feature
   ```
6. Borra la rama después de fusionarla:

   ```bash
   git branch -d new-feature
   ```

## Ejercicio 3: Resolución de conflictos en merges

1. Crea una nueva rama llamada `changing-readme`:

   ```bash
   git checkout -b changing-readme
   ```
2. Edita el archivo `README.md` y agrega una línea nueva al final.
3. Realiza un commit con el mensaje "Modificar README en rama changing-readme".
4. Cambia a la rama `main` y edita el mismo archivo `README.md`, pero con un cambio diferente en la misma línea.
5. Realiza un commit en `main` con el mensaje "Modificar README en main".
6. Intenta fusionar `changing-readme` en `main`, resolviendo los posibles conflictos (si los hubiere):

   ```bash
   git merge changing-readme
   ```
7. Usa `git status` para identificar el archivo en conflicto y edítalo manualmente.
8. Resuelve el conflicto, guarda los cambios y finaliza el merge:

   ```bash
   git add README.md
   git commit -m "Resolver conflicto en README"
   ```
