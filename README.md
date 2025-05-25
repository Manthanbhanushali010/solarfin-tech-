# Solar Energy Tokenization System

A blockchain-based system for tokenizing solar energy production, built on Avalanche Fuji testnet.

## Overview

This system enables:
- Tokenization of solar energy production (1 MWh = 1 SolarToken)
- Green loan financing (70% of installation cost)
- Automated token minting based on energy production
- USDC payments for energy production
- Token burning for loan repayment

## Smart Contracts

1. `EnergyToken.sol`: ERC-20 token for solar energy
2. `EnergyOracle.sol`: Mock IoT data oracle
3. `EnergyAutomation.sol`: Automated token minting
4. `LoanContract.sol`: Green loan management
5. `EscrowContract.sol`: USDC payment handling

## Setup

1. Install dependencies:
```bash
npm install
```

2. Create `.env` file:
```
PRIVATE_KEY=your_private_key
SNOWTRACE_API_KEY=your_snowtrace_api_key
```

3. Get testnet AVAX:
- Visit https://faucet.avax.network
- Request testnet AVAX

4. Deploy contracts:
```bash
npx hardhat run scripts/deploy_poc.js --network fuji
```

5. Run tests:
```bash
npx hardhat test
```

## Demo Flow

1. Deploy contracts to Fuji testnet
2. Update energy reading in EnergyOracle (1.5 MWh)
3. Mint tokens through EnergyAutomation
4. Deposit USDC payment to EscrowContract
5. Burn tokens and claim payment through LoanContract

## API

Mock IoT API endpoint: `/api/energy`
Returns:
```json
{
  "energyWh": 1500000,
  "timestamp": "2024-03-14T12:00:00Z",
  "deviceId": "SOLAR-001",
  "location": "London, UK"
}
```

## Security Considerations

- All contracts use OpenZeppelin's audited contracts
- Role-based access control for sensitive operations
- Automated testing for critical functions
- Escrow mechanism for secure payments

## License

MIT 