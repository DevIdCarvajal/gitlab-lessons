# Ejercicios

## Ejercicio 1: Realización de commits y revert

1. Crea un nuevo archivo `notas.txt` y escribe en él una lista de tareas pendientes.
2. Añádelo al stage y realiza un commit con un mensaje apropiado.
3. Modifica el archivo `notas.txt`, agregando más tareas.
4. Realiza otro commit con un mensaje apropiado.
5. Muestra el historial de commits simplificado (una línea por commit).
6. Revierte el último commit sin perder los cambios en el archivo.
7. Vuelve a confirmar el cambio y súbelo al repositorio.

## Ejercicio 2: Trabajo con ramas (branching)

1. Crea una nueva rama llamada `new-feature`.
2. En esta rama, crea un archivo `feature.txt` y escribe una breve descripción de una nueva característica.
3. Añádelo al stage y realiza un commit.
4. Cambia de vuelta a la rama `main`.
5. Fusiona la rama `new-feature` en `main`.
6. Borra la rama después de fusionarla.

## Ejercicio 3: Resolución de conflictos en merges

1. Crea una nueva rama llamada `changing-readme`.
2. Edita el archivo `README.md` y agrega una línea nueva al final.
3. Realiza un commit con el mensaje "Modificar README en rama changing-readme".
4. Cambia a la rama `main` y edita el mismo archivo `README.md`, pero con un cambio diferente en la misma línea.
5. Realiza un commit en `main` con el mensaje "Modificar README en main".
6. Intenta fusionar `changing-readme` en `main`, resolviendo los posibles conflictos (si los hubiere).
7. Usa `git status` para identificar el archivo en conflicto y edítalo manualmente.
8. Resuelve el conflicto, guarda los cambios y finaliza el merge.

# Proyecto: Moby Git (Día 2) 🐋📝

1. Crear un repositorio remoto privado vacío en GitLab y utilizarlo para subir el cuaderno de bitácora.
2. Crear una rama en local a partir de `main` llamada `first-revision`, modificar alguna de las tres entradas del cuaderno de bitácora y hacer `merge` de esos cambios a `main`.
3. Crear otra rama a partir de `first-revision` llamada `second-revision`, modificar la misma entrada del ejercicio anterior, en la misma línea, hacer `merge` a `main` y resolver el conflicto.
4. Sincronizar todo con el repositorio en GitLab.
