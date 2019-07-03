---
layout: posts
title: React-Redux store 配置
date: 2019-07-03 15:29:00
tags: ["React", "React-Redux"]
---
### modules/index.js
``` javascript
import { combineReducers } from 'redux';
import app from './app';
/**
 * reducer 合并
 */
const rootReducer = combineReducers({
  app
});
export default rootReducer;
```

### configureStore.js
``` javascript
import { createStore, applyMiddleware, compose } from "redux";
import thunk from "redux-thunk";
import rootReducer from "./modules"; // reducers

let finalCreateStore;
// 如果程序运行在非生产模式下，且浏览器安装了调试插件，则创建包含调试插件的store
if (process.env.NODE_ENV !== "production" && window.__REDUX_DEVTOOLS_EXTENSION__ ) {
  finalCreateStore = compose(
    applyMiddleware(thunk),
    window.__REDUX_DEVTOOLS_EXTENSION__()
  )(createStore);
} else {
  finalCreateStore = applyMiddleware(thunk)(createStore);
}

export default function configureStore(initialState) {
  const store = finalCreateStore(rootReducer, initialState);

  // 支持reducer的热加载
  if (process.env.NODE_ENV !== "production" && module.hot) {
    module.hot.accept("./modules", () =>
      store.replaceReducer(require("./modules"))
    );
  }

  return store;
}

```

### index.js
``` javascript
import React from "react";
import ReactDOM from "react-dom";
import { Provider } from "react-redux";
import configureStore from "./redux/configureStore";
import App from "./containers/App";
import * as serviceWorker from './serviceWorker';
const store = configureStore();
window.mock = mock;
ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById("root")
);
serviceWorker.register();
```