# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repo Is

Static marketing/legal pages for two iOS apps, deployed via GitHub Pages at `expenselyapp.com`:

- **Landlord Ledger** — rental property receipt, expense, and mileage tracker (Xcode project name `SnapReceipt`, a separate repo not checked out here).
- **Invoice Ledger** — invoices, estimates, and jobs for tradespeople (separate app, separate repo, not checked out here).

No app code lives in this repository.

## Layout

```
index.html, privacy-policy.html, support.html, icon.png   — root-level copies (Landlord Ledger content)
landlordledger/  — index.html, privacy-policy.html, support.html, icon.png  (Landlord Ledger, current)
invoiceledger/   — index.html, privacy-policy.html, support.html, icon.png  (Invoice Ledger)
```

**Known duplication, not yet resolved:** the root-level `index.html` / `privacy-policy.html` / `support.html` currently have the *same* `<title>`s and near-identical content to `landlordledger/`'s copies — they were never consolidated when `landlordledger/` and `invoiceledger/` were split into per-app subfolders. The Landlord Ledger app itself links to `landlordledger/privacy-policy.html` (confirmed canonical as of September 2026), **not** the root-level one. When editing Landlord Ledger copy, treat `landlordledger/` as the source of truth and check whether the root-level duplicate also needs the same edit — don't assume they're kept in sync automatically, since nothing enforces that today.

## Development

No build tools, no dependencies, no package manager. Edit HTML files directly (each is self-contained with an embedded `<style>` block, no external CSS/JS) and open in a browser to preview.

To deploy: push to `main` branch — GitHub Pages deploys automatically.

## Shared Structure

Every page (`index.html`, `privacy-policy.html`, `support.html`, across both `landlordledger/` and `invoiceledger/`) follows the same template: a `.topnav` linking Home/Support/Privacy Policy, a gradient `header` with the app icon and title, `main` content, and a matching `footer`. CSS variables in `:root` (`--green`, `--accent`, `--text`, `--muted`, `--bg`, `--card`) drive the color theme — Landlord Ledger and Invoice Ledger each use their own palette. Responsive breakpoint at `820px`.

## Contact Email

Support/privacy contact is `expensely.app@gmail.com` (previously had a typo as `@google.com` in `landlordledger/` — fixed September 2026; double-check for the same typo before trusting any `mailto:` link you haven't already verified in a given file).

## Domain

`CNAME` contains `expenselyapp.com` for GitHub Pages custom domain routing. Do not edit unless intentionally changing the domain.

## Keeping Privacy/Support Copy Accurate

These pages describe the apps' actual data-handling behavior (App Store privacy review reads them). When an app's storage/sync model changes, this repo's copy needs a matching update — it's a separate git repo from the app, so it's easy to forget. Landlord Ledger, for example, added optional iCloud sync (`NSPersistentCloudKitContainer`) on top of its original local-only storage; `landlordledger/privacy-policy.html`, `support.html`, and `index.html` were updated accordingly in September 2026.
