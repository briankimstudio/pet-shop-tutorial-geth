Modifications for running PetShop tutorial with geth
By Brian Kim, February 20, 2018

1. Modify port in truffle.js

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

2. Unlock account before submitting transactions

Add following line before calling web3.eth.getAccounts within handleAdopt function in app.js

   web3.personal.unlockAccount(web3.personal.listAccounts[0],"PASSPHASE")

3 Modify gas limit

Check gas limit on geth console.
> eth.getBlock("pending").gasLimit
4712388

Modify gas in truffle.js

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
