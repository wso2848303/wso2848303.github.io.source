---
layout: posts
title: axios全局拦截
date: 2019-07-03 14:08:06
tags: ["Axios", "requests"]
---
``` javascript
import axios from 'axios';
axios.interceptors.response.use(
  response => {
    console.log(response);
    return response;
  },
  error => {
    return Promise.reject(error);
  }
)
axios.interceptors.request.use(
  config => {
    console.log(config);
    return config
  },
  error => {
    return Promise.reject(error);
  }
)
```

分别全局拦截axios的响应和请求，主要用来做登录拦截或者错误统一提示或请求统计一些功能