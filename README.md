# USDT Yield Board (personal, static, no server)
Open `index.html` (single self-contained file, ethers v6.17 bundled). Build: `node build.mjs`. Lint: `npx eslint .`.
Tests (live, public RPC + DefiLlama): `node test/live.test.mjs`, `node test/sequence.test.mjs` (eth_simulateV1 full move sequences), `node test/ui.test.mjs` (headless Chrome + mock wallet that rejects every send).

## Verified contracts (source = official address book; verified on-chain 2026-11-01: code present, underlying == USDT)
| Venue | Chain | Address(es) | Source |
|---|---|---|---|
| USDT (Binance-Peg, 18 dec) | BSC | 0x55d398326f99059fF775485246999027B3197955 | Aave & Venus address books |
| USD₮0 (6 dec) | Arbitrum | 0xFd086bC7CD5C481DCC9C85ebE478A1C0b69FCbb9 | Aave address book, Compound config |
| Aave v3 Pool / aUSDT | Arbitrum | 0x794a61358D6845594F94dc1DB02A252b5b4814aD / 0x6ab707Aca953eDAeFBc4fD23bA73294241490620 | bgd-labs/aave-address-book AaveV3Arbitrum.sol |
| Aave v3 Pool / aUSDT | BSC | 0x6807dc923806fE8Fd134338EABCA509979a7e0cB / 0xa9251ca9DE909CB71783723713B21E4233fbf1B1 | bgd-labs/aave-address-book AaveV3BNB.sol |
| Venus Core vUSDT | BSC | 0xfD5840Cd36d94D7229439859C0112a4185BC0255 (comptroller 0xfD36E2c2a6789Db23113685031d7F16329158384) | VenusProtocol/venus-protocol deployments/bscmainnet_addresses.json |
| Venus Core vUSDT_Core | Arbitrum | 0xB9F9117d4200dC296F9AcD1e8bE1937df834a2fD | VenusProtocol/isolated-pools deployments/arbitrumone_addresses.json |
| Compound v3 cUSDTv3 (Comet) | Arbitrum | 0xd98Be00b5D27fc98112BdE293e487f8D4cA57d07 | compound-finance/comet deployments/arbitrum/usdt/roots.json |
| Fluid fUSDT (ERC-4626) | Arbitrum | 0x4A03F37e7d3fC243e3f99341d36f4b829BEe5E03 | Instadapp/fluid-contracts-public deployments/deployments.md |
| Fluid fUSDT (ERC-4626) | BSC | 0xA5b8FCa32E5252B0B58EAbf1A8c79d958F8EE6A2 | same |
