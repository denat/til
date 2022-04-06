# Debug Node.js code in JavaScript Debug Terminal

Even more convenient than the [auto attach](https://code.visualstudio.com/docs/nodejs/nodejs-debugging#_auto-attach) feature 
is the [JavaScript Debug Terminal](https://code.visualstudio.com/docs/nodejs/nodejs-debugging#_javascript-debug-terminal). Any Node process
that you run in it will automatically have a debugger attached to it!

Additionally, you'd want to skip debugging for node internals, which would require adding this to your user or workspace settings:

```json
"debug.javascript.terminalOptions": {
  "skipFiles": [
    "<node_internals>/**"
  ]
},
```