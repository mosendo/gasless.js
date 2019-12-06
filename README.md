<div align="center">
  <h2>Gasless.js</h2>
  <blockquote>Send DAI without ETH in your app</blockquote>
</div>

## Features

- Gasless DAI transfers via the Mosendo API
- Browser & Node.js support
- Injected web3 provider (e.g. Metamask) support
- EIP712 for readable user signed messages

## Getting Started
```sh
npm i --save gasless
```

## Usage

### Injected Web3 Provider (e.g. Metamask)

```js
import Gasless from 'gasless';

(async ()=>{

    await window.ethereum.enable();
    const gasless = new Gasless(window.web3.currentProvider);
    const gasPrice = await window.web3.eth.getGasPrice();
    const daiFee = await gasless.getFee(gasPrice);
    const from = window.web3.eth.defaultAccount;
    const txHash = await gasless.send(
        from,   // Sender address                   (string)
        to,     // Recipient address                (string)
        value,  // base unit DAI amount             (string)
        daiFee  // (Optional) base unit DAI fee.    (string)
    );

})()
```

### Custom Web3 Provider

Please make sure that your custom provider supports EIP712 signTypedData_v3.

Just replace `window.web3.currentProvider` in the example above with your custom provider.