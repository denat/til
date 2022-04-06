# Debug libraries locally using yarn link

To debug a library/package in the context of your application:


### 1. Clone and setup the library locally

```unix
❯ git clone git@github.com:apollographql/graphql-tag.git
❯ cd graphql-tag
```

### 2. In the library directory, make it available for linking by running `yarn link`

```unix
❯ yarn link
yarn link v1.22.5
success Registered "graphql-tag".
info You can now run `yarn link "graphql-tag"` in the projects where you want to use this package and it will be used instead.
Done in 0.08s.
```

### 3. In your app (this lib's dependent), run `yarn link <library name>`

```unix
❯ yarn link graphql-tag
yarn link v1.22.5
success Using linked package for "graphql-tag".
Done in 0.14s.
```

This connects your app to the local version of the lib dependency, allowing you to debug and even run your own modified version of the lib code!

What's happening behind the scenes is that yarn is creating a symlink in your app's node_modules (i.e. `node_modules/graphql-tag`) that links to the local copy of the library.

Links are registered in `~/.config/yarn/link` if on Linux, or `%APPDATA%\Local\Yarn\Data\link` if on Windows.