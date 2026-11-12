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
