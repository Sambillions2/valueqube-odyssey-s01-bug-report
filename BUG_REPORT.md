# ValueQube Qube Odyssey S01 Bug Report

## Title

**qtUSDC faucet claim remains in “Confirming” state for approximately five minutes and silently resets without dispensing tokens**

## Summary

The qtUSDC faucet in Qube Odyssey S01 does not successfully complete a claim.

When **Claim 1,000 qtUSDC** is selected, the interface changes to **Confirming** and remains in that state for approximately five minutes. It then returns to the normal **Claim 1,000 qtUSDC** button without crediting the requested qtUSDC and without displaying an actionable error message.

The same dashboard wallet successfully received the available tBNB test asset, while the qtUSDC balance remains at `0 qtUSDC`.

## Affected Feature

- **Product:** ValueQube Qube Odyssey S01
- **Feature:** Claim S01 test assets
- **Affected asset:** qtUSDC
- **Claim amount:** 1,000 qtUSDC

## Wallet Address

`0x92C459bd458028a92Acd680287630dd7583B839C`

## Reproduction Steps

1. Open Qube Odyssey S01.
2. Sign in using Google authentication.
3. Use the wallet displayed by the ValueQube dashboard after authentication.
4. Navigate to **Claim S01 test assets**.
5. Locate the **qtUSDC** claim card.
6. Confirm that it displays:
   - **Per claim:** `1,000 qtUSDC`
   - **Wallet balance:** `0 qtUSDC`
   - **Next claim:** `Available now`
7. Click **Claim 1,000 qtUSDC** once.
8. Observe that the button changes to **Confirming**.
9. Wait approximately five minutes.
10. Observe that the interface returns to **Claim 1,000 qtUSDC**.
11. Check the qtUSDC wallet balance.
12. Confirm that the balance remains `0 qtUSDC`.

## Expected Result

The qtUSDC claim should complete successfully and **1,000 qtUSDC should be credited to the dashboard wallet**.

If the claim cannot be completed, the application should provide a clear and actionable error explaining the failure.

## Actual Result

The claim enters a **Confirming** state for approximately five minutes.

It then silently returns to the default **Claim 1,000 qtUSDC** state.

No qtUSDC is credited, and the displayed wallet balance remains:

`0 qtUSDC`

No actionable error explaining why the claim failed is displayed.

## Control / Comparison

The same dashboard session successfully received the tBNB test asset:

- **tBNB balance:** `0.005 tBNB`
- **Status:** `tBNB received`

This demonstrates that the authenticated dashboard was able to receive another S01 test asset while the qtUSDC claim remained unsuccessful.

## Testing Environment

- **Operating system:** Windows
- **Browser:** Google Chrome
- **Authentication:** Google account
- **Platform:** ValueQube Qube Odyssey S01
- **Affected flow:** qtUSDC faucet claim
- **Wallet:** Dashboard-displayed wallet address listed above

## Supporting Evidence

### Evidence 1 — qtUSDC claim state

The qtUSDC claim card displayed:

- `Per claim: 1,000 qtUSDC`
- `Wallet balance: 0 qtUSDC`
- `Next claim: Available now`
- `Claim 1,000 qtUSDC`

### Evidence 2 — Successful tBNB receipt

The tBNB card displayed:

- `Wallet balance: 0.005 tBNB`
- `Status: tBNB received`

### Evidence 3 — qtUSDC failed claim behavior

Observed sequence:

**Claim 1,000 qtUSDC → Confirming → approximately 5 minutes → Claim 1,000 qtUSDC**

The qtUSDC balance remained `0 qtUSDC`.

## Additional Observation

Chrome DevTools displayed several console warnings/errors during testing, including Content Security Policy messages and browser content-script warnings.

These observations are **not identified as the root cause** of the qtUSDC failure because their causal relationship to the faucet behavior was not established.

## Impact

Users may be unable to obtain the qtUSDC test settlement asset through the advertised S01 faucet flow.

This can prevent or interrupt Odyssey activities that require qtUSDC, while the interface provides no actionable explanation after the claim attempt fails.

This issue concerns a test asset with no monetary value; no financial loss is being claimed.

## Suggested Investigation

The ValueQube team could investigate the qtUSDC claim flow around the transition from **Confirming** back to **Claim**, including whether the claim request is successfully created, processed, and reflected in the dashboard wallet balance.

## Reproducibility

**Observed repeatedly:** Yes.

The same behavior was observed across multiple qtUSDC claim attempts: the claim entered **Confirming**, remained there for several minutes, and then returned to the claim button without increasing the qtUSDC balance.

---

**Wallet:** `0x92C459bd458028a92Acd680287630dd7583B839C`

**Affected asset:** qtUSDC

**Claim amount:** 1,000 qtUSDC
## Video Evidence

[View the full reproduction video](Recording 2026-08-17 141257-compressed.mp4)
