# Execute a Node.js script directly using a shebang line

In Unix, you can directly execute a JS script using Node.js by placing `#!/usr/bin/env node` as the first line in the script.

Example file named `hello.js`:

```js
#!/usr/bin/env node

console.log("Hello world!");
```

Can be run as:

```bash
> ./hello.js
Hello world!
```

These are called [Shebang lines](https://en.wikipedia.org/wiki/Shebang_(Unix)). They assume that the file is marked as executable (`chmod +x ./file`).

Shebang lines are used mostly for Python scripts (via `#!/usr/bin/env python3`) to explicitly select a Python interpreter version.