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
spl-token authorize --disable Hay367MHMWdWnZKMtXXKHCRXfqPY6hofMsBA25VTYcXP freeze
```

Replace `Hay367MHMWdWnZKMtXXKHCRXfqPY6hofMsBA25VTYcXP` with the mint address received from the previous command.

### Output
```
Updating Hay367MHMWdWnZKMtXXKHCRXfqPY6hofMsBA25VTYcXP
  Current freeze: 4FbPnN2A6zerBETx7NeERqDJMZjR5WhUQgXbCEw6mbVD
  New freeze: disabled

Signature: 5ZR8NnxSvdBoYoGkeQnvPM4SToxogHEH9UUyhX5st8QVUqAm5DS67ksQ4mtsXuSMgRzP8opjUDFcw3rdeDPYV9ZL
```

### 3. Transfer Mint Authority to Sanctum

```bash
spl-token authorize Hay367MHMWdWnZKMtXXKHCRXfqPY6hofMsBA25VTYcXP mint GRwm4EXMyVwtftQeTft7DZT3HBRxx439PrKq4oM6BwoZ \
-um --config ~/.config/solana/cli/config.yml \
--fee-payer ~/solana/me.json
```

Replace `Hay367MHMWdWnZKMtXXKHCRXfqPY6hofMsBA25VTYcXP` with the same mint address.

### Output
```
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