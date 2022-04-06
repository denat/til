# SSR & Isomorphic apps depend on React's renderToString() method

Frameworks such as Next.js and Razzle heavily depend on React's [`renderToString`](https://reactjs.org/docs/react-dom-server.html#rendertostring) method from `react-dom/server`.

This method is used on the server side to generate the component's HTML and send the output to the client "over the wire", leaving the client to just hydrate the contents and wire up the React stuff using [`ReactDOM.hydrate()`](https://reactjs.org/docs/react-dom.html#hydrate).

More info:

- [https://reactjs.org/docs/react-dom-server.html#rendertostring](https://reactjs.org/docs/react-dom-server.html#rendertostring)
- [https://en.wikipedia.org/wiki/Isomorphic_JavaScript](https://en.wikipedia.org/wiki/Isomorphic_JavaScript)
- [https://github.com/facebook/react/blob/main/packages/react-dom/src/server/ReactDOMStringRenderer.js#L16](https://github.com/facebook/react/blob/main/packages/react-dom/src/server/ReactDOMStringRenderer.js#L16)