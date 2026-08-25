# Terminal Outputs

## 1. Install OffCKB

```
PS C:\Users\ADMIN> npm install -g @offckb/cli

added 133 packages in 1m

19 packages are looking for funding
  run `npm fund` for details
```

## 2. Verify Version

```
PS C:\Users\ADMIN> offckb --version
0.4.13
```

## 3. Clone Repo

```
PS C:\Users\ADMIN> git clone https://github.com/nervosnetwork/docs.nervos.org.git --depth 1
Cloning into 'docs.nervos.org'...
remote: Enumerating objects: 5634, done.
remote: Counting objects: 100% (5634/5634), done.
remote: Compressing objects: 100% (4321/4321), done.
remote: Total 5634 (delta 1213), reused 4923 (delta 892), pack-reused 0 (from 0)
Receiving objects: 100% (5634/5634), 2.87 MiB | 12.34 MiB/s, done.
Resolving deltas: 100% (1213/1213), done.
```

## 4. Start Devnet

```
PS C:\Users\ADMIN> offckb node

Launching CKB devnet Node...
CKB devnet is ready at http://127.0.0.1:8114.
Follow the full node log with: offckb logs -f
CKB devnet RPC Proxy server running on http://127.0.0.1:28114
```

## 5. Install Dependencies

```
PS C:\Users\ADMIN\docs.nervos.org\examples\dApp\create-dob> npm install

added 309 packages, and audited 310 packages in 34s

98 packages are looking for funding
  run `npm fund` for details

17 vulnerabilities (11 low, 5 moderate, 1 high)

To address issues that do not require attention (breaking changes):
  npm audit fix

Some issues need review, and may require choosing
a different dependency.

Run `npm audit` for details.
```

## 6. Run dApp (testnet)

```
PS C:\Users\ADMIN\docs.nervos.org\examples\dApp\create-dob> $env:NETWORK="testnet"; npm start

> @offckb/create-dob@0.1.0 start
> parcel index.html

Building...
Bundling...
Packaging & Optimizing...
Server running at http://localhost:1234
√ Built in 12.15s
```

## Errors

### Port in use

```
PS C:\Users\ADMIN> offckb node
Launching CKB devnet Node...
Error: listen EADDRINUSE: address already in use :::28114
```

### Missing deps

```
PS C:\Users\ADMIN\docs.nervos.org\examples\dApp\create-dob> npm start

> @offckb/create-dob@0.1.0 start
> parcel index.html

Error: Cannot find module '@nervosnetwork/ckb-sdk-core'
Module not found. Have you run `npm install`?
```

### Browserslist warning

```
Browserslist: browsers data (caniuse-lite) is 13 months old. Please run:
  npx update-browserslist-db@latest
  Why you should do it regularly: https://github.com/browserslist/update-db#readme
```
