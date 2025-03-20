# Soluciones

## Ejercicio 1: Configurar un pipeline básico en GitLab CI/CD

1. Crea un archivo `.gitlab-ci.yml` en la raíz del repositorio.
2. Define un pipeline con una sola etapa (`build`) que muestre un mensaje en la terminal:

   ```yaml
   stages:
     - build

   build_job:
     stage: build
     script:
       - echo "Pipeline ejecutado correctamente"
   ```
3. Haz un commit y súbelo a GitLab:

   ```bash
   git add .gitlab-ci.yml
   git commit -m "Añadir pipeline básico"
   git push origin main
   ```
4. Verifica que el pipeline se ejecute correctamente en GitLab en la sección **CI/CD > Pipelines**.

## Ejercicio 2: Configurar un pipeline con pruebas automatizadas en Node.js

1. Asegúrate de que tu proyecto tiene `Jest` instalado (si no, instálalo con `npm install --save-dev jest`).
2. Modifica el archivo `.gitlab-ci.yml` para ejecutar las pruebas:

   ```yaml
   stages:
     - test

   test:
     stage: test
     image: node:18
     before_script:
       - npm install
     script:
       - npm test
   ```
3. Crea un archivo de prueba `sum.js` con el siguiente contenido:

   ```javascript
   function sum(a, b) {
     return a + b;
   }

   module.exports = sum;
   ```
   Y un test en `__tests__/sum.test.js`:

   ```javascript
   const sum = require('../sum');

   test('Suma de 2 + 3 debe ser 5', () => {
     expect(sum(2, 3)).toBe(5);
   });
   ```
4. Haz un commit y sube los cambios:

   ```bash
   git add .
   git commit -m "Añadir pipeline con pruebas automatizadas"
   git push origin main
   ```
5. Comprueba en **GitLab > CI/CD > Pipelines** que el test se ejecuta correctamente.

## Ejercicio 3: Configurar una regla para ejecutar pipelines solo en la rama main

1. Modifica el `.gitlab-ci.yml` para que los pipelines solo se ejecuten en `main`:

   ```yaml
   test:
     stage: test
     image: node:18
     before_script:
       - npm install
     script:
       - npm test
     only:
       - main
   ```
2. Crea una nueva rama y haz un commit:

   ```bash
   git checkout -b new-branch
   touch archivo.txt
   git add archivo.txt
   git commit -m "Prueba en nueva rama"
   git push origin new-branch
   ```
3. Ve a **CI/CD > Pipelines** y verifica que no se ejecuta el pipeline en `new-branch`.
4. Cambia a `main`, sube un cambio y verifica que ahora sí se ejecuta el pipeline.
