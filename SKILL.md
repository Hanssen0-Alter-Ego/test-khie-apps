---
name: test-khie-apps
description: Test any Khie-compatible CKB application through the CCC App private-key wallet and Nervos testnet faucet. Use for browser-based wallet connection, testnet transaction and UI behavior checks, or reproducing Khie integration problems. Not limited to NervDAO.
---

# Test Khie-compatible apps

Use the target application's normal browser UI, CCC App as a disposable testnet wallet, and Khie as their connection. Adapt the application-specific assertions rather than assuming a NervDAO workflow.

## Authorization and safety

- Confirm the user's target application, test scope, and authorization for wallet connection and testnet transactions. This skill is procedure, not standing permission.
- Never use mainnet funds, a real wallet, a production mutation, or a user's existing private key for this workflow. Stop on ambiguous network or an action outside the authorized scope.
- Generate a fresh disposable key using CCC App's **RANDOM** control. Keep **Show private key** off. Do not read, copy, log, save, screenshot, publish, or ask the user to send the private key. Do not export it to a script or use it on another origin.
- Pairing URLs contain a secret. Treat them as transient connection credentials: transfer only between the intended target app and wallet, never include them in reports, artifacts, screenshots, logs, or public comments.
- Solve CAPTCHA only with required user authorization. Do not bypass browser warnings, denials, permissions, or anti-bot restrictions. No new persistent access is implied.

## Establish provenance

1. Identify the exact app URL, repository, merged or preview commit, and network. Obtain deployment evidence from trusted repository checks/deployments; a green deployment alone does not prove behavior.
2. Verify the official wallet URL from the CCC repository documentation: `https://app.ckbccc.com/`. The Khie module is `https://app.ckbccc.com/#khie`.
3. Observe the actual UI and confirm **CKB TESTNET** before generating a wallet or connecting. Recheck the requested network in the wallet connection prompt. Record only non-secret version and network evidence.

## Create and pair a disposable wallet

1. In CCC App select **Khie**, then **Enter private key**, **RANDOM**, and **CONTINUE**. The warning says this key is page-local and cleared on leave/reload; never rely on recovering it later.
2. Wait for **LIBP2P NODE READY**, relay connected, a `ckt...` address, and balance. Do not mistake node startup for successful app pairing.
3. In the target app open its wallet selector and choose **Khie**.
4. Prefer copying the target app's **connector pairing code** into CCC App's **Connector pairing code** field. Use the documented browser clipboard, keep the value in transient memory, and never print it. Click **Connect** only when enabled.
5. Approve the connection only after verifying the intended application and `ckb-testnet` request. Check both ends: the wallet should show the intended peer active and signer connected; the application must display the correct connected address or wallet UI.
6. The reverse direction may also be supported: wallet provider code into the application's wallet-code field. Formats vary with deployed versions. A disabled Connect button is not successful pairing; record the exact versions and try the supported reciprocal direction without changing network or broadening permissions.
7. If clipboard paste is empty, verify copy via the documented browser locator and clipboard APIs rather than extracting storage or secrets. Do not request camera access merely to avoid clipboard troubleshooting.

## Fund and test

1. Use the public test address at `https://faucet.nervos.org/`, only after confirming it is the intended testnet wallet. Respect faucet rate limits and CAPTCHA gates.
2. Verify the faucet request result and actual on-chain funding separately; retain transaction hash/public explorer URL and observed balance, not secret material.
3. Exercise a minimal, bounded application action. Inspect requested recipients, network, amount, fee, and purpose before signing; stop for any missing authorization. Reserve sufficient balance for fees and necessary cell capacity.
4. Verify the result in the application and a trusted testnet explorer/RPC. Submission or transaction assembly is not confirmation. Record pending, rejected, and committed states accurately.
5. Test relevant cancellation, invalid/insufficient input, repeat-action, back/navigation, refresh/reconnect, and error-recovery paths. Avoid destructive tests or unwanted duplicate transactions. Page reload can erase a disposable wallet; finish dependent checks before reloading it.
6. For time-locked or multi-phase protocols, report exactly which stage completed. Do not claim final withdrawal, redemption, or maturity behavior without actually testing it.

## Evidence and completion

- Record app URL, exact deployment/commit evidence, wallet/app versions if available, testnet, steps, expected versus observed results, public transaction references, and coverage gaps.
- Capture only useful authentic screenshots. Inspect each before sharing; exclude private keys, pairing codes/QRs, account secrets and unrelated personal content. Do not alter pixels that prove the result.
- Do not call an incomplete run a pass. Browser recovery, missing funding, or unavailable deployment evidence is a limitation, not automatically an application defect.
- Keep app behavior evidence distinct from source-code hypotheses. Reproduce failures and seek counterevidence before claiming a defect.
- At the end unpair/disconnect only this test session when appropriate; never clear unrelated browser data. Do not persist disposable secrets in this skill.
- Publishing comments, screenshots, or reports requires the applicable user authorization and destination checks; this skill does not grant it.

Read [the validation record](references/validation.md) for which parts have actually been exercised and which remain unverified.
