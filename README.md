# react-app-rewire-disable-chunks
In `react-scripts` v1, your JavaScript was always compiled to a single file. In
version 2, code splitting is enabled by default, so your application will be
split into several 'chunks' which can be loaded onto the page indepedently. This
is often a good idea, especially for performance! But there are also legitimate
use cases where you need your code to be in just one file, especially when your
React app is just one portion of a larger page.

This rewiring allows you to easily customise your `create-react-app` application
without having to eject it. You only need to install this package alongside
`react-app-rewired`, and make a couple of changes to your `package.json`.

## Installation
1. Install required dependencies:

    ```sh
    yarn add -D react-app-rewired react-app-rewire-disable-chunks
    ```

2. Edit your `package.json` scripts to use `react-app-rewired` instead of `react-scripts`.
3. Add this line to your `package.json`:

    ```json
      "config-overrides-path": "node_modules/react-app-rewire-disable-chunks",
    ```

That's it! Your app should now be compiled to just `/static/js/bundle.js` in dev
mode, or `main.[hash].js` for production builds.
