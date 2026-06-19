# Stake9ja Roadmap & Next Tasks

This document contains the initial roadmap and prioritized task list for the Stake9ja MVP (first sprint & follow-ups). It was generated after the initial scaffold push.

Sprint 0 — Setup & Secrets (Immediate, 1–2 days)
- Add repository secrets (GitHub Settings → Secrets):
  - PAYSTACK_SECRET (Paystack secret key)
  - SPORTSRADAR_KEY, STATSPERFORM_KEY, RAPIDAPI_KEY
  - DATABASE_URL
  - REDIS_URL
  - JWT_SECRET
  - PRIVATE_KEY (for smart-contract deployment)
  - MUMBAI_RPC_URL (for Polygon Mumbai)
  - SENTRY_DSN (optional)
- Upload high-resolution SVG logo to /assets/logo/stake9ja.svg
- Configure branch protection policies for main (optional)

Sprint 1 — Core Backend + Auth + Wallet (2–3 weeks)
- Implement Auth module (register/login/refresh + JWT + TOTP 2FA stub)
- Implement User profile endpoints
- Implement Wallet module: create wallet on user registration, deposit intent flow, Paystack webhook verification endpoint
- Implement Transactions ledger and DB hooks
- Create E2E test for deposit + webhook flow using Paystack test keys

Sprint 2 — Betting Engine (3–4 weeks)
- Implement Markets & Selections ingestion pipeline (sports-data connectors stub)
- Implement Bet placement endpoint (/bets/place) with validation, reservation of wallet balance, and stored bet record
- Implement Worker-based settlement job (BullMQ stub) and idempotent settlement
- Implement Bet settlement ledger (payouts, fees, reserve contributions)

Sprint 3 — Realtime + Frontend MVP (2–3 weeks)
- Socket.IO gateway for live odds and match updates
- Frontend: login, dashboard, event list, market view, bet slip, wallet pages
- PWA manifest + service worker

Sprint 4 — KYC + Withdrawals + Admin (2–3 weeks)
- Upload KYC documents, OCR pipeline (Onfido/Trulioo or Tesseract fallback)
- Admin KYC queue + manual review UI
- Withdrawal request flow + admin approval UI

Sprint 5 — Smart Contracts & On-Chain Staking (3–4 weeks)
- Finalize Solidity contract (stake/selectWinners/settleRound/withdrawAdminFees)
- Unit tests (Hardhat) + deployment script to Mumbai
- Reconciliation jobs between on-chain events and backend ledger

Sprint 6 — Production Hardening & Compliance
- Security testing (SAST/DAST), pen-test
- Monitoring & logging (Prometheus/Grafana, ELK or Loki)
- Backup & DR configuration
- Legal & AML processes (jurisdiction-specific)

Acceptance criteria for MVP:
- Users can register, verify email, login
- Users can deposit via Paystack (test flow verified) and see balance
- Users can view live events and markets (mock or provider data)
- Users can place bets and see pending/settled status
- Admins can process withdrawals and KYC requests
- Smart contract skeleton exists and can be deployed to Mumbai testnet

How to prioritize / next decisions for you:
- Provide high-resolution SVG logo
- Confirm payment providers (Paystack confirmed)
- Provide sports-data provider API keys (set as GitHub Secrets)
- Confirm which features to include in MVP vs later phases (e.g., on-chain payouts immediate or delayed)

