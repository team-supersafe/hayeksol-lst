The HayekSOL LST is being deployed with Sanctum

## Project Files

### Token Files
- `HayekSOL.json` - Token metadata file containing name, symbol, description, image, and website
- `HayekSOL-metadata.json` - On-chain metadata configuration for the token
- `HAY3ZXFGUEaQLM1rnxHATU64n7c32PAyQ9CnvYxfZR4Q.json` - Token mint keypair
- `HayekSOL_token_info.md` - Documentation of token creation details and addresses

### Assets
- `HayekSOL.svg` - Vector logo for the token
- `HayekSOL.png` - Raster logo for the token

### Documentation
- `create_lst_commands.md` - Detailed commands used for token creation and configuration
- `readme.md` - This file, containing project overview and setup instructions

## Setup Instructions

### 1. Creating the Token Mint ✅
- Token properties:
  - Mint Address: `HAY3ZXFGUEaQLM1rnxHATU64n7c32PAyQ9CnvYxfZR4Q`
  - Decimals: 9 (standard for Solana tokens)
- Add metadata with metaboss CLI to leverage Metaplex's token metadata standard:
  - Name: "Hayek Staked SOL"
  - Symbol: "HayekSOL"
  - Description: "MEV-Powered Liquid Staking from the Hayek Validator"
  - Image: "https://team-supersafe.github.io/hayeksol-lst/HayekSOL.svg"
  - Website: "https://hayek.fi"
- Disable Freeze Authority
- Transfer Mint Authority to Sanctum (`GRwm4EXMyVwtftQeTft7DZT3HBRxx439PrKq4oM6BwoZ`)

### 2. Onboarding Process
1. Fill out the Sanctum onboarding form with:
   - Token mint address: `HAY3ZXFGUEaQLM1rnxHATU64n7c32PAyQ9CnvYxfZR4Q`
   - Project details
   - Contact information
   - Technical requirements

### 3. Technical Implementation
1. Deploy the Sanctum 2 Stake Pool Program
2. Configure the following parameters:
   - Stake pool authority
   - Fee structure
   - Rebalancing parameters
   - APY settings

### 4. Post-Deployment Steps
1. Verify the stake pool deployment
2. Test the integration
3. Set up monitoring and maintenance procedures
4. Configure APY optimization settings

### Important Notes
- Ensure all security best practices are followed
- Maintain proper documentation
- Set up monitoring for pool health
- Regular maintenance and updates as needed

For more detailed information, refer to the [Sanctum Documentation](https://learn.sanctum.so/docs/sanctum-lsts/setting-up-an-lst-with-sanctum)