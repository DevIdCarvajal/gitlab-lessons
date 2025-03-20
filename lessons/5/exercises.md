# Ejercicios

## Ejercicio 1: Configurar un pipeline básico en GitLab CI/CD

1. Crea un archivo `.gitlab-ci.yml` en la raíz del repositorio.
2. Define un pipeline con una sola etapa (`build`) que muestre un mensaje en la terminal.
3. Haz un commit y súbelo a GitLab.
4. Verifica que el pipeline se ejecute correctamente en GitLab en la sección **CI/CD > Pipelines**.

## Ejercicio 2: Configurar un pipeline con pruebas automatizadas en Node.js

*Nota: Si no trabajas habitualmente con Node.js y prefieres hacerlo con otro stack tecnológico que te sea más familiar, no dudes en hacerlo. La idea de este ejercicio es que hagas un test y veas que se lanza en el pipeline al subirlo a GitLab.*

1. Asegúrate de que tu proyecto tiene `Jest` instalado (si no, instálalo con `npm install --save-dev jest`).
2. Modifica el archivo `.gitlab-ci.yml` para ejecutar las pruebas.
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
4. Haz un commit y sube los cambios.
5. Comprueba en **GitLab > CI/CD > Pipelines** que el test se ejecuta correctamente.

## Ejercicio 3: Configurar una regla para ejecutar pipelines solo en la rama main

1. Modifica el `.gitlab-ci.yml` para que los pipelines solo se ejecuten en `main`.
2. Crea una nueva rama y haz un commit.
3. Ve a **CI/CD > Pipelines** y verifica que no se ejecuta el pipeline en `new-branch`.
4. Cambia a `main`, sube un cambio y verifica que ahora sí se ejecuta el pipeline.
