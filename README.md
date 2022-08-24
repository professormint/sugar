[![Crate](https://img.shields.io/crates/v/sugar-cli)](https://crates.io/crates/sugar-cli)
[![Downloads](https://img.shields.io/crates/d/sugar-cli)](https://crates.io/crates/sugar-cli)
[![Stars](https://img.shields.io/github/stars/metaplex-foundation/sugar?style=social)](https://img.shields.io/github/stars/metaplex-foundation/sugar?style=social)
[![Forks](https://img.shields.io/github/forks/metaplex-foundation/sugar?style=social)](https://img.shields.io/github/forks/metaplex-foundation/sugar?style=social)
[![Release](https://img.shields.io/github/v/release/metaplex-foundation/sugar)](https://img.shields.io/github/v/release/metaplex-foundation/sugar)
[![Build and Release](https://github.com/metaplex-foundation/sugar/actions/workflows/build.yml/badge.svg)](https://github.com/metaplex-foundation/sugar/actions/workflows/build.yml)
[![License](https://img.shields.io/crates/l/sugar-cli)](https://github.com/metaplex-foundation/sugar/blob/main/LICENSE)

# Phase CLI

<p align="center">
  <img src="phase-logo.svg">
</p>

Phase CLI is built upon the popular Metaplex Sugar CLI to allow the creation of Phase compatiable minting accounts. 

> **Note:** This is a alpha release of Phase CLI. Use at your own risk.

## Installation

### Recommended Method

For macOS, Linux and Windows Subsystem Linux (WSL), run the following install script in your terminal:

```bash
bash <(curl -sSf https://dedmonkes.github.io/phase-cli/install.sh)
```


### Developers

Build From Source:

You need to have access to the phase-protocol repo to build as it is a private submodule in this repo

```bash
git clone --recurse-submodules git@github.com:dedmonkes/sugar.git 
cargo install --path ./
```



## Quick Start

Before using the CLI you must have created a roadmap at http://phaseprotocol.io, take note of both the roadmap address and the collection mint address that are created in this process, as that will be needed to deploy your phase compatiable minting account.

Set up your Solana CLI config with an RPC url and a keypair ( this keypair must be the same one used to create the roadmap in the webapp ):

```bash
solana config set --url <rpc url> --keypair <path to keypair file>
```

Phase CLI will then use these settings by default if you don't specify them as CLI options, allowing commands to be much simpler. If you need help setting up Solana CLI and creating a `devnet` wallet, check the [Candy Machine v2 documentation](http://docs.metaplex.com/candy-machine-v2/getting-started#solana-wallet).

Create a folder named `assets` to store your json and media file pairs with the naming convention 0.json, 0.<ext>, 1.json, 1.<ext>, etc., where the extension is `.png`, `.jpg`, etc. This is the same format described in the [Candy Machine v2 documentation](http://docs.metaplex.com/candy-machine-v2/preparing-assets). Although you must use the collection mint provided by the Phase Protocol web app so do not include this in your assets, instead use the `collection set <mint_address>` command after deploying your candy machine to config the collection associated. 

You can then use the `launch` command to start an interactive process to create your config file and deploy a Candy Machine to Solana. In this process you will be prompted for the roadmap address you have just created. The payout address (pool) will be automatically derived from this address (wSOL), so you will not be prompted for a payout address.

```bash
phase launch
```

At the end of the execution of the `launch` command, the Candy Machine will be deployed on-chain.

To mint

``bash
phase mint <roadmapAddress>
```
