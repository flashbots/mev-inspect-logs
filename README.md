# Log-based MEV inspections

This repository contains scripts which output data compatible with MEV Explore. This is
complementary to the [tracing-based](https://github.com/flashbots/mev-inspect-rs/) MEV inspectors.

## Supported Log Inspections

* DyDx: `node scripts/getDydxLiqs.js`

## Env Vars

Set the `URL` environment variable if you want to use a non-localhost node with the scripts.

## MEV DB

Your script must outpout a CSV file with the following columns:

* `hash`: The transaction's hash
* `status`: `success` if the
* `block_number`: The transaction's block number
* `gas_price`: The transaction's gas price
* `revenue`: The revenue made from the transaction
* `protocols`: The protocols involved in this transaction
* `actions`: The action: arbitrage, liquidation, trade, sandwich
* `eoa`: The sender of the transaction
* `contract`: The receiver of the transaction
* `proxy_impl`: The proxy which was used by the contract. Typically arbitrageurs will have a main contract that they always use as their entrypoint, and they have multiple implementations for their various strategies

The output will then be directly inserted to the database of MEV Explore.

Alternatively, you could have the option to directly talk to a PostGres with [this](https://github.com/flashbots/mev-inspect-rs/blob/master/src/mevdb.rs#L38-L56) schema.
