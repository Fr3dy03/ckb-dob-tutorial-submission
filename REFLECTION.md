# Reflection

## What I Did

I ran through the "Create a DOB" tutorial from start to finish. Installed OffCKB, spun up a devnet, built the tutorial dApp, uploaded an image, created a Spore DOB on-chain, rendered it back in the browser, then switched to testnet.

## What I Learned

**Setting up OffCKB** - The dev environment is straightforward. One command to install, one to start the node. It gives you pre-funded accounts and a local RPC endpoint. No Docker, no config files, just `npm install -g @offckb/cli` and `offckb node`. Compared to setting up a local Ethereum node, this was painless.

**Running the dApp** - The tutorial uses Parcel as a bundler and React for the UI. Nothing fancy. The NETWORK environment variable switches between devnet, testnet, and mainnet. Same code, different RPC endpoint. I liked that - no separate deployments needed.

**Creating the DOB** - The `createSpore()` function does the heavy lifting. I feed it a private key and image bytes, it builds a transaction with a Spore output cell, signs it, sends it. The image bytes go directly into the cell data field. That's the key insight - the data is on-chain, not a pointer to something off-chain.

**Rendering from chain** - `showSporeContent()` fetches the cell back using the tx hash and output index, then `unpackToRawSporeData()` decodes the content type and bytes. I convert the hex to a Blob, create a URL, and set it as an img src. The image appears in the browser. It came from the blockchain.

**Switching to testnet** - Changed the environment variable, restarted the app, done. The ccc-client reads the env and picks the right RPC. Devnet points to localhost, testnet points to the public node.

## What Stood Out

DOBs and NFTs are fundamentally different. An NFT is a token that points to metadata. A DOB is the metadata itself, stored in a cell. The data is the asset, not a reference to it.

The cell model makes this natural. Each cell has capacity, lock, type, and data. Capacity pays for storage. The Spore type script enforces the data structure. It's a cleaner separation than smart contract NFTs where everything is mixed together.

The content-type field was surprising. Spore doesn't care what you put in there. Images, PDFs, videos, text - anything that fits in the cell capacity. That's more flexible than most NFT standards.

The trade-off is cost. You pay CKB for every byte stored. A 2.8KB image costs a few hundred CKB. A 10MB video would cost significantly more. But you get permanence - no pinning services, no gateways, no external dependencies.

## Errors I Hit

- Port 28114 was already in use - had to kill the old process
- Browserslist data was stale - fixed with `npx update-browserslist-db@latest`
- npm audit showed vulnerabilities - none relevant to the tutorial

All minor, all fixable. The tutorial code worked as documented.
