# Tender Signature Helper (Single-File HTML)

A tiny, offline-friendly web tool to help teams decide **who must sign which tender documents** based on:
- Tender metadata (subject, customer, amount, business area, area manager)
- A role model (e.g., Legal Representative vs Delegates)
- Delegate authorization rules (area + max amount)
- A checklist of documents to send for signature (select only what you need)

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
