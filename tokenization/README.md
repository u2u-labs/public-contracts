# Configuration Export for GitHub Repository

This folder contains the organized configuration files for contract and token addresses that will be hosted in a GitHub repository and fetched by the application.

## Folder Structure

```
config-export/
├── mainconfig.json                 # Main configuration with default chain
├── wld/                            # World Chain (Symbol: WLD, Chain ID: 480)
│   ├── contracts.json             # Contract addresses for World Chain
│   └── tokens.json                # Token addresses for World Chain
└── u2u/                            # U2U Solaris Mainnet (Symbol: U2U, Chain ID: 2484)
    ├── contracts.json             # Contract addresses for U2U Network
    └── tokens.json                # Token addresses for U2U Network
```

## File Descriptions

### mainconfig.json
- Determines the default chain for the application
- Contains chain metadata (ID, name, RPC URLs, block explorers)
- Lists all available chains

### [chain-symbol]/contracts.json
- Contains all contract addresses for that specific chain
- Includes Uniswap V2, V3, and Universal Router addresses
- Includes network documentation links

### [chain-symbol]/tokens.json
- Contains all token configurations for that chain
- Each token includes: address, symbol, decimals, name, isNative flag
- Lists supported tokens available in the swap UI
- Includes network-specific notes

## How to Use

1. Copy the entire contents of this `config-export/` folder to your configuration GitHub repository
2. Push to the appropriate branch (dev, staging, production)
3. The application will fetch configurations from the raw GitHub URL pattern:
   ```
   https://raw.githubusercontent.com/{owner}/{repo}/{branch}/{chain}/{file}
   ```

## Environment Variables

The application needs the following environment variable:
- `NEXT_PUBLIC_ENV`: Determines which branch to fetch configs from (dev, staging, production)

## Example Fetch URLs

For World Chain on production branch:
- Contracts: `{raw-url}/production/wld/contracts.json`
- Tokens: `{raw-url}/production/wld/tokens.json`

For World Chain on dev branch:
- Contracts: `{raw-url}/dev/wld/contracts.json`
- Tokens: `{raw-url}/dev/wld/tokens.json`

## Notes

- All addresses are in lowercase for consistency
- Native tokens use the zero address (0x0000000000000000000000000000000000000000)
- Update `mainconfig.json` to change the default chain
- Add new chains by creating a new folder with contracts.json and tokens.json
