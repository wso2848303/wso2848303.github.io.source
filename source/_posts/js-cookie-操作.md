---
layout: posts
title: js cookie 操作
date: 2019-07-04 12:59:09
tags: ["javascript"]
---
``` javascript
/**
 * 设置cookie
 * @param key {string} key
 * @param value {string} 值
 * @param days {number} 记录时间
 */
export const setCookie = (key, value, days = 1) => {
  let date = new Date();
  date.setDate(date.getDate() + days);
  document.cookie = key + '=' + escape(value) + ';expires' + date;
};
/**
 * 删除cookie
 * @param key {string} key
 */
export const removeCookie = (key) => {
  setCookie(key, '', -1);
};
/**
 * 获取cookie
 * @param key {string} key
 * @returns {*}
 */
export const getCookie = (key) => {
  let cookieStr = document.cookie.split('; ');
  for (let i = 0; i < cookieStr.length; i++) {
    let ret = cookieStr[i].split('=');
    if (ret[0] === key) {
      return unescape(ret[1]);
    }
  }
  return false;
};
```