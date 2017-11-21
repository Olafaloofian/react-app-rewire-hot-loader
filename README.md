# `react-app-rewire-hot-loader`

Add the [`react-hot-loader`](https://github.com/gaearon/react-hot-loader) to your `create-react-app` app via [`react-app-rewired`](https://github.com/timarney/react-app-rewired).

Because who wants their app, state, and styles automatically reloading all the time?

## Installation

```sh
npm install --save react-app-rewire-hot-loader

# If you don't already, you also need:
npm install --save react-app-rewired
npm install --save react-hot-loader
```

## Usage

1. In the `config-overrides.js` of the root of your project you created for `react-app-rewired` add this code:

```JS
const rewireReactHotLoader = require('react-app-rewire-hot-loader');

/* config-overrides.js */
module.exports = function override(config, env) {
  config = rewireReactHotLoader(config, env);
  return config;
}
```

2. Follow 'step 4' from https://github.com/gaearon/react-hot-loader , replicated below:

Wrap your application into `<AppContainer>`, all children of `<AppContainer>` will be reloaded when a change occurs.
```js
// main.js
import React from 'react'
import ReactDOM from 'react-dom'
import { AppContainer } from 'react-hot-loader'
import App from './containers/App'

const render = Component => {
  ReactDOM.render(
    <AppContainer>
      <Component />
    </AppContainer>,
    document.getElementById('root'),
  )
}

render(App)

// Webpack Hot Module Replacement API
if (module.hot) {
  module.hot.accept('./containers/App', () => { render(App) })
}
```

That's it, you now have hot reloads!


## License

Licensed under the MIT License, Copyright ©️ 2017 Chris Harris. See [LICENSE.md](LICENSE.md) for more information.
