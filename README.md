# How to run Truffle's PetShop tutorial with geth
By Brian Kim, February 20, 2018

The original Trufffle's PetShop tutorial requires Ganache, MetaMask to run the sample code. This tutorial is for running the sample code with geth and without Metamask. For this purpose, several modifications to source code are necessary to collaborate with geth. Most of the modifications are configuration of network envrionment such as **port** and **IP address**.

## 1. Modify port in truffle.js
```javascript
module.exports = {
  // See <http://truffleframework.com/docs/advanced/configuration>
  // for more about customizing your Truffle configuration!
  networks: {
    development: {
      host: "127.0.0.1",
      port: 8545, // 7545
      gas: 4712388,
      network_id: "*" // Match any network id
    }
  }
};
```
## 2. Unlock account before submitting transactions

Add following line before calling web3.eth.getAccounts within handleAdopt function in app.js
```javascript
   web3.personal.unlockAccount(web3.personal.listAccounts[0],"PASSPHASE")
```
## 3 Modify gas limit

##### 3.1 Check gas limit on geth console.
```javascript
> eth.getBlock("pending").gasLimit
4712388
```
##### 3.2 Modify gas in truffle.js
```javascript
module.exports = {
  networks: {
    development: {
      host: "127.0.0.1",
      port: 8545,
      gas: 4712388,
      network_id: "*" // Match any network id
    }
  }
};
```
