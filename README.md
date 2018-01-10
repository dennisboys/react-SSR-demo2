## Server-side Rendering React App

#### Steps

#### Server side rendering (SSR)

Since we need to use JSX on the server side, so the code on the server need to run through Webpack and Babel in order for Node.js to understand it.

On server side, `src/index.js` will be the entry point for Webpack, and a bundle.js will be generated in build folder for Node.js to execute. We use `renderToString()` to render React component into a HTML markup string and sends it to browser upon request. However, this HTML markup does not contain any Javascript itself, so we need to also ship the Javascript code to the browser. We embed the client bundle.js file in the view template so when the template is loaded in the browser, it would see the bundle.js file and fetch it from the server behind the scene.

On the client side, `src\client\client.js` will be the entry point for Webpack, and a bundle.js will be generated in public folder. When this file is loaded in the browser, it hydrates the React component in the same div where the server generated markup sits and injects life into the components, such as attaching Javascript event handlers.