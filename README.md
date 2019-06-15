# react-app-rewire-micro-frontends

This package makes a couple of modifications to react-scripts 2.0 for the
purpose of building microfrontends

## Single chunk

In `react-scripts` v1, your JavaScript was always compiled to a single file. In
version 2, code splitting is enabled by default, so your application will be
split into several 'chunks' which can be loaded onto the page indepedently. This
makes it much more difficult to dynamically download the required scripts into
an HTML file other than the one that react-scripts generates. So this rewiring
puts things back into a single chunk.

## Externals

To save bandwidth, react and react-dom are excluded from the compiled code, and
are expected to be present on the page as scripts instead.

## Installation
1. Install required dependencies:

    ```sh
    yarn add -D react-app-rewired react-app-rewire-micro-frontends
    ```

2. Edit your `package.json` scripts to use `react-app-rewired` instead of `react-scripts`.
3. Add this line to your `package.json`:

    ```json
      "config-overrides-path": "node_modules/react-app-rewire-micro-frontends",
    ```

That's it! Your app should now be compiled to just `/static/js/bundle.js` in dev
mode, or `main.[hash].js` for production builds, and in either case the compiled
code will not include react or react-dom.
