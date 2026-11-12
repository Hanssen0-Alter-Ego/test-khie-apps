# Validation record

## 2026-11-12 partial browser run

- Target: `https://test.nervdao.com/`; repository merge commit `92e68309bdb0cc6005b2529581068b36a1206368` for PR #31. Its Netlify check `Netlify (develop - testnetvdao)` was successful. No claim that the loaded bundle was independently cryptographically matched to that commit.
- Official CCC App URL was verified from the repository README.
- Exercised CCC App Khie module, CKB TESTNET, private-key RANDOM, CONTINUE. Key stayed hidden; wallet displayed a testnet address, zero balance, relay connected and libp2p ready.
- Copying CCC App's provider URL into the target's wallet pairing field left Connect disabled. This is an observed compatibility limitation, not a proven regression or root-cause finding.
- Reciprocal direction succeeded: copied target connector code into CCC App, connected, saw NervDAO `Relayed · Active`, then `Direct · Active`; approved `Switch to network ckb-testnet`. CCC App reported `Signer connected`.
- The final target-app connected screen was not verified before environment disruption. Do not describe this as completed end-to-end wallet validation.
- Opening the faucet coincided with execution environment loss/recovery and an unresponsive browser operation. No faucet claim, funded balance, signed transaction, deposit, withdrawal, or end-to-end application behavioral pass was verified.
- No private keys, pairing URLs, QR codes, or session credentials are retained here. A later run must create/recover its own authorized session and independently verify each untested stage.

## 2026-11-12 recovered-session continuation

- Created a new disposable UI-only testnet signer after browser reset; reciprocal connector-code pairing completed again.
- Claimed the minimum offered faucet amount, 10,000 test CKB, without a CAPTCHA prompt. Explorer verified output to the disposable address with two confirmations in block 23,038,043: https://testnet.explorer.nervos.org/transaction/0x86f893c63d2c4fc55b9b582afe69dc4973a565135700b068542f5f9475400ff2 .
- Approved the explicit `ckb-testnet` connection. NervDAO displayed its Dashboard, the matching connected address, 10,000 CKB balance, zero deposited/redeeming balances, and no holdings. This completes the wallet-connection and funding UI check previously left unverified.
- Opened Make a Deposit. Empty input disabled Deposit. Entering `1` displayed a 0.00018671 CKB estimated fee and enabled Deposit. Attempting to click Deposit resulted in a browser protocol timeout. Subsequent target and wallet accessibility observations and target screenshot also timed out.
- The click outcome is uncertain; no wallet transaction-signing approval was performed. Do not infer that a transaction was sent or that accepting a below-capacity input is a proven application defect. Do not blindly repeat an uncertain action.
- Deposit confirmation, cancellation/error handling, redemption, withdrawal, repeated navigation, and reconnect persistence remain unverified. The browser-wide observation failure is an execution blocker, not an established app regression.

## 2026-11-12 follow-up and crash diagnosis

- Reconciled the earlier uncertain 1 CKB attempt: the prior wallet retained its original 10,000 CKB live cell, exactly one committed transaction (faucet), zero pending transactions, and zero DAO deposits. No deposit occurred.
- After a clean browser session, another disposable signer received 10,000 test CKB in transaction https://testnet.explorer.nervos.org/transaction/0xcf8b15a9512ab83b7bdae5e8a035950011296bfc624a314a7a03433b7de9930e (block 23,038,105, six confirmations observed).
- Pairing initially returned `All multiaddr dials failed`. Reloading only the target app and generating a fresh connector invitation recovered pairing while preserving the wallet page. Connection approval and the funded NervDAO dashboard worked.
- Entered 200 test CKB and observed fee estimate 0.00018671. After clarified user authority for this separate live test, clicking Deposit changed the button to disabled `To be confirmed`; no wallet signing approval was performed.
- Native desktop observation identified the subsequent blocker: both NervDAO and CCC App Chromium renderers displayed crash error code 9 (`Can't open this page` / `Aw, Snap!`). This is stronger evidence than protocol timeout but does not establish a root cause or a product regression. Do not infer out-of-memory without relevant browser-host diagnostics.
- Keep browser-control timeouts distinct from renderer crashes; use supported native screenshots when DOM observation is unavailable. Never retry a potentially submitted transaction without checking wallet/explorer state first. A crashed page-local signer cannot be recovered by reading browser secrets.
- The 200 CKB request remains unconfirmed and no deposit transaction hash was observed. Deposit, redemption, and withdrawal behavior remain unvalidated. No recurring monitor was created.
