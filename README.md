# cover-token-mining

This Repo has the COVER token, migrator, vesting, blacksmith contracts.

## Contracts on Mainnet
* COVER Token: [0x5D8d9F5b96f4438195BE9b99eee6118Ed4304286](https://etherscan.io/address/0x5D8d9F5b96f4438195BE9b99eee6118Ed4304286#code)
* Migrator: [0xfcF3295b3B357e3e0D37ac5Ee14823E06ffdfBC6](https://etherscan.io/address/0xfcF3295b3B357e3e0D37ac5Ee14823E06ffdfBC6#code)
* Blacksmith: [0xE0B94a7BB45dD905c79bB1992C9879f40F1CAeD5](https://etherscan.io/address/0xE0B94a7BB45dD905c79bB1992C9879f40F1CAeD5#code)
* Vesting: [0xE98567885Df519dFeB12C0E268dD5d9b798bD531](https://etherscan.io/address/0xE98567885Df519dFeB12C0E268dD5d9b798bD531#code)

## Design
![design](https://github.com/CoverProtocol/cover-token-mining/blob/main/cover-token-mining.pdf)

## Development
* run `npm install` to install all node dependencies
* run `npm hardhat compile` to compile

### Run Test With hardhat EVM (as [an independent node](https://hardhat.dev/hardhat-evm/#connecting-to-hardhat-evm-from-wallets-and-other-software))
* Run `npx hardhat node` to setup a local blockchain emulator in one terminal.
* `npx hardhat test --network localhost` run tests in a new terminal.
 **`npx hardhat node` restart required after full test run.** As the blockchain timestamp has changed.

#### test `Migrator`
* Comment the one hard-coded safe2 address requirement in Migrator constructor.

## Deploy to Kovan Testnet
* Update `./scripts/deploy-constants.js` to use Kovan addresses.
* Add required env vars into your `./.env` file.  `KOVAN_DEV_PRIVATE_KEY` `KOVAN_TREASURY` `KOVAN_GOV`.
* Make sure your deployer account have `keth`.
* Comment out requirement in Constructor of the Migrator
* Run `npx hardhat run scripts/deploy.js --network kovan`.
* Add pools manually, adjust protocolFactory address in `add-pools.js` file and run `npx hardhat run scripts/add-pools.js --network kovan`.
