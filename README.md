# Log-based MEV inspections

This repository contains scripts which output data compatible with MEV Explore. This is
complementary to the [tracing-based](https://github.com/flashbots/mev-inspect-rs/) MEV inspectors.

## Supported Log Inspections

* DyDx: `node scripts/getDydxLiqs.js`

## Env Vars

Set the `URL` environment variable if you want to use a non-localhost node with the scripts.
