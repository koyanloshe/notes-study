# Node design patterns

![Node design patterns-1](images/Node%20design%20patterns-1.png)

![Node design patterns-2](images/Node%20design%20patterns-2.jpeg)

![Node design patterns-3](images/Node%20design%20patterns-3.png)

`const module = (() => { `
`  const privateFoo = () => {...}; `
`  const privateBar = []; `
` `
`  const exported = { `
`    publicFoo: () => {...}, `
`    publicBar: () => {...} `
`  }; `
` `
`  return exported; `
`})(); `
`console.log(module);`

* A module name is accepted as input, and the very first thing that we do is resolve the full path of the module, which we call id. This task is delegated to require.resolve(), which implements a specific resolving algorithm (we will talk about it later).
* If the module has already been loaded in the past, it should be available in the cache. In this case, we just return it immediately.
* If the module was not loaded yet, we set up the environment for the first load. In particular, we create a module object that contains an exports property initialized with an empty object literal. This property will be used by the code of the module to export any public API.
* The module object is cached.
* The module source code is read from its file and the code is evaluated, as we have seen before. We provide the module with the module object that we just created, and a reference to the require() function. The module exports its public API by manipulating or replacing the module.exports object.
* Finally, the content of module.exports, which represents the public API of the module, is returned to the caller.

![Node design patterns-4](images/Node%20design%20patterns-4.png)

