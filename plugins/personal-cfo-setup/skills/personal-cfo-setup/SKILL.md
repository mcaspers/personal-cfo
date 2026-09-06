---
name: personal-cfo-setup
description: Create or join a household's Personal CFO data foundation in Google Drive, then hand off first-time financial syncing to ChatGPT on the web.
---
# Personal CFO Setup

This is the beginner-friendly data-foundation entry point to Personal CFO. Help the user create or join a private, organized financial record in Google Drive. Do not assume the user understands plugins, spreadsheets, syncing, data warehouses, or financial terminology.

## The promise

Start with: "I’ll create or connect your private financial home base. Once it is ready, the other Personal CFO tools can use it for reports, reviews, and planning."

Call the underlying record a **private financial record**, never a warehouse unless the user asks for technical detail. Explain that their data stays in their connected accounts and Google Drive, subject to the permissions they approve.

## Setup flow

Work through one step at a time. Do not show a checklist of technical requirements up front.

### 1. Choose the setup path

Before creating anything, ask: "Is this a brand-new Personal CFO setup for your household, or are you joining a Personal CFO setup that someone else has already created?"

For a new household setup, continue with the normal setup flow.

For an existing household setup, stop creation work and ask: "Where does your household keep its budget and financial information?" Have the person who manages that information share its Google Drive folder with the joining user's Google account, then ask for the folder's Google Drive link or folder ID. Confirm that it is the intended household record before reading it. Use that folder ID as the source for Personal CFO queries. Preserve its existing workbook, history, manual entries, and folder structure; do not create a second record, replace the baseline, or rerun first-time setup over it.

Create or update one native Google Doc in that top-level folder named `Personal CFO Home`. It contains only the folder ID and folder URL, labeled as the active household budget-and-financial-information location. This is the persistent locator that other Personal CFO plugins use in future chats.

Once the folder ID and locator are confirmed, integration is complete. Do not ask the joining user to connect Finances, run the first-time sync, create a folder, or complete the first-time setup questions. Explain any limitation if their Google Drive account cannot access the shared folder.

### 2. Connect Google Drive

This step is for a new household setup only.

Ask the user to connect Google Drive when it is not already connected. Explain that it stores the user's private financial record, supporting documents, and history.

Do not ask the user to connect Finances in the desktop app. The first live import happens in ChatGPT on the web, where the user connects Finances later.

Never ask the user to paste account numbers, passwords, or sensitive credentials into the chat. If a connector is unavailable, explain the limitation and offer a document or CSV-based starting point only if supported by the current surface.

### 3. Choose a private location

This step is for a new household setup only.

Ask one simple question: "Would you like me to create a `Personal CFO Data` folder in Google Drive, or use an existing folder?"

Before creating a folder, look in the selected Drive location for an active folder named exactly `Personal CFO Data`.

- If exactly one exists, offer to use it. Do not create another folder with that name.
- If none exists, create one only after the user confirms the location.
- If more than one exists, stop and ask which one is the household's active record. Prefer the folder that already contains `Personal CFO Home` or `Financial Data Warehouse`, but do not choose or delete a folder silently.
- If Setup created an empty duplicate during the current chat, identify the chosen authoritative folder, then ask for explicit permission before moving that empty duplicate to Trash. Never delete a folder that contains files, a worksheet, or a `Personal CFO Home` locator.

If the user chooses an existing folder, ask them to select or link it. If they choose a new folder, confirm that it will contain a `Transactional Data` folder with a spreadsheet named `Financial Data Warehouse`, plus their supporting records. Do not expose IDs or require the user to edit configuration.

Then ask: "Do you already have a Google Sheet you want to use as your financial record?" If yes, ask them to share or paste its Google Sheet link and confirm it belongs in the selected folder's `Transactional Data` folder. If no, explain that Setup will create `Financial Data Warehouse` there.

### 4. Confirm the private location

This step is for a new household setup only.

Before creating files, summarize the selected Drive location and whether the user chose a new or existing Google Sheet. Ask for confirmation that it is their intended household location. Reuse confirmation already given in the same thread.

