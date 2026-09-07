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

When Google Drive is not connected, direct the user to open the desktop app's **Plugins** area, add or enable **Google Drive**, and complete the Google sign-in and permission screens. Link to [Google Drive app and setup in ChatGPT](https://help.openai.com/en/articles/10929079-google-drive-app-and-setup-in-chatgpt) for step-by-step help. Explain that it stores the user's private financial record, supporting documents, and history; their data remains in their connected accounts and Drive, subject to the permissions they approve. Then stop and ask the user to confirm when Google Drive is connected. Do not ask for a Drive location until they confirm.

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
- `Cash & Manual Spending` — optional receipts and other supporting documents for cash spending or spending that connected accounts cannot categorize. The household can explain cash use in conversation; no separate manual log is required.
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

After the Drive location and spreadsheet are resolved, explain that Setup will create a small `Personal CFO Home` document in the selected top-level folder. It is the durable locator that future Personal CFO tools use to find this household's private financial record; it is not a report or a place to keep household notes.

Create or update one native Google Doc inside the selected top-level budget-and-financial-information folder named `Personal CFO Home`. It contains only:

- `Active Personal CFO folder ID: <folder ID>`
- `Active Personal CFO folder URL: <folder URL>`

Verify the document is in the selected top-level folder. This locator is not a financial report and must not contain balances, transactions, account numbers, credentials, or lifestyle notes. Show the user its link and say: “`Personal CFO Home` is the small durable document that lets future Personal CFO tools find this household folder. Please do not edit its contents, rename it, move it, or delete it.” That resolved top-level folder is their working scope; its `Transactional Data` subfolder contains the warehouse, while the other subfolders hold uploaded supporting documents.

### 8. Hand off the first live sync to ChatGPT on the web

For a new household setup, explain plainly that the private financial home is created but it does not contain live financial-account data yet. Then direct the user, one action at a time:

1. Open [ChatGPT on the web](https://chatgpt.com/finances) and connect Finances. Wait until the Finances page shows that account data has synced.
2. Open **Skills**, select **Create**, then **Upload from your computer**, and upload the separately supplied `financial-warehouse-sync.zip` package.
3. Start a new web chat, run **Financial Warehouse Sync**, and tell it: "Sync my connected financial data into the Financial Data Warehouse in my Personal CFO folder."
4. Give the web skill the selected Personal CFO folder or spreadsheet link if it asks. It automatically performs a read-only Finances readiness check, tells the user whether the connection is usable, and asks for a final confirmation before it writes live data into the spreadsheet.

After giving this handoff, stop. Ask the user to return to this same Setup conversation after **Financial Warehouse Sync** reports that it has finished. Do not poll, create a recurring task, or begin the document-gathering conversation before the user returns.

### 9. Confirm the completed sync when the user returns

When the user returns and says the web sync is finished, first confirm that it completed. Inspect the selected `Financial Data Warehouse` for its recent sync status when the current surface can do so; otherwise ask the user for the web skill's completion summary. Continue when the sync completed successfully, including a completed run that reports coverage gaps or unsupported accounts. If it failed, is still running, or cannot be confirmed, explain that the financial record is not ready for the next step and direct the user back to the web sync.

Do not treat an unavailable or unsupported connection as a zero balance, a closed account, or evidence that an asset does not exist. Do not describe the household as fully set up until the web skill confirms a successful sync. Do not expose unnecessary folder IDs, spreadsheet IDs, account numbers, audit hashes, raw provider IDs, or internal tab names.

### 10. Guide the supporting-document handoff

Once the completed sync is confirmed, explain that connected account data covers only what Finances could retrieve. The household should now gather copies of the documents and valuations that fill the gaps. Present this concise, clearly labeled handoff, using the existing folders rather than creating or renaming anything:

- **Transactional Data** — recent statements or exports for bank, credit-card, loan, investment, retirement, or other accounts that could not be connected through Finances. Include the account name and statement date; do not ask for logins or passwords.
- **Cash & Manual Spending** — optional receipts or other supporting documents that help explain cash withdrawals. A checking-account withdrawal funds cash; it is not, by itself, evidence of a spending category. Ask the household to explain ordinary cash use in the conversation when useful; the relevant Personal CFO workflow records a confirmed reusable treatment. Do not ask the household to create a cash log, spreadsheet, or other manual ledger. If this folder is absent because the household record predates it, ask for permission before creating it.
- **Benefits & Insurance** — employer benefits guides, health-plan details, HSA/FSA information, and life, disability, home, auto, and umbrella insurance policies or declarations.
- **Debt & Credit** — mortgage, loan, line-of-credit, and credit-card statements; payoff or amortization information; and refinancing records.
- **Estate & Legal** — wills, trusts, healthcare directives or proxies, powers of attorney, and other household legal records the user wants stored.
- **Investments & Retirement** — IRA, 401(k), pension, brokerage, stock-plan, and other retirement or investment statements, including plan or cost-basis records when available.
- **Property & Vehicles** — property deeds and mortgage-related records. Ask whether the user wants to document a current home value and let them choose the source: an online estimate such as Zillow or another real-estate service, a broker estimate, tax assessment, or appraisal are all reasonable options. Save the source and date with the record. Add vehicle titles or registration, insurance records, and a current dated valuation source if the user wants one.

Tell the user that they can upload only the records they are comfortable keeping in Drive, now or later; these documents are optional evidence for their private record and future Personal CFO work. Conversation with the agent is the standard way to provide context or answer questions; the agent writes any confirmed structured context under the hood. Do not ask the user to maintain a spreadsheet, ledger, or other structured file. Do not request credentials, passwords, or documents the user does not want stored.

Ask which category they want to start with. Work through one category at a time: name the destination folder, repeat the relevant examples above, ask the user to upload or note any unavailable records, and then offer the next category. Preserve all existing files and keep the user in control of what is uploaded.

## Ongoing use

Explain the system in one short paragraph: the private record lives in the user's Drive; connected Finances data is synced into it from ChatGPT on the web; and the other Personal CFO tools automatically look for `Personal CFO Home` when a new chat does not already identify the folder. Recommend an initial Lifestyle Review before ongoing maintenance, because it establishes the household context used to interpret later data.

After that review, offer an optional recurring data refresh—not a recurring review. Ask whether the user wants an automatic refresh and, only if they do, ask them to choose weekly, monthly, quarterly, yearly, or a custom cadence. Direct them to create a separate task in [ChatGPT Scheduled](https://chatgpt.com/scheduled) on the web using Financial Warehouse Sync. The saved task must authorize only a non-destructive sync into the existing warehouse resolved by `Personal CFO Home`; it must report connection or location problems instead of writing. It refreshes connected transaction data only. It does not update Household Context, classify transactions, gather documents, or perform a financial-plan review. Do not create a schedule from this desktop setup conversation without explicit user approval.

## Safety boundaries

Do not make investment trades, provide individualized investment instructions, calculate a final tax liability, certify a deduction, give legal advice, or claim professional suitability. Label conclusions as observations, calculations, user-provided facts, assumptions, or unavailable information. Treat connector failures as data gaps, not evidence that an account or value disappeared.
