Svelte is a JavaScript framework designed to build user interfaces (UIs) for the web. It differs from other frameworks like React, Angular, or Vue in its approach to building applications. Svelte shifts the work typically done at runtime to build time, resulting in smaller and more efficient code that runs faster in the browser.

Key features of Svelte include:

1. **Compiler-based Approach:** Svelte shifts much of the work traditionally done in the browser to the build step. The framework compiles components into highly optimized JavaScript code during the build process, which reduces the amount of runtime overhead.
    
2. **Declarative Syntax:** Svelte uses a declarative syntax for building components. It's similar to HTML, making it easy to read and understand. Svelte components consist of HTML, CSS, and JavaScript, all in a single file.
    
3. **Reactivity:** Svelte provides reactivity without the need for a virtual DOM. It automatically tracks dependencies and updates the DOM efficiently, resulting in performant applications.
    
4. **No Virtual DOM:** Unlike some other frameworks, Svelte does not use a virtual DOM. Instead, it updates the actual DOM elements directly, which can lead to improved performance.
    
5. **Component-based Architecture:** Svelte follows a component-based architecture, allowing developers to create reusable and modular UI components.
    
6. **Scoped Styles:** Styles defined within a Svelte component are scoped to that component by default, reducing the risk of style conflicts.


# Requirements 
[[Node.js]]
[[npm]]


# Project structure
- [[Svelte project structure]]


# Basic setup
install [[Node.js]] and npm
- download template svelte `npx degit sveltejs/template my-svelte-app`
 - move to the directory `cd my-svelte-app`
 - installare le dipendenze per il progetto  ` npm install`
- avvia il server di sviluppo `npm run dev`

# Projects
- [[Simple Chat]]
- [[Adventure-ia]]
- 

