# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repo Is

A static marketing/landing page for the Expensely iOS app (receipt scanning and expense tracking). Deployed via GitHub Pages at `expenselyapp.com`. The actual app code is not in this repository.

## Development

No build tools, no dependencies, no package manager. Edit HTML/CSS files directly and open in a browser to preview.

To deploy: push to `main` branch — GitHub Pages deploys automatically.

## Architecture

Two pages, each a self-contained HTML file with embedded `<style>` blocks (no external CSS files, no JavaScript):

- [index.html](index.html) — Marketing landing page with features grid, privacy callout, and App Store CTA
- [privay-policy.html](privay-policy.html) — Privacy policy (note: filename has a typo — "privay" not "privacy", but `index.html` links to this exact filename so do not rename without updating the link)

CSS uses variables defined in `:root` for the green color theme (`--green`, `--accent`, `--text`, `--muted`, `--bg`, `--card`). Responsive breakpoint at `820px`.

## Domain

`CNAME` contains `expenselyapp.com` for GitHub Pages custom domain routing. Do not edit unless intentionally changing the domain.
