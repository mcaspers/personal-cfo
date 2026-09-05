# Personal CFO

Personal CFO helps you organize your household finances in one private place, then gives you a simple check-in: **what changed, what needs attention, and what you may want to do next.**

It does not move money, make trades, file taxes, or replace a financial, tax, legal, insurance, or accounting professional.

## Start here — no technical experience needed

You should not need to use a terminal, GitHub, or code to use Personal CFO.

### What you need

1. A **ChatGPT subscription or workspace plan** that gives your account access to **ChatGPT Work**, **Plugins**, and **Finances**.
2. The ChatGPT desktop app. You will use it to add Personal CFO and install the setup plugin.
3. A Google account with Google Drive.
4. A computer with a web browser. You will use ChatGPT Work on the web to connect financial accounts; Finances is not available in the desktop app.

Plugin availability depends on your plan, workspace settings, and which features are available to your account. If you do not see **Work**, **Plugins**, or **Finances** in ChatGPT, stop there—this setup will not work on that account yet. See [OpenAI’s plugin availability guidance](https://learn.chatgpt.com/docs/use-chatgpt?translationFallback=fr-FR) and [Finances setup guidance](https://learn.chatgpt.com/fr-FR/use-cases/track-bills-subscriptions-and-spending).

### Install Personal CFO

1. Open the **ChatGPT desktop app** and sign in.
2. Open **Plugins** in Settings.
3. Click **Add** in the top-right corner, then click **Add a marketplace**.
4. Paste this marketplace address:

   ```text
   https://github.com/mcaspers/personal-cfo
   ```

5. Add the marketplace. A new **Personal CFO** marketplace will appear in your Plugins list.
6. Find **Personal CFO Setup** and click **Install** or turn it on.

### Connect your accounts and start setup

1. Open [ChatGPT Work on the web](https://chatgpt.com) and connect **Finances** from the sidebar. Connect your accounts only through the normal Finances connection screens—never paste a bank password into a chat.
2. In the ChatGPT desktop app, start a **new** Personal CFO conversation.
3. When asked, connect **Google Drive**. This is where your private financial record will live.
4. Paste this message:

   ```text
   Set up my Personal CFO and create my first financial check-in.
   ```

5. Answer the questions one at a time. When asked where to store your financial record, choose either:

   - **Create a Personal CFO Data folder for me**, or
   - **Use an existing Google Drive folder**.
6. Review the summary. It will tell you what accounts and history it found, what needs reconnecting, and what it could not find.

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
