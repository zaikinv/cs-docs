## Modules

  - IIFE (old)

    ```js
    const module = (function(anotherObjectLoaded) {
      // implementation
      return {
        doSomething: () => {}
      }
    })(window)
    ```

    ❌ still polluting global space

    ❌ order matters

  - CommonJS (mainly in Node)

    ```js
      const anotherModuleLoaded = require('module')
      
      module.exports = {
        // implementation
        doSomething: () => {}
      }
      ```
      ❌ synchronously loaded

  - AMD (asynchronous, used in Require.js)

    ```js
      define('module', [anotherModule], function(anotherModuleLoaded) {
        // implementation
        return {
          doSomething: () => {}
        }
      })
      ```

      ❌ loader libraries are required (Require.js)

  - UMD

    - CommonJs + AMD + globar variable

    - An `if-else` wrapper that provides module in format required by environment

    ❌ boilerplate code

  - ES6

      ```js
      import anotherModule from 'module';

      const doSomething = () => {}

      export default doSomething
      ```  
