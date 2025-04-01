# Creating the LST Token with Sanctum

This guide contains the commands needed to create the LST token mint following Sanctum's documentation.

## Prerequisites

- Solana CLI tools installed
- Metaboss installed
- SPL Token CLI installed
- Your keypair file (`HayekSOL_keypair.json`)
- Metadata file (`HayekSOL-metadata.json`)

## Commands

### 1. Create Token Mint and Metadata

```bash
metaboss create fungible \
--decimals 9 \
--metadata HayekSOL-metadata.json \
--mint-path HAY3ZXFGUEaQLM1rnxHATU64n7c32PAyQ9CnvYxfZR4Q.json \
--rpc "https://rpc.ironforge.network/mainnet?apiKey=<yourApiKey>"
```

This command will create your token mint and metadata accounts. After running this, you'll receive a mint address that you'll need for the next steps.

Command output

```text
Signature: 4gfjrjK5bTXDccZyzMYrdKPncuKjQV8doeQVpFouRnWJLihENCASuvWPME1s7d43FBnXPvALGFrBa7bPwBA1KnbN
Mint: HAY3ZXFGUEaQLM1rnxHATU64n7c32PAyQ9CnvYxfZR4Q
Metadata: H5HFaENgLs5UL2hjtzQ1yuJ2FcRX9QQonUJTzWSBwT1L
```

### 2. Disable Freeze Authority

> NOTE: spl-token might need the location of your config file, provide it with --config

```bash
spl-token authorize --disable HAY3ZXFGUEaQLM1rnxHATU64n7c32PAyQ9CnvYxfZR4Q freeze \
-um --config ~/.config/solana/cli/config.yml
```

Command output

```text
Updating HAY3ZXFGUEaQLM1rnxHATU64n7c32PAyQ9CnvYxfZR4Q
  Current freeze: GFefRR6EASXvnphnJApp2PRH1wF1B5pJijKBZGFzq1x1
  New freeze: disabled

Signature: 5j3ipK4xKMUWDnfA3E9u1fNTjB9PCs4j6h67ow8PvZiDsbaFxqbuYL7mxaGcd6vNXUs945cLd664GPCpAimebX5D
```

#### Updating Metadata

You can change metadata like "name", "uri", "symbol" or add new fields to the metadata one at a time with metaboss

```sh
metaboss update name --keypair ~/solana/me.json \
--account HAY3ZXFGUEaQLM1rnxHATU64n7c32PAyQ9CnvYxfZR4Q \
--new-name "Hayek Staked SOL" \
--rpc "https://rpc.ironforge.network/mainnet?apiKey=<yourApiKey>"
```

Command output

```text
Tx sig: 2vscTMEtWeffBugjUgwXVhigJPvgbAWP7r7xpmDgBkG9j1boHsFuk4gc4yTU6pqaZ6TBeK78HbeFN622jCjatdyz
```

In this case we changes the field name to "Hayek Staked SOL". Do the same to change other fields.

### 3. Transfer Mint Authority to Sanctum

```bash
spl-token authorize HAY3ZXFGUEaQLM1rnxHATU64n7c32PAyQ9CnvYxfZR4Q mint GRwm4EXMyVwtftQeTft7DZT3HBRxx439PrKq4oM6BwoZ \
-um --config ~/.config/solana/cli/config.yml
```

Command output

```text
Updating Hay367MHMWdWnZKMtXXKHCRXfqPY6hofMsBA25VTYcXP
  Current mint: 4FbPnN2A6zerBETx7NeERqDJMZjR5WhUQgXbCEw6mbVD
  New mint: GRwm4EXMyVwtftQeTft7DZT3HBRxx439PrKq4oM6BwoZ

Signature: 4Fs53qfVeEUnBDKQSKg4NUTAvqKKK6xLnDhArhMy5iS4oGc45tC6aiXWe1NyASsHcZH69yKoeJTYF8NM55LudeY8
```

## Verification

After running these commands, verify the following on the Solana explorer:

1. 9 decimals
2. 0 initial supply
3. No freeze authority
4. On-chain metadata is loading correctly

## Notes

- The Sanctum manager key (`GRwm4EXMyVwtftQeTft7DZT3HBRxx439PrKq4oM6BwoZ`) will temporarily control the mint authority until your stake pool is live
- Once your stake pool is live, the mint authority will be transferred to your pool
- Make sure to save the mint address for future reference
