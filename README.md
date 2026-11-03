# USDT Yield Board · กระดานผลตอบแทน USDT (ส่วนตัว)

เว็บหน้าเดียว (ไฟล์ `index.html` ไฟล์เดียว ไม่มีเซิร์ฟเวอร์ ไม่เก็บกุญแจ) สำหรับดูและย้าย USDT บน **BNB Chain + Arbitrum** ผ่าน **MetaMask**
เว็บจริง: https://boonkarnariyarit6.github.io/usdt-yield/

> **ทุกธุรกรรมต้องกดยืนยันใน MetaMask เองทีละรายการ** หน้านี้ส่งหรือเซ็นอะไรเองไม่ได้ · อนุมัติ (approve) เฉพาะจำนวนพอดี ไม่อนุมัติไม่จำกัด · ไม่ใช่คำแนะนำการลงทุน DeFi มีความเสี่ยงสูญเงิน

## ฟีเจอร์
- **อันดับผลตอบแทน USDT** จาก DefiLlama + สัญญาจริง พร้อม **เกรดความเสี่ยง A–E** และย้ายเงินคลิกเดียว (ถอน → อนุมัติพอดี → ฝาก) ใน 7 แพลตฟอร์มที่ตรวจสัญญาแล้ว (Aave v3, Venus Core, Compound v3, Fluid)
- **ภาพรวมพอร์ต** ทั้ง 2 เครือข่าย เป็น USD และบาท (อัตรา USD/THB จาก frankfurter.dev) พร้อมกำไร/ขาดทุน 24 ชม. / 7 วัน / 30 วัน / ตั้งแต่เริ่มบันทึก / เทียบเงินต้นที่ใส่เอง (บันทึกในเบราว์เซอร์)
- **ค้ำ BTC กู้ USDT**: Aave v3 (Arbitrum, BNB), Venus Core (BNB, Arbitrum), Compound v3 (Arbitrum) ตารางดอกเบี้ยกู้/LTV/สภาพคล่อง/ส่วนต่าง, ตัววางแผน (LTV เป้าหมาย, HF, ราคาชำระบัญชี, กำไรสุทธิ), จำลองทั้งชุดก่อนทำ, กู้แล้วฝากต่อให้อัตโนมัติ (ไม่ฝากกลับเข้า Compound ที่กู้มา), คืนหนี้/ถอน BTC, แผงตำแหน่งกู้สีตาม Health factor
- **แจ้งเตือน** APY ต่ำกว่าเป้า, มีที่ดีกว่าบนเครือข่ายเดียวกัน, HF ต่ำ, ราคา BTC ต่ำ (Notification ของเบราว์เซอร์ + แถบบนหน้า, ส่งออก/นำเข้า JSON) — **ทำงานเฉพาะตอนเปิดหน้านี้ค้างไว้**
- **Pendle อัตราคงที่ (ดูอย่างเดียว)**: รายการตลาด PT บน Arbitrum/BNB พร้อมลิงก์ไป app.pendle.finance (ตอนนี้ไม่มี PT ที่อ้างอิง USDT โดยตรง มีแต่สเตเบิลสังเคราะห์ หน้าเว็บบอกตรง ๆ)
- **แบ่งเงินตามสัดส่วน (Rebalance)**: ตั้ง % เป้าหมายต่อแพลตฟอร์ม คำนวณขั้นการย้าย แล้วทำทีละขั้นหรือทั้งหมดตามลำดับ (เครือข่ายเดียวกันเท่านั้น)

