---
name: personal-cfo-setup
description: Create or join a household's Personal CFO data foundation in Google Drive and connect its financial-data sources.
---
# Personal CFO Setup

This is the beginner-friendly data-foundation entry point to Personal CFO. Help the user create or join a private, organized financial record in Google Drive. Do not assume the user understands plugins, spreadsheets, syncing, data warehouses, or financial terminology.

## The promise

Start with: "I’ll connect or create your private financial home base. Once it is ready, the other Personal CFO tools can use it for reports, reviews, and planning."

Call the underlying record a **private financial record**, never a warehouse unless the user asks for technical detail. Explain that their data stays in their connected accounts and Google Drive, subject to the permissions they approve.

## Setup flow

Work through one step at a time. Do not show a checklist of technical requirements up front.

### 1. Choose the setup path

Before creating anything, ask: "Is this a brand-new Personal CFO setup for your household, or are you joining a Personal CFO setup that someone else has already created?"

For a new household setup, continue with the normal setup flow.

For an existing household setup, stop creation work and ask: "Where does your household keep its budget and financial information?" Have the person who manages that information share its Google Drive folder with the joining user's Google account, then ask for the folder's Google Drive link or folder ID. Confirm that it is the intended household record before reading it. Use that folder ID as the source for Personal CFO queries. Preserve its existing workbook, history, manual entries, and folder structure; do not create a second record, replace the baseline, or rerun first-time setup over it.

Create or update one native Google Doc in that top-level folder named `Personal CFO Home`. It contains only the folder ID and folder URL, labeled as the active household budget-and-financial-information location. This is the persistent locator that other Personal CFO plugins use in future chats.

Once the folder ID and locator are confirmed, integration is complete. Do not ask the joining user to connect Finances, run the first-time sync, create a folder, or complete the first-time setup questions. Explain any limitation if their Google Drive account cannot access the shared folder.

### 2. Connect only what is needed

This step is for a new household setup only.

Ask the user to connect Finances and Google Drive when they are not already connected. In plain language, explain why each is needed:

- Finances provides connected-account activity and balances.
- Google Drive stores the user's private financial record, supporting documents, and history.

Never ask the user to paste account numbers, passwords, or sensitive credentials into the chat. If a connector is unavailable, explain the limitation and offer a document or CSV-based starting point only if supported by the current surface.

### 3. Choose a private location

This step is for a new household setup only.

Ask one simple question: "Would you like me to create a `Personal CFO Data` folder in Google Drive, or use an existing folder?"

If the user chooses an existing folder, ask them to select or link it. If they choose a new folder, confirm that it will contain a spreadsheet named `Financial Data Warehouse` plus their supporting records. Do not expose IDs or require the user to edit configuration.

Then ask: "Do you already have a Google Sheet you want to use as your financial record?" If yes, ask them to share or paste its Google Sheet link and confirm it belongs in the selected folder. If no, explain that Setup will create `Financial Data Warehouse` in that folder.

### 4. Confirm before account-specific analysis

This step is for a new household setup only.

Before reading account-specific facts, summarize the intended handoff: the selected Drive location, connected source names, and whether this is a first-time or refresh setup. Ask for confirmation that this is the user's own financial data. Reuse confirmation already given in the same thread.

### 5. Build the private financial record

This step is for a new household setup only, after the user has connected their accounts and chosen the Drive folder.

Pass the selected top-level folder as `target_folder_id` or `target_folder_url`. When the user provided a Google Sheet, also pass it as `warehouse_spreadsheet_id` or its Google Sheet URL. Then read and follow [financial-warehouse-sync.md](references/financial-warehouse-sync.md). It uses the provided Sheet when it is a live Google Sheet inside the selected folder; otherwise, when no Sheet was provided, it safely creates `Financial Data Warehouse` there. It then imports the available history, preserves manual values and stale-but-known facts, and verifies the result.

Do not turn its technical checkpoints into user tasks. If it reports a blocking ambiguity, translate it clearly. Example: "I found two possible Personal CFO folders. To avoid putting information in the wrong place, please choose the one you want to use."

### 6. Create the Personal CFO Home locator

After the sync has successfully resolved the canonical record, create or update one native Google Doc inside the selected top-level budget-and-financial-information folder named `Personal CFO Home`. It contains only:

- `Active Personal CFO folder ID: <folder ID>`
- `Active Personal CFO folder URL: <folder URL>`

Verify the document is in the selected top-level folder. This locator is not a financial report and must not contain balances, transactions, account numbers, or credentials. Future Personal CFO plugins resolve this exact document when the folder is not already identified in the current chat. That resolved folder is their working scope for the household's warehouse, uploaded files, and supporting documents.

### 7. Give a human completion summary

For a new household setup, report only what a household needs to know:

- whether the private financial record is ready;
- the number of accounts and the available transaction period, when known;
- any accounts that need reconnecting;
- any important data gaps; and
- that `Personal CFO Home` is ready for the other Personal CFO plugins.

Never imply that absent, stale, or login-required data is zero or closed. Do not expose unnecessary account numbers, spreadsheet IDs, audit hashes, raw provider IDs, or internal tab names.

## Ongoing use

Explain the system in one short paragraph: account data can be refreshed through connected Finances, the private record lives in the user's Drive, and the other Personal CFO tools automatically look for `Personal CFO Home` when a new chat does not already identify the folder. Ask before creating a recurring refresh schedule.

## Safety boundaries

Do not make investment trades, provide individualized investment instructions, calculate a final tax liability, certify a deduction, give legal advice, or claim professional suitability. Label conclusions as observations, calculations, user-provided facts, assumptions, or unavailable information. Treat connector failures as data gaps, not evidence that an account or value disappeared.
