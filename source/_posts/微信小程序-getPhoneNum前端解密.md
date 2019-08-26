---
title: 微信小程序 getPhoneNum前端解密
date: 2019-08-26 16:33:09
tags: ["wechat-app"]
---
## 算法
解密算法使用google的[crytojs](https://github.com/gwjjeff/cryptojs)

### RdWXBizDataCrypt.js
``` javascript
/**
 * Created by rd on 2017/5/4.
 */
// 引入CryptoJS
var Crypto = require('cryptojs/cryptojs.js').Crypto;
var app = getApp();

function RdWXBizDataCrypt(appId, sessionKey) {
  this.appId = appId
  this.sessionKey = sessionKey
}

RdWXBizDataCrypt.prototype.decryptData = function (encryptedData, iv) {
  // base64 decode ：使用 CryptoJS 中 Crypto.util.base64ToBytes()进行 base64解码
  var encryptedData = Crypto.util.base64ToBytes(encryptedData)
  var key = Crypto.util.base64ToBytes(this.sessionKey);
  var iv = Crypto.util.base64ToBytes(iv);

  // 对称解密使用的算法为 AES-128-CBC，数据采用PKCS#7填充
  var mode = new Crypto.mode.CBC(Crypto.pad.pkcs7);
  
  try {
    // 解密
    var bytes = Crypto.AES.decrypt(encryptedData, key, {
        asBpytes:true,
        iv: iv,
        mode: mode
    });
    
    var decryptResult = JSON.parse(bytes);
    
  } catch (err) {
    console.log(err)
  }

  if (decryptResult.watermark.appid !== this.appId) {
    console.log(err)
  }

  return decryptResult
}

module.exports = RdWXBizDataCrypt
```

### demo.js
``` javascript
import WXBizDataCrypt from '../../utils/RdWXBizDataCrypt';
getPhoneNumber: function (e) {
    if (e.detail.errMsg === 'getPhoneNumber:ok') {
      let pc = new WXBizDataCrypt(globalData.appId, globalData.sessionKey);
      let data = pc.decryptData(e.detail.encryptedData, e.detail.iv);
      this.setData({
        tel: data.purePhoneNumber,
        area: data.countryCode
      });
    }
  }
```