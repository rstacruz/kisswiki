Importing the exact module you want isn't some premature optimisation, it's what you should be doing. Inporting one named export from a module should run the entire module, exporting and importing all unnecessary code. That's what the ES6 module definition is. Rollup, to me, is a nice hack, but it's not something you should be depending on. In any case, importing the exact module will always be faster than importing it from the main file, as rollup doesn't need to analyse any of the other dependencies.

https://github.com/jspm/jspm-cli/issues/1631