## Build / test (สำหรับนักพัฒนา)
`node build.mjs` → `index.html` (และ `dist/index.html`) · Lint: `npx eslint .`
Tests (live public RPC/API, ไม่มีการส่งธุรกรรมจริง):
- `node test/live.test.mjs` อ่านข้อมูล/จำลองถอน-ฝาก
- `node test/sequence.test.mjs` จำลองย้ายเงินครบชุดด้วย eth_simulateV1
- `node test/borrow.test.mjs` จำลองค้ำ BTC → กู้ → ฝาก และย้อนกลับ (+30 วัน) ทั้ง 5 แพลตฟอร์ม
- `node test/extras.test.mjs` คณิตของเกรดความเสี่ยง/แจ้งเตือน/พอร์ต/rebalance + API (frankfurter, Pendle, DefiLlama)
- `node test/ui.test.mjs` Chrome headless + MetaMask จำลองที่ **ปฏิเสธทุกธุรกรรม**

CSP อนุญาตเฉพาะ: DefiLlama (yields/api/coins), api-v2.pendle.finance, api.frankfurter.dev และ RPC สาธารณะของ BNB Chain/Arbitrum

## Verified contracts (official address books; verified on-chain 2026-11-01)
| Venue | Chain | Address(es) | Source |
|---|---|---|---|
| USDT (Binance-Peg, 18 dec) | BSC | 0x55d398326f99059fF775485246999027B3197955 | Aave & Venus address books |
| USD₮0 (6 dec) | Arbitrum | 0xFd086bC7CD5C481DCC9C85ebE478A1C0b69FCbb9 | Aave address book, Compound config |
| WBTC (8 dec) / BTCB (18 dec) | Arbitrum / BSC | 0x2f2a2543B76A4166549F7aaB2e75Bef0aefC5B0f / 0x7130d2A12B9BCbFAe4f2634d864A1Ee1Ce3Ead9c | Aave address books |
| Aave v3 Pool / aUSDT | Arbitrum | 0x794a61358D6845594F94dc1DB02A252b5b4814aD / 0x6ab707Aca953eDAeFBc4fD23bA73294241490620 | bgd-labs/aave-address-book AaveV3Arbitrum.sol |
| Aave v3 aWBTC / vDebtUSDT | Arbitrum | 0x078f358208685046a11C85e8ad32895DED33A249 / 0xfb00AC187a8Eb5AFAE4eACE434F493Eb62672df7 | same |
| Aave v3 Pool / aUSDT | BSC | 0x6807dc923806fE8Fd134338EABCA509979a7e0cB / 0xa9251ca9DE909CB71783723713B21E4233fbf1B1 | bgd-labs/aave-address-book AaveV3BNB.sol |
| Aave v3 aBTCB / vDebtUSDT | BSC | 0x56a7ddc4e848EbF43845854205ad71D5D5F72d3D / 0xF8bb2Be50647447Fb355e3a77b81be4db64107cd | same |
| Venus Core vUSDT / vBTC (comptroller 0xfD36E2c2a6789Db23113685031d7F16329158384) | BSC | 0xfD5840Cd36d94D7229439859C0112a4185BC0255 / 0x882C173bC7Ff3b7786CA16dfeD3DFFfb9Ee7847B | VenusProtocol/venus-protocol bscmainnet_addresses.json |
| Venus Core vUSDT_Core / vWBTC_Core (comptroller 0x317c1A5739F39046E20b08ac9BeEa3f10fD43326) | Arbitrum | 0xB9F9117d4200dC296F9AcD1e8bE1937df834a2fD / 0xaDa57840B372D4c28623E87FC175dE8490792811 | VenusProtocol/isolated-pools arbitrumone_addresses.json |
| Compound v3 cUSDTv3 (Comet, WBTC collateral) | Arbitrum | 0xd98Be00b5D27fc98112BdE293e487f8D4cA57d07 | compound-finance/comet deployments/arbitrum/usdt |
| Fluid fUSDT (ERC-4626) | Arbitrum | 0x4A03F37e7d3fC243e3f99341d36f4b829BEe5E03 | Instadapp/fluid-contracts-public deployments.md |
| Fluid fUSDT (ERC-4626) | BSC | 0xA5b8FCa32E5252B0B58EAbf1A8c79d958F8EE6A2 | same |
