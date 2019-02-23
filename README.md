# tcb-service-sdk
云开发增值服务调用 SDK

## 支持服务

以下是支持服务的接口入参，具体用法请参考下节的[支持平台及使用步骤](#支持平台及使用步骤)。

* [短信](docs/sms/README.md)
* [AI](docs/ai/README.md)

## 支持平台及使用步骤

### 小程序
1. 将 `dist/tcb-service-js-sdk` 目录复制到小程序中。
2. 初始化：

```js
import TcbService from '路径/tcb-service-sdk/index'
let tcbService = new TcbService()
tcbService.callService({
    service: 'video',
    action: 'webrtcroom-enter-room',
    data: {
        roomID: '1234' 
    }
})
```

### Node （云函数或云主机）
1. 使用该命令安装依赖： `npm i --save tcb-service-sdk wx-server-sdk`
2. 初始化

```js
const cloud = require('wx-server-sdk')
cloud.init()
import TcbService from 'tcb-service-sdk'
let tcbService = new TcbService({
    // 相关参数，secret, env 等
})
tcbService.callService({
    service: 'video',
    action: 'webrtcroom-enter-room',
    data: {
        roomID: '1234' 
    }
})
```

## 接口

### callService

- 入参

| 字段 | 类型 | 必填 | 说明
| --- | --- | --- | ---
| service | string | 是 | 服务模块名称 <br> 1. sms 短信 <br> 2. ai 智能图像 
| action | string | 是 | 具体服务
| data | object | 否 | 传入参数

- 出参

| 字段 | 类型 | 必填 | 说明
| --- | --- | --- | ---
| code | string | 是 | 返回错误码，0为成功
| message | string | 是 | 返回信息
| data | object|array | 是 | 返回数据