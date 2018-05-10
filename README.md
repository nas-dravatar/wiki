# Wiki

This project is still in Development, Check out later


## How to get User info?

Easy, you will only need a function to send a reqeust with any Javascript Module (like Axios, Superagent)
```javascript
 async function get (from) {
  const to = network.testnet.address
  const other = {
    'value': '0',
    'nonce': 0,
    'gasPrice': '1000000',
    'gasLimit': '2000000',
    'contract': { 'function': 'get', 'args': '[""]' }
  }
  const { body } = await request
    .post('https://testnet.nebulas.io/v1/user/call')
    .send(Object.assign({ from, to }, other))

  const { result } = body.result
  const value = JSON.parse(result)
  console.log(value)
  return value
}
```


The return value is a Object contains three values: `avatar` `nickname` and `bio`

You just need to pick what you need. e.g.

```javascript
const {avatar, nickname, bio} = await get(walletAddress) // I need all of them
const {avatar} = await get(walletAddress) // I only need avatar
```

