# Changelog

All notable changes to `komma-softhouse/filament-btcpay` are documented here. The format follows Keep a Changelog and the project follows SemVer.

## [1.0.1] - 2026-09-20

### Changed

- Dashboard rebuilt: settled this month with 14-day trend and month-over-month, awaiting payment in amount, payouts to approve, wallet balance; full-width stacked on-chain/Lightning chart with the invoice count; latest invoices table widget.
- Row actions on every live-data page grouped in a menu, so tables no longer overflow.
- Actions with a form open as regular modals instead of confirmation dialogs; Lightning pay dialog labels aligned.
- *New address* on the wallet explained in place and in the help; pull payment methods read from both Greenfield shapes.

## [1.0.0] - 2026-09-20

### Added

- Settings page in three steps: server URL with test, **Connect with BTCPay** (BTCPay's authorize flow, key stored encrypted, store picked on BTCPay's side) or a pasted key with test, and one-click webhook registration with a fresh secret.
- Invoice defaults: currency, confirmation policy (0, 1, 2, 6 blocks), expiry and late-payment windows, redirect after payment, checkout language, payment methods offered.
- Bitcoin invoices resource: list with status, paid amount and method, filters; view with checkout link and QR, payments received, linked record; refresh from BTCPay, mark settled or invalid, archive and restore, open in BTCPay.
- **New invoice** dialog for payments typed by hand and **Pay with Bitcoin** action for any resource whose model implements `Payable`.
- `Btcpay` facade: `createInvoice()`, `checkoutFor()`, `find()`, `sync()`, `mark()`, `archive()`, `rate()`, `client()`; `resolveConnectionUsing()` for multi-tenant hosts and `beforeCreating()` veto.
- Webhook endpoint with `BTCPay-Sig` verification, store check, delivery log and idempotent processing, inline or on a queue; seven invoice events for the host.
- Dashboard widgets: settled this month, awaiting payment, expired in 30 days, 12-week volume chart.
- Commands: `btcpay:selftest`, `btcpay:sync`, `btcpay:webhook:register`, `btcpay:prune`, `btcpay:license`.
- Settings page also carries **store policies** (payment tolerance, network fee mode, suggested fee, countdown, sound, Lightning options, support link, external CSS, anyone-can-create-invoice), **exchange rates** (source and spread, rate now) and **checkout appearance** (store name, logo, brand colour, browser title, default method, header, Pay-in-wallet button, confetti, receipt, payer e-mail), all written to the store on BTCPay on save.
- **Wallet** page: on-chain balances, receive address with QR, transactions with labels and notes, send from a hot wallet with confirmation target and RBF, new address.
- **Lightning** page: node info and URIs, balances, channels, invoices received and payments sent, new BOLT11 invoice with QR, pay a BOLT11 invoice, deposit address, open channel.
- **Refund** action on settled invoices: paid amount, invoice amount at today's rate, in fiat, or custom; on-chain or Lightning; percentage kept as fee. Creates the pull payment and shows the claim link.
- **Pull payments** page: create with amount, currency, validity, payout methods and auto-approval; public claim link; archive.
- **Payouts** page: every claim and direct payout with approve, cancel, mark paid; direct payouts to an address; payout processors of the store.
- **Payment requests** page: create, edit, archive hosted pages that ask for an amount, with expiry and partial payments; public link and payer e-mail.
- **Pay button & POS** page: HTML snippet generator for a pay button (fixed or free amount) and Point of Sale apps with items, layouts, tips and discounts.
- **Reports** page: BTCPay's payments, invoices and products reports for a period, totals per currency, CSV download.
- **Stores** resource: additional BTCPay stores with their own key and webhook, Connect per store, and a store switcher in the header of every page; invoices filter by store; webhook deliveries verified with the secret of their store.
- Store events for the host: `RefundCreated`, `PayoutApproved`, `PayoutPaid`, `PaymentRequestCompleted`.
- Plugin modules: `everything()`, `wallet()`, `lightning()`, `paymentRequests()`, `pullPayments()`, `payouts()`, `apps()`, `reports()`, `stores()`, plus `brandingDisk()`.
- Abilities: `refund-invoice`, `manage-wallet`, `send-from-wallet`, `manage-lightning`, `manage-payment-requests`, `manage-payouts`, `view-reports`, `manage-stores`.
- **Receipt page** of the application at `/btcpay/return/{invoice}`: branded with the checkout logo and colour, heading, message, button, order reference and payments, polling until the payment confirms; the default redirect for every invoice, or a URL of your own.
- Settings page organised in tabs: Connection, Invoices, Store policies, Exchange rates, Checkout.
- English and Spanish translations; slide-over help on every page.