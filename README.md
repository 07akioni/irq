# irw

`irw` means `isomorphic request wrapper`.

You can use it to wrap different http request clients into a isomorphic way.

```ts
import { irw } from "irw";

// for axios
const request = irw({
  request(config) {
    return axios(config);
  },
});

// for weixin miniapp
const request = irw({
  request(config) {
    wx.request(config);
  },
});

// interceptor
request.interceptors.request.use((config) => {
  return {
    ...config,
    headers: {
      ...config.headers,
      token: "foo",
    },
  };
});

// request
request.get('/url', { params: {} }).then()
request.post('/url', { data: {} }).then()
request({
  url: '/url'
  method: 'post',
  data: {}
}).then()
```
