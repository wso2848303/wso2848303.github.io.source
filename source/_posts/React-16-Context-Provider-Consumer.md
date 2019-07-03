---
layout: posts
title: React 16 Context Provider/Consumer
date: 2019-07-03 14:50:36
tags: ["react"]
---

``` javascript
import React, {
  Component
} from 'react';
const Context = React.createContext();
class Father extends Component {
  constructor(props) {
    super(props);
  }
  render() {
    return ( <
      Context.Provider value = {
        {
          props: {
            ...this.props
          }
        }
      } >
      ...jsx <
      /Context.Provider>
    )
  }
}
class Child extends Component {
  constructor(props) {
    super(props);
  }
  render() {
    return ( <
      Context.Consumer > {
        // 此处context数据即为最近父级Provider中定义要共享的对象
        context => {
          return (
            ...jsx
          )
        }
      } <
      /Context.Consumer>
    )
  }
}
```
已经定义过的Consumer可以接收最近上级的Provider定义的传递数据（任何类型）