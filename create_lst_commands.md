# Creating the LST Token Mint

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
    --mint-path Hay367MHMWdWnZKMtXXKHCRXfqPY6hofMsBA25VTYcXP.json
```

This command will create your token mint and metadata accounts. After running this, you'll receive a mint address that you'll need for the next steps.

### 2. Disable Freeze Authority

```bash
spl-token authorize --disable YOUR_MINT_ADDRESS freeze
```

Replace `YOUR_MINT_ADDRESS` with the mint address received from the previous command.

### 3. Transfer Mint Authority to Sanctum

```bash
spl-token authorize YOUR_MINT_ADDRESS mint GRwm4EXMyVwtftQeTft7DZT3HBRxx439PrKq4oM6BwoZ
```

Replace `YOUR_MINT_ADDRESS` with the same mint address.

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