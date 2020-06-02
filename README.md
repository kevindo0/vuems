### vuems
```bash
npm install
npm install --registry=https://registry.npm.taobao.org
# 本地开发
npm run dev
```

### 1. 技巧
#### 1. [IM敏感词](https://cloud.tencent.com/document/product/269/1671#.EF.BC.88.E4.BA.8C.EF.BC.89.E6.9C.8D.E5.8A.A1.E7.AB.AF.E7.9A.84.E9.94.99.E8.AF.AF.E7.A0.81)
```js
import TIM from 'tim-js-sdk'
const message = this.tim.createTextMessage({
  to: "groupId",
  conversationType: TIM.TYPES.CONV_GROUP,
  payload: {
    text: "inputmsg"
  }
})
// 以送消息
const promise = this.tim.sendMessage(message)
promise.then((res) => {
  console.log(res)
}).catch((imError) => {
  // {"message":"secure check error! beat word: ***","code":80001}
  // 80001 文本安全打击，文本中可能包含敏感词汇。 
  console.warn('sendMessage error:', imError)
})
```

### 参考事例
#### 1. [chat](https://wow.techbrood.com/fiddle/6557)

