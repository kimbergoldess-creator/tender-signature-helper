# Tender Signature Helper (Single-File HTML)

A tiny, offline-friendly web tool to help teams decide **who must sign which tender documents** based on:
- Tender metadata (subject, customer, amount, business area, area manager)
- A role model (e.g., Legal Representative vs Delegates)
- Delegate authorization rules (area + max amount)
- A checklist of documents to send for signature (select only what you need)

## Why this exists

This tool was born out of real operational pain.

I have spent over 20 years working in commercial back-office and tender-related roles, where internal policies, signature rules, and authorization thresholds are often complex, fragmented, and poorly accessible to the people who actually need them on a daily basis.

In many organizations, commercial assistants are expected to:
- interpret internal policies and powers of attorney,
- remember thresholds and exceptions,
- and make correct decisions under time pressure,

even though these rules are usually documented in long, static documents that are rarely read, hard to interpret, and easy to misapply.

This project applies a **poka-yoke (error-proofing) approach** to a very specific niche problem:  
turning internal rules into deterministic, easy-to-use decisions that prevent mistakes before they happen.

The idea is deliberately simple:
instead of asking people to “understand the policy”, the system asks for a few structured inputs and returns a clear, actionable answer.

My background sits at the intersection of:
- **commercial operations** (20+ years in back-office and tender workflows),
- **social sciences** (political science, economics, and law),
- **logic and technology** (rule-based reasoning, structured decision flows, and AI-assisted development).

This cross-domain perspective is the real value behind the tool:
understanding how organizations work, how rules are created, and how humans actually interact with systems — then translating all of that into practical, usable logic.

This repository is not about building a large-scale platform.
It is about showing how small, well-designed tools can reduce cognitive load, prevent errors, and bridge the gap between policy, technology, and real work.


## Features
- One single file `index.html` (no build, no dependencies)
- Calculates signer:
  - **LEGAL_REPRESENTATIVE** (fixed signer)
  - **DELEGATE_X** (picked based on area + amount)
  - Conditional documents (delegate if authorized, otherwise legal representative)
- AM approval checkbox (AM OK to proceed) included in output
- Select only the documents you actually need to send for signature
- Generates:
  - A copyable **TSV table** (paste into Excel/Outlook)
  - A copyable **email-ready text block**

## Quick Start
1. Download or clone this repo
2. Open `app/index.html` in any modern browser (Chrome/Edge/Firefox)
3. Fill tender data, select documents, click **Calculate signers**
4. Copy TSV table / Copy email text

## Customization
Open `app/index.html` and edit the configuration section:

- `DELEGATES`  
  Add your delegates and authorization thresholds.
- `DOCUMENTS`  
  Add your document list and signature rule:
  - `LR` (always legal representative)
  - `DEL` (always delegate; picked by rules)
  - `COND_AMOUNT` (delegate if authorized, else legal representative)

Example rule meanings:
- `LR`: fixed signer
- `DEL`: signer chosen by delegate rules (area + amount)
- `COND_AMOUNT`: if delegate covers amount for that area => delegate; else => legal rep

## Data & Privacy
- Runs locally in the browser.
- No network calls.
- No server.
- No storage (no LocalStorage save/load buttons).

## License
MIT — do whatever you want, just keep the license notice.
