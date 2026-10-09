# LAS and Physical NAV: functions and observable results

This document states **what** the assurance layer does and **what anyone can observe**. It intentionally omits **how** it decides. Rules, thresholds, tolerances and implementation are proprietary and are not published.

## LAS: Lindblad Assurance Standard

**Function.** LAS evaluates signed evidence about a physical lot and returns a deterministic verdict.

**Observable properties:**
- **Deterministic:** the same evidence always produces the same result.
- **Independent sources:** the third-party path used in the demonstration requires evidence from **three independent, authorized sources**: warehouse, weighing and laboratory. All three are mandatory, and if one is missing the result is not VERIFIED.
- **Authorized issuers only:** evidence counts only if its issuer was activated beforehand through a 2-of-3 Safe approval.
- **Hash-anchored:** every evidence item and every result is identified by its hash.
- **No device required:** the third-party path works without hardware attestation. Device attestation is an optional additional assurance path and was **not** used in this demonstration.

**Result in the demonstration:** `VERIFIED`, with all checks passed and a certified quantity of **19.950 t**.

## Physical NAV

**Function.** Physical NAV states the quantity of the lot that is **eligible to back tokens**.

**Observable properties:**
- It **never exceeds** the certified quantity.
- It is backed by **one active allocation**, and issuance is bound to that allocation.
- Tokens issued can never exceed the allocated quantity.

**Result in the demonstration:** **19.900 t ELIGIBLE**, with one active allocation of 19.900 t, of which 1.000 t backs the 1.000 tLICO issued.

> The difference between the certified quantity (19.950 t) and the eligible NAV (19.900 t) results from the proprietary eligibility rules. It is not an assertion about physical loss, quality or market value.

## What is not claimed

- No claim that a real lot exists. Lot and issuers are **synthetic**.
- No claim of legal title, custody, insurance or regulatory recognition.
- No claim about market value. Physical NAV is a **quantity**, not a price.
