<p align="center"><img src="https://dydx.exchange/images/logo.png" width="256" /></p>

<p align="center">
  <a href="https://circleci.com/gh/dydxprotocol/protocol">
    <img src="https://img.shields.io/circleci/project/github/dydxprotocol/protocol.svg" />
  </a>
  <a href='https://coveralls.io/github/dydxprotocol/protocol'>
    <img src='https://coveralls.io/repos/github/dydxprotocol/protocol/badge.svg?branch=master' alt='Coverage Status' />
  </a>
  <a href='https://github.com/dydxprotocol/protocol/blob/master/LICENSE'>
    <img src='https://img.shields.io/github/license/dydxprotocol/protocol.svg' alt='License' />
  </a>
  <a href='https://www.npmjs.com/package/@dydxprotocol/protocol'>
    <img src='https://img.shields.io/npm/v/@dydxprotocol/protocol.svg' alt='NPM' />
  </a>
  <a href='https://slack.dydx.exchange'>
    <img src='https://img.shields.io/badge/chat-slack-blue.svg' alt='Slack' />
  </a>
</p>

Source code for Ethereum Smart Contracts used by the dYdX Margin Trading Protocol

[Whitepaper](https://whitepaper.dydx.exchange)

[Short & Leveraged Long Tokens Whitepaper](https://margintokens.dydx.exchange)

### Development

#### Install

```
npm install
```

#### Compile

```
npm run compile
```

#### Test

```
npm test
```

#### Lint

Lint the javascript files (tests, deploy scripts)
```
npm run lint
```


Lint the solidity files (all smart contracts)
```
npm run solint
```

Lint the solidity files (custom dYdX linter)
```
npm run dydxlint
```

## Architecture

### Contracts

#### Base Protocol

##### Margin.sol

Contains business logic for margin trading. All external functions for margin trading are in this contract.

##### Proxy.sol

Used to transfer user funds. Users set token allowance for the proxy authorizing it to transfer their funds. Only allows authorized contracts to transfer funds.

##### Vault.sol

Holds all token funds. Is authorized to transfer user funds via the Proxy. Allows authorized contracts to withdraw funds.

#### Second Layer

##### ZeroExExchangeWrapper.sol

Allows positions to be opened or closed using 0x orders. Wraps the 0x Exchange Contract in a standard interface usable by Margin.

##### ERC20Short.sol

Allows short positions to be tokenized as ERC20 tokens. Ownership of a short token grants ownership of a proportional piece of the backing position.

##### ERC20Long.sol

Allows leveraged long positions to be tokenized as ERC20 tokens. Ownership of a leveraged long token grants ownership of a proportional piece of the backing position.

##### ERC721Position.sol

Allows margin positions to be represented as ERC721 tokens.

##### ERC721MarginLoan.sol

Allows loans to be represented as ERC721 tokens.

##### DutchAuctionCloser.sol

Allows margin positions to be automatically close via a dutch auction.

##### SharedLoan.sol

Allows multiple lenders to share in a loan position together.

_Read more about our smart contract architecture [here](https://docs.google.com/document/d/19mc4Jegby5o2IPkhrR2QawNmE45NMYVL6U23YygEfts/edit?usp=sharing)_
