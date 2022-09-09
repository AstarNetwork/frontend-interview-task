# Astar frontend interview task

## Task description

You are to build a web UI for psp22 smart contract (ERC20 equivalent) deployed on a local chain.
You are free to use a framework of your choice.
Interface can be as simple as wish, but should be to demonstrate your skills. When reviewing it, we will emphasize code and functionality over design.

Interface should _at least_ be able to:

- connect/disconnect to wallet
- display ballance of connected account
- display total supply
- transfer tokens to another account

## Environment

The contract is pregenerated and prebuilt for you, but you still need to run the node and deploy it.
This is made easier by using the `swanky-cli` tool, so all you need to do is download the node for your platform nd unpack it into the `/bin` folder:

- [mac](https://github.com/AstarNetwork/swanky-node/releases/download/v0.10.0/swanky-node-v0.10.0-macOS-x86_64.tar.gz)
- [linux](https://github.com/AstarNetwork/swanky-node/releases/download/v0.10.0/swanky-node-v0.10.0-ubuntu-x86_64.tar.gz)

> Note, the node filename must be `swanky-node`

## Setup

After cloning this repo, run

```
yarn install
```

to install the dependencies and download the node as described above.

### Running a node

In the project root folder, run

```
yarn node-start
```

You can interact with the node by going to the [polkadot.js.org](https://polkadot.js.org/apps) and switching to the `DEVELOPMENT->Local Node` in the upper left corner.

![Switching node](/img/scrn1.png?raw=true "Switching node")

### Adding an account

You can generate a new account by running

```
yarn account:generate
```

Mnemonic and an alias will be stored to `swanky.config.json`.
Now go to the `Accounts` section of polkadot.js.org interface and click `+ Add account` button.

Paste in the mnemonic you just generated and give it a name (use the same alias for simplicity).

Next, you need to transfer some units to that account so it can deploy the contract.
Next to `ALICE` account, click `send` button, choose your new account as destination, and enter `1000000000000` under `amount`.
Click `Make transfer` and `Sign and submit`.

### Deploying the contract

Using the alias of the account you created in the last step, run

```
yarn deploy --account [YOUR_ACCOUNT_ALIAS]
```

You'll get the address the contract is deployed to.

Optionally, you can add that contract to the polkadot.js.org interface to get an overview of the available messages.
Click `Developer -> Contracts -> "+Add an existing contract button"`.
Paste in your deployed contract address and drag and drop or upload the metadata file from `contracts/psp22/target/ink/metadata.json`.

![Adding contract](/img/scrn2.png?raw=true "Adding contract")

> Note if you restart the node your deployed contracts and added accounts will be lost - you'll have to repeat the process.

Everything is ready now for you to get hacking. Good luck!

## Resources:

- [polkadot{.js} wallet extension](https://polkadot.js.org/extension/)
- [polkadot.js library docs](https://polkadot.js.org/docs/)
- examples:
  - [react](https://github.com/polkadot-js/ui/tree/master/packages/example-react)
  - [vue](https://github.com/polkadot-js/ui/tree/master/packages/example-vue)
