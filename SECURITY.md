# Security Policy

## Supported versions

| Version | Supported |
| --- | --- |
| 1.x | ✅ |

Security fixes land on the latest 1.x release. Older tags are not patched.

## Reporting a vulnerability

Report privately, never in a public issue: open a
[security advisory](https://github.com/komma-softhouse/filament-btcpay/security/advisories/new)
on this repository, or write to **security@kommasofthouse.com**.

Please include the affected version, the steps to reproduce it, and what an
attacker could obtain or alter. A proof of concept helps, but a clear
description is enough.

What to expect:

- Acknowledgement within 3 working days.
- An assessment, with severity and a fix window, within 10 working days.
- Credit in the release notes when the fix ships, unless you prefer not to
  be named.

Please give us a reasonable window to release a fix before disclosing
publicly.

## Scope

The plugin can now move money out of the store — send from the wallet, pay Lightning invoices, open channels, create and approve payouts, refund invoices. Those actions sit behind the `send-from-wallet`, `manage-payouts` and `refund-invoice` abilities; a Gate named `btcpay.{ability}` decides per user. Reports of a way to reach them without the ability, or to make the panel act on a store the user did not select, are in scope.

This package creates payment invoices on a BTCPay Server and marks records
paid from its webhooks. Reports of the following are especially welcome:

- Anything that lets a webhook delivery be accepted without a valid
  `BTCPay-Sig`, replayed, or accepted for a store other than the
  configured one.
- Anything that lets an invoice be marked settled locally without BTCPay
  confirming it, or a settled invoice be altered.
- Anything that exposes the API key or the webhook secret, in storage,
  logs, responses or the connect callback.
- Anything that lets the connect callback be reached with a forged state
  and store an attacker's key, or send the browser to an attacker's URL.
- Anything that lets the "Pay with Bitcoin" action create invoices for
  records the user may not see.

Out of scope: findings that require an already-compromised host or
privileged access to the database, denial of service through resource
exhaustion, and vulnerabilities in BTCPay Server itself.
