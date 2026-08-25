# CKB DOB Campaign Submission

Completed the ["Create a DOB"](https://docs.nervos.org/docs/dapp/create-dob) tutorial.

## What Happened

OffCKB installed. Devnet running. Built the tutorial dApp. Uploaded a test image. Created a Spore DOB on-chain. Rendered it back in the browser. Switched to testnet.

```powershell
npm install -g @offckb/cli
offckb node
# CKB devnet RPC Proxy server running on http://127.0.0.1:28114

cd docs.nervos.org/examples/dApp/create-dob
npm install
$env:NETWORK="testnet"; npm start
# Server running at http://localhost:1234
```

## Transaction

| Network | Tx Hash |
|---------|---------|
| Testnet | `0xbe5e779e2955c2492fa01deadbb3a55a9358bc2c9660f7621ab3e1df8b1601f4` |


## Reflection

The core difference between DOBs and NFTs: where the data lives. Traditional NFTs point to off-chain metadata. DOBs store the actual bytes in a CKB cell. My 2.8KB test image is sitting on-chain right now - not a hash of it, not a URL to it, the actual file.

You pay capacity for every byte. Permanence costs CKB. No pinning services, no gateways that could go down.

The cell model makes this work. Each cell has capacity (pays for storage), a lock script (ownership), a type script (Spore protocol), and data (your content). Cleaner than NFT contracts where token logic, metadata, and storage are all tangled together.

The content-type field surprised me. Spore doesn't care what you store. Could be images, PDFs, videos, text, executables - anything that fits. Opens up use cases beyond collectibles.

Use cases I thought about:
- Academic credentials on-chain, verifiable by anyone with the tx hash
- Legal timestamps - hash a contract, store it as a DOB, provable timestamp + content
- Software distribution - store a binary, users verify content hash matches download

The code was clean. `createSpore()` builds the transaction, signs it, sends it. `showSporeContent()` fetches the cell, unpacks the data. CCC SDK handles RPC. OffCKB handles devnet.

Errors: port 28114 already in use, browserslist stale, npm audit showed 17 vulnerabilities (none relevant).

## Checklist

- [x] OffCKB installed (v0.4.13)
- [x] Devnet running
- [x] DOB created with image via Spore-SDK
- [x] Image rendered from chain data
- [x] dApp on testnet
- [x] Real transaction hash: `0xbe5e779e2955c2492fa01deadbb3a55a9358bc2c9660f7621ab3e1df8b1601f4`
- [x] Screenshot taken
- [x] Reflection written

Done.
