# Ethereum Smart Contracts

[![solidity](https://img.shields.io/badge/code%20style-solidity-brightgreen.svg?style=flat-square)](https://github.com/ethereum/solidity) [![EIP20](https://img.shields.io/badge/TOKEN-ERC20-brightgreen.svg?style=flat-square)](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-20.md) [![license](https://img.shields.io/github/license/mashape/apistatus.svg?style=flat-square)](https://opensource.org/licenses/MIT)

This repository contains Solidity smart contract codes. The repo currently implements [EIP20](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-20.md) tokens

## CALLTOKEN.sol
It’s a token contract that follows ERC20 standard, it it initialises with this parameters: 
```
“initial supply”, “token name”, “token symbol”
```
In our case: "52500000", "CAPITAL", "CALL" according to the Crowdsale Whitepaper.

After mint is over it is transferred to the owner address.

## CALLGTOKEN.sol 
It’s a token contract that follows ERC20 standard, it initialises with this parameters: 
```
“initial supply”, “token name”, “token symbol”
```
In our case: "10500000000", "CAPITAL GAS", "CALLG" according to the Crowdsale Whitepaper.

After mint is over it is transferred to the owner address.

## CapitalTechCrowdsale.sol
The parity of the tokens is as follows: `1 CALL = 200 CALLG`.

It’s a crowdsale contract with custom parameters, it’s initialised with these parameters: 
```
“storage wallet”, “CALLToken Contract address”, “CALLGToken Contract address”.
```
The contract has refund capabilities, user funds invested into the contract can be easily extracted back by them by calling the claimRefund() public function, but only if the soft cap (90% tokens sold) is not reached and if the sale is over.

If a user buys `1 CALL`, he automatically receives `1 CALL` and `200 CALLG` tokens.

The price of tokens calculates with the help of a public Fiat Contract.

The crowdsale split as follows:

Presale stage has 15 days, and the price of `1 CALL & 200` CALLG is 1.5$

The pre-ico stage has 30 days, and the cost of `1 CALL & 200` CALLG is 2$

Main sale stage has 30 days, and the price of `1 CALL & 200` CALLG is as following:

`First week: 3$`

`Second week: 3.3$`

`Third week: 3.6$`

`Fourth week: 4$`

The minimum investment is `0.01 ether`, and maximum contribution per address is `1500 ether`.

If an investor tries to buy tokens before the sale has opened, the transaction is rejected.

If an investor tries to buy tokens after the sale has closed, the transaction is rejected.

It has a manual transfer function that can be called by the only by the owner; it is used if a user invests through alternative payments (credit card, Bitcoin, litecoin, etc).

All unsold tokens will be burned after the end of crowdsale.
