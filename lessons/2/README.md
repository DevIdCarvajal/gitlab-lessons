# 2. Configuración inicial y gestión de repositorios

- [Creación y clonación de repositorios](#creación-y-clonación-de-repositorios)
- [Configuración de SSH y HTTPS](#configuración-de-ssh-y-https)
- [Organización y gestión de proyectos en GitLab](#organización-y-gestión-de-proyectos-en-gitlab)

## Creación y Clonación de Repositorios

Un repositorio en Git es el lugar donde se almacena el historial de cambios de un proyecto.

Se pueden crear repositorios locales o clonar repositorios remotos para trabajar en equipo.

### Creación de un Repositorio Local

Para inicializar un nuevo repositorio en Git:

```bash
git init
```

Esto crea un nuevo repositorio vacío en la carpeta actual.

### Clonación de un Repositorio

Para clonar un repositorio remoto en el equipo local:

```bash
git clone <URL_DEL_REPOSITORIO>
```

Esto descargará una copia del repositorio y permitirá trabajar con él localmente.

## Configuración de SSH y HTTPS

Git permite comunicarse con repositorios remotos mediante dos protocolos: HTTPS y SSH.

### Configuración de HTTPS

Para usar HTTPS, es necesario autenticarse con usuario y contraseña o con un token de acceso personal.

1. Configurar el usuario y correo:

   ```bash
   git config --global user.name "Tu Nombre"
   git config --global user.email "tu_email@example.com"
   ```
2. Al hacer `git push` por primera vez, Git solicitará las credenciales.

### Configuración de SSH

El acceso por SSH permite una autenticación segura sin necesidad de introducir credenciales en cada operación.

1. Generar una clave SSH:

   ```bash
   ssh-keygen -t ed25519 -C "tu_email@example.com"
   ```
2. Agregar la clave SSH a GitLab en `Ajustes > SSH Keys`.
3. Probar la conexión:

   ```bash
   ssh -T git@gitlab.com
   ```

## Organización y Gestión de Proyectos en GitLab

### Creación de un Proyecto en GitLab

1. Iniciar sesión en GitLab y hacer clic en "Nuevo proyecto".
2. Seleccionar "Crear un nuevo proyecto en blanco".
3. Opcionalmente, marcar la casilla "Inicializar repositorio con un README". 
   - Si se marca, se podrá clonar directamente con:

     ```bash
     git clone <URL_DEL_REPOSITORIO>
     ```
   - Si no se marca, se deberá inicializar el repositorio localmente y enlazarlo con GitLab:

     ```bash
     git init
     git remote add origin <URL_DEL_REPOSITORIO>
     git add .
     git commit -m "Primer commit"
     git push -u origin main
     ```
4. Elegir visibilidad y configuración del repositorio.

### Gestión de Permisos y Colaboradores

GitLab permite asignar diferentes roles a los miembros del proyecto:

- **Desarrollador**: Puede contribuir con código, pero no administrar el proyecto.
- **Mantenedor**: Tiene permisos para fusionar ramas y gestionar configuraciones.
- **Propietario**: Control total del proyecto.
