# Soluciones

## Ejercicio 1: Configuración Inicial de Git

1. Configura tu nombre y correo en Git:

   ```bash
   git config --global user.name "Tu Nombre"
   git config --global user.email "tuemail@example.com"
   ```
2. Verifica la configuración con:

   ```bash
   git config --list
   ```

## Ejercicio 2: Creación y Clonación de Repositorios

1. Crea un nuevo repositorio en GitLab.
2. Clónalo en tu equipo con:

   ```bash
   git clone <URL_DEL_REPOSITORIO>
   ```

## Ejercicio 3: Inicialización y Vinculación de un Repositorio Local

1. Crea una carpeta y navega a ella:

   ```bash
   mkdir mi_repositorio && cd mi_repositorio
   ```
2. Inicializa un repositorio local:

   ```bash
   git init
   ```
3. Conéctalo a GitLab:

   ```bash
   git remote add origin <URL_DEL_REPOSITORIO>
   ```

## Ejercicio 4: Primeros Commits

1. Crea un archivo `README.md` con una breve descripción del proyecto.
2. Añádelo al repositorio y realiza un commit:

   ```bash
   git add README.md
   git commit -m "Añadir README inicial"
   ```
3. Sube los cambios a GitLab:

   ```bash
   git push -u origin main
   ```
