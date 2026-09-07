# Personal CFO

Personal CFO helps you organize your household finances in one private place, then gives you a simple check-in: **what changed, what needs attention, and what you may want to do next.**

> **Important:** Personal CFO is a tool for organizing and exploring your own financial information. Its creator is not a financial professional, and nothing it produces is financial, investment, tax, legal, insurance, accounting, or other professional advice.
>
> Use it to centralize information, see it more clearly, and work with it more productively. It does not recommend or execute trades, move money, file taxes, or make decisions for you. Always verify important information and seek advice from a qualified professional before acting on a financial, tax, legal, insurance, or accounting matter.

## Privacy and your ChatGPT plan

Personal CFO works with sensitive household information. On a personal ChatGPT workspace (Free, Plus, or Pro), OpenAI says data sharing for model training is enabled by default, but you can opt out: go to **Settings → Data Controls → Improve the model for everyone** and turn it off. The setting applies to new conversations, so do this before using Personal CFO. Follow OpenAI’s step-by-step instructions: [How to stop chats from training ChatGPT](https://help.openai.com/en/articles/7730893-data-control).

If you want a workspace where OpenAI does not use your inputs and outputs to train its models by default, consider **ChatGPT Business**. It includes additional workspace controls and is designed for teams of 2–200. At publication, a Business Standard seat is listed at $20 per person per month when billed annually or $25 when billed monthly; check OpenAI’s [Business pricing page](https://openai.com/business/pricing/) for current pricing, availability, and terms.

## Start here — no technical experience needed

You should not need to use a terminal, GitHub, or code to use Personal CFO.

### What you need

1. A **ChatGPT Plus or Pro subscription** with access to **Plugins**, **Google Drive**, and **Finances**. Finances is currently available to eligible U.S. Plus and Pro users on the web.
2. The ChatGPT desktop app. You will use it to add Personal CFO and install the setup plugin.
3. A Google account with Google Drive.
4. A computer with a web browser. The first live financial-data sync happens in ChatGPT on the web.

Plugin availability depends on your plan, workspace settings, and which features are available to your account. If you do not see **Plugins**, **Google Drive**, or **Finances** in ChatGPT, stop there—this setup will not work on that account yet.

### First, connect your apps

1. In the **ChatGPT desktop app**, open the main **Plugins** tab and add **Google Drive**. Follow the normal Google sign-in steps to connect it.
2. On **ChatGPT on the web**, open **Plugins** and make sure **Google Drive** is enabled and connected there too. The Financial Warehouse Sync skill needs both the web version of Google Drive and Finances; a desktop-only Google Drive connection is not enough.
3. You will connect **Finances** later in ChatGPT on the web, immediately before the first live sync. Never enter a bank password into a ChatGPT conversation.

### Add the Personal CFO marketplace

1. In the **ChatGPT desktop app**, open **Settings** and then **Plugins**.
2. Click **Add** in the top-right corner, then click **Add a marketplace**.
3. Paste this marketplace address:

   ```text
   https://github.com/mcaspers/personal-cfo
   ```

4. In the **Git ref** field, enter:

   ```text
   main
   ```

5. Add the marketplace. A new **Personal CFO** marketplace will appear in your Plugins list.
6. Return to the main **Plugins** tab. Open the Personal CFO marketplace and click the **+** button beside each **Personal CFO** plugin you want to use. You must do this one plugin at a time. For a complete first test, add all of them:

   - Personal CFO Setup
   - Personal CFO Data Layer
   - Personal CFO Report
   - Personal CFO Review
   - Personal CFO Financial Plan
   - Personal CFO Portfolio Review
   - Personal CFO Investment Options
   - Personal CFO Tax Review
   - Personal CFO Lifestyle Review

   Adding a marketplace only makes its plugins available. It does **not** automatically add them to ChatGPT.

### Start Personal CFO

1. In the ChatGPT desktop app, start a **new** Personal CFO conversation.
2. Paste this message:

   ```text
   Set up my Personal CFO financial home.
   ```

3. The first question asks whether you are starting a new household record or joining one that your spouse, partner, or another household member already set up.

   - **Starting a new record:** continue to the next step.
   - **Joining an existing record:** ask the person who manages the household's budget and financial information to share that Google Drive folder with your Google account. Then paste its Google Drive link or folder ID when Personal CFO asks. That is all this setup path needs: it uses the established record rather than connecting your accounts or creating a duplicate.
4. For a new household record, Setup connects Google Drive and asks where to store the record:

   - **Create a Personal CFO Data folder for me**, or
   - **Use an existing Google Drive folder**.
5. Setup reuses an existing `Personal CFO Data` folder if it finds one, so it does not create a second household record. It creates simple document folders and a small Google Drive document called `Personal CFO Home` in the one active top-level folder. The folders are for transactional data, benefits and insurance, debt and credit, estate and legal records, investments and retirement, and property and vehicles. `Financial Data Warehouse` lives inside `Transactional Data`. Do **not** delete `Personal CFO Home`: it is the grounding document every Personal CFO plugin uses to find this household's shared financial home. Upload copies of any documents you want available there now or later; they are not required for the first live-data sync.
6. Before syncing, open **Plugins** in ChatGPT on the web and confirm that **Google Drive** says it is connected. This is separate from the desktop connection and is required for the web skill to find and update your spreadsheet.
7. To import your live data, open [ChatGPT Finances on the web](https://chatgpt.com/finances), click **Connect Accounts**, and complete the secure connection screens for the accounts you want to include. Wait until Finances shows that account data has synced.
8. In ChatGPT on the web, open **Skills** → **Create** → **Upload from your computer**. Download and upload [Financial Warehouse Sync](web-skills/financial-warehouse-sync.zip).
9. Start a new web chat, run **Financial Warehouse Sync**, and say: `Sync my connected financial data into the Financial Data Warehouse in my Personal CFO folder.` Provide the folder or spreadsheet link if asked. The web skill first checks whether Finances is ready, then asks for your final confirmation before it writes anything.
10. The web skill's completion summary tells you what data it found and whether the shared Personal CFO location is ready for the other plugins.

That is it. Your private financial record is stored in your Google Drive, and you can return later for a fuller review, report, plan, portfolio review, or tax-preparation worksheet.

### Optional: understand the patterns behind your spending

After a successful sync, install **Personal CFO Lifestyle Review** from the Personal CFO marketplace in the desktop app. Start a new task and say: `Review the lifestyle patterns in my Personal CFO transactions.` The skill reads the transaction history, highlights a few supported patterns, and asks about them one at a time. Your explanations stay in the chat unless you explicitly ask to save them.

### Optional: refresh your data every month

After the first sync succeeds, you can have ChatGPT refresh the existing warehouse automatically each month.

1. In ChatGPT on the web, open [Scheduled](https://chatgpt.com/scheduled) and create a new task. Choose a time that works for you, such as the first day of each month at 9:00 AM.
2. Confirm that **Google Drive** and **Finances** are still connected in ChatGPT on the web. A scheduled task cannot sync if either connection needs attention.
3. Give the task a non-sensitive name such as `Monthly Personal CFO refresh`, then paste these instructions:

   ```text
   Every month, run Financial Warehouse Sync using my connected Finances and Google Drive. Resolve my active household location through Personal CFO Home. Synchronize only into the existing Financial Data Warehouse inside that location's Transactional Data folder.

   I authorize this scheduled task to write my financial data only to that existing spreadsheet. Use the normal non-destructive delta sync: preserve manual records and stale last-known data, never treat a connector problem as zero, and never clear history or create a replacement folder or workbook. If Finances or Google Drive is unavailable, the destination is ambiguous, or the workbook is not in Transactional Data, do not write. Tell me what needs attention instead.

   Report whether the sync succeeded, what data was updated, any connector warnings, and whether another full sync is recommended.
   ```

4. Review the task's instructions and schedule, then save it. Check its first result before relying on it.

Do not put spreadsheet IDs, folder IDs, balances, account numbers, or other sensitive details in a scheduled task's name or instructions. `Personal CFO Home` lets the task find the right household location without them. You can review, pause, edit, or delete the task from [Scheduled](https://chatgpt.com/scheduled). See OpenAI's [Scheduled tasks guide](https://help.openai.com/en/articles/10291617) for current availability, limits, and notification settings.

## If you cannot find “Add a marketplace”

Your ChatGPT account or workspace may not support personal marketplaces, or your administrator may have turned them off. Ask the person who sent you this guide for help. Do not try to download a ZIP and upload it to Google Drive instead—uploading a ZIP only stores a file; it does not install Personal CFO.

## What Personal CFO does with your information

- Finances supplies read-only connected-account information.
- Google Drive stores the financial record, history, and supporting documents you choose to use.
- Personal CFO labels stale, incomplete, and unavailable data instead of treating it as zero.
- You confirm the selected Drive folder before Personal CFO uses account-specific details.

Always review anything important before acting on it. Financial data can be incomplete or incorrectly categorized.

## For the publisher or technical tester only

Before sharing the marketplace address, commit and push this repository to its default GitHub branch. The address in the user instructions reads the files from GitHub, not from your computer.

This repository is a Codex marketplace. To test it from a local checkout:

```bash
git clone https://github.com/mcaspers/personal-cfo.git
cd personal-cfo
codex plugin marketplace add "$(pwd)"
codex plugin add personal-cfo-setup@personal-cfo
```

Start a new Codex task after installation, then ask: `Set up my Personal CFO financial home.`

The marketplace catalog is [`.agents/plugins/marketplace.json`](.agents/plugins/marketplace.json). The `plugins/` directory contains Personal CFO Setup plus the optional advanced workflows.

## Advanced options

After setup, Personal CFO can also create a household report, period-over-period review, financial plan, portfolio review, investment-options memo, or tax-review worksheet. These are optional; start with Personal CFO Setup.
