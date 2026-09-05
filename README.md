# Personal CFO

Personal CFO helps you organize your household finances in one private place, then gives you a simple check-in: **what changed, what needs attention, and what you may want to do next.**

It does not move money, make trades, file taxes, or replace a financial, tax, legal, insurance, or accounting professional.

## Start here — no technical experience needed

You should not need to use a terminal, GitHub, or code to use Personal CFO.

### What you need

1. A **ChatGPT subscription or workspace plan** that gives your account access to **ChatGPT Work**, **Plugins**, and **Finances**.
2. The ChatGPT desktop app. You will use it to add Personal CFO and install the setup plugin.
3. A Google account with Google Drive.
4. A computer with a web browser. You start Finances from the desktop app, but connect financial accounts in ChatGPT Work on the web.

Plugin availability depends on your plan, workspace settings, and which features are available to your account. If you do not see **Work**, **Plugins**, or **Finances** in ChatGPT, stop there—this setup will not work on that account yet. See [OpenAI’s plugin availability guidance](https://learn.chatgpt.com/docs/use-chatgpt?translationFallback=fr-FR) and [Finances setup guidance](https://learn.chatgpt.com/fr-FR/use-cases/track-bills-subscriptions-and-spending).

### First, connect your apps

1. In the **ChatGPT desktop app**, open the main **Plugins** tab and add **Google Drive**. Follow the normal Google sign-in steps to connect it.
2. Add **Finances** from the same main Plugins tab. The desktop app opens **ChatGPT Work on the web** at the Finances page.
3. On the page headed **“Connect your financial accounts,”** click **Connect Accounts**. Follow the secure connection screens for each bank, card, loan, investment, or other account you want to include. Never enter a bank password into a ChatGPT conversation.
4. When the connections are complete, return to the ChatGPT desktop app.
5. Both Google Drive and Finances must be available on your plan before Personal CFO can use them.

### Add the Personal CFO marketplace

1. In the **ChatGPT desktop app**, open **Settings** and then **Plugins**.
2. Click **Add** in the top-right corner, then click **Add a marketplace**.
3. Paste this marketplace address:

   ```text
   https://github.com/mcaspers/personal-cfo
   ```

4. Add the marketplace. A new **Personal CFO** marketplace will appear in your Plugins list.
5. Return to the main **Plugins** tab. Open the Personal CFO marketplace and click the **+** button beside each **Personal CFO** plugin you want to use. You must do this one plugin at a time. For a complete first test, add all of them:

   - Personal CFO Setup
   - Personal CFO Data Layer
   - Personal CFO Report
   - Personal CFO Review
   - Personal CFO Financial Plan
   - Personal CFO Portfolio Review
   - Personal CFO Investment Options
   - Personal CFO Tax Review

   Adding a marketplace only makes its plugins available. It does **not** automatically add them to ChatGPT.

### Start Personal CFO

1. In the ChatGPT desktop app, start a **new** Personal CFO conversation.
2. Paste this message:

   ```text
   Set up my Personal CFO and create my first financial check-in.
   ```

3. The first question asks whether you are starting a new household record or joining one that your spouse, partner, or another household member already set up.

   - **Starting a new record:** continue to the next step.
   - **Joining an existing record:** first, ask the person who set it up to share the `Personal CFO Data` Google Drive folder with your Google account. Then ask them for that folder's Google Drive folder ID and paste it when Personal CFO asks for it. That is all this setup path needs: it uses the established record rather than connecting your accounts or creating a duplicate.
4. For a new household record, when asked where to store it, choose either:

   - **Create a Personal CFO Data folder for me**, or
   - **Use an existing Google Drive folder**.
5. Review the summary. It will tell you what accounts and history it found, what needs reconnecting, and what it could not find.

That is it. Your private financial record is stored in your Google Drive, and you can return later for a fuller review, report, plan, portfolio review, or tax-preparation worksheet.

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

Start a new Codex task after installation, then ask: `Set up my Personal CFO and create my first financial check-in.`

The marketplace catalog is [`.agents/plugins/marketplace.json`](.agents/plugins/marketplace.json). The `plugins/` directory contains Personal CFO Setup plus the optional advanced workflows.

## Advanced options

After setup, Personal CFO can also create a household report, period-over-period review, financial plan, portfolio review, investment-options memo, or tax-review worksheet. These are optional; start with Personal CFO Setup.
