# Use $$() to select all matching elements

In Chrome devtools, `$()` is a shortcut for `document.querySelector()`, which returns the first element in the document that matches the provided selector(s). It returns null if no matches are found.

There's also `$$()`, a shortcut for `document.querySelectorAll()`, which returns a `NodeList` with all the matches. This will never return null. If no matches are found it'll simply return an empty `NodeList`.