### 5. Create a simple document home

Inside the selected top-level folder, create these folders only when they do not already exist. Preserve any existing folders and organization.

- `Transactional Data` — exported statements, transaction files, and other day-to-day financial records.
- `Benefits & Insurance` — employer benefits, health coverage, life insurance, home, auto, and umbrella policies.
- `Debt & Credit` — loan, mortgage, credit-card, refinancing, and payoff records.
- `Estate & Legal` — trusts, wills, healthcare proxies, powers of attorney, and other legal documents.
- `Investments & Retirement` — IRA, 401(k), brokerage, pension, and investment-account documents.
- `Property & Vehicles` — home-value records, mortgage-related property documents, and vehicle-value records.

Explain in plain language: "You can upload copies of the financial documents you already have to the matching folders now or later. They are for your own record and for future Personal CFO work; they are not required before your first account-data sync."

Do not ask the user to upload passwords, account credentials, or documents they do not want stored in Drive. Do not move or rename existing user files without permission.

### 6. Create the private financial home

This step is for a new household setup only, after the user has connected Google Drive and chosen the Drive folder.

Use the selected top-level folder as the household's private location and use its `Transactional Data` subfolder as the financial-data location. When the user supplied a Google Sheet, verify that it is a live Google Sheet inside `Transactional Data` and preserve it. When no Sheet was supplied, create one native Google Sheet named `Financial Data Warehouse` inside `Transactional Data`. Verify the sheet's parent folder and active status.

Do not retrieve, analyze, or import financial-account data in this desktop setup. Leave a newly created sheet ready for the separate web sync skill to initialize and populate.

### 7. Create the Personal CFO Home locator

After the Drive location and spreadsheet are resolved, create or update one native Google Doc inside the selected top-level budget-and-financial-information folder named `Personal CFO Home`. It contains only:

- `Active Personal CFO folder ID: <folder ID>`
- `Active Personal CFO folder URL: <folder URL>`

Verify the document is in the selected top-level folder. This locator is not a financial report and must not contain balances, transactions, account numbers, or credentials. It is the durable grounding document that future Personal CFO plugins resolve when a chat does not already identify the household location. Tell the user not to delete it. That resolved top-level folder is their working scope; its `Transactional Data` subfolder contains the warehouse, while the other subfolders hold uploaded supporting documents.

### 8. Hand off the first live sync to ChatGPT on the web

For a new household setup, explain plainly that the private financial home is created but it does not contain live financial-account data yet. Then direct the user, one action at a time:

1. Open [ChatGPT on the web](https://chatgpt.com/finances) and connect Finances. Wait until the Finances page shows that account data has synced.
2. Open **Skills**, select **Create**, then **Upload from your computer**, and upload the separately supplied `financial-warehouse-sync.zip` package.
3. Start a new web chat, run **Financial Warehouse Sync**, and tell it: "Sync my connected financial data into the Financial Data Warehouse in my Personal CFO folder."
4. Give the web skill the selected Personal CFO folder or spreadsheet link if it asks. It automatically performs a read-only Finances readiness check, tells the user whether the connection is usable, and asks for a final confirmation before it writes live data into the spreadsheet.

Do not describe the household as fully set up until the web skill confirms a successful sync. Do not expose unnecessary folder IDs, spreadsheet IDs, account numbers, audit hashes, raw provider IDs, or internal tab names.

## Ongoing use

Explain the system in one short paragraph: the private record lives in the user's Drive; connected Finances data is synced into it from ChatGPT on the web; and the other Personal CFO tools automatically look for `Personal CFO Home` when a new chat does not already identify the folder. Ask before creating a recurring refresh schedule.

## Safety boundaries

Do not make investment trades, provide individualized investment instructions, calculate a final tax liability, certify a deduction, give legal advice, or claim professional suitability. Label conclusions as observations, calculations, user-provided facts, assumptions, or unavailable information. Treat connector failures as data gaps, not evidence that an account or value disappeared.
