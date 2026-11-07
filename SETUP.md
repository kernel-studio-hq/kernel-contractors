# Setting it up yourself

Do this once, on the computer you will work from. Allow about an hour the first time, and more on an older computer. When you are done, your AI assistant can read your records, write to them, and save its work without ever asking you how.

Be honest with yourself before you start. This takes some comfort with typing commands into a terminal window, following steps exactly, and not panicking at a screen full of text. Many owners would rather have someone set it up for them, and that is a perfectly good choice. The [front page](README.md) says how.

**What it costs to run.** This template is free. Running it is not. You need:

- **Your own GitHub account.** A basic account is free. It is where your records are kept and where every save goes.
- **Your own paid Claude plan.** On the free plan, the Claude app can chat but cannot work in a folder on your computer. Check current plans and prices at [claude.com/pricing](https://claude.com/pricing).

**Which assistant this guide covers.** This guide was written for the Claude desktop app, working in its **Code** tab. Other AI assistants that read a file called `AGENTS.md` may also work with these records, but this guide does not cover them and they have not been tried from start to finish.

## Before you start: is this computer ready

Four things, before anything else:

1. **It is yours to control:** not a shared, family or public computer. This setup puts your business records on its hard drive and lets an AI application read and change them.
2. **You know the password that lets you install software on it.** Two steps below will ask for it.
3. **The screen lock is on, and so is disk encryption** (FileVault on a Mac, BitLocker on Windows). If this computer is lost, that is what keeps your records from whoever finds it.
4. **It is a Mac or a Windows computer that still gets updates.** Older computers can do this, and Step 3 says what to expect on one.

## What you are setting up, in plain terms

1. **Your GitHub account.** Where your records are kept safe, and where every save goes.
2. **Your own private copy of this template, on GitHub.** GitHub keeps things in what it calls a *repository* (people say "repo"): a folder that remembers every saved change. Yours will hold customer names, addresses, contracts and prices, so it must be **private**.
3. **A small sign-in tool** (GitHub CLI). It lets your assistant save on your behalf, so it never has to ask you about saving.
4. **Your copy, downloaded to this computer.** On your computer a repository looks and works like an ordinary folder.
5. **The Claude desktop app,** signed in with your paid plan, opened on that folder in its Code tab.

Work through the steps in order. Where a step shows a grey box, copy what is in it, paste it into the window the step names, and press Enter. **Every grey box holds exactly one line. Do them one at a time, and check the result written under each box before you go on to the next.**

Never paste a one-time code, a password or a token into a chat with your assistant, or give one to anyone. Codes go only into GitHub's own pages.

---

## Step 1. Your GitHub account

If you don't have one, make one at [github.com](https://github.com/), in the browser. Use your own named email address, not a shared one such as an info@ address. Turn on two-step sign-in when GitHub offers it.

Write down your GitHub **username** (the short name GitHub shows at the top right when you click your picture). Later steps need it.

## Step 2. Make your own private copy

1. **In the browser,** open this template's page on GitHub: [github.com/kernel-studio-hq/kernel-contractors](https://github.com/kernel-studio-hq/kernel-contractors).
2. **In the browser,** click the green **Use this template** button near the top right, then click **Create a new repository**. Do not click **Fork**: a fork of a public repository cannot be made private.
3. **In the browser,** check that **Owner** shows your own username.
4. **In the browser,** in **Repository name**, type `business-records`. You can choose another name, but then you will need to change it in every grey box below that says `business-records`.
5. **In the browser,** click **Private**. This matters more than anything else on this page.
6. **In the browser,** click **Create repository**.

You should now see your copy, with the word **Private** in a small label next to its name. If it says **Public**, click **Settings**, scroll to the bottom, and use **Change visibility** to make it private before you go any further.

## Step 3. Install the sign-in tool

*Already have it? Skip to Step 4 and check.*

**Mac.** Open **Terminal** (press `Cmd + Space`, type "Terminal", press Enter). Paste:

```bash
brew install gh
```

It should end without an error. If it says `brew: command not found`, Homebrew is not installed. Homebrew is a tool that installs other tools. Install it first from [brew.sh](https://brew.sh/), then run the line above again.

**On an older Mac, expect this to look alarming.** It may print a long warning that your kind of Mac is no longer supported. It may ask `Do you want to proceed with the installation? [y/n]`: type `y`, then press Enter, in the terminal window. It may run for several minutes and print a great deal of text. It may even end with a line in red that begins `Error`. Do not judge it by any of that, and do not try the fixes it prints on the screen. **The only test that counts is Step 4.** If the second check there prints a version number, the install worked. If it does not, stop and get help.

**Windows.** Open **PowerShell** (press the Start key, type "PowerShell", press Enter). Paste:

```powershell
winget install --id GitHub.cli --source winget
```

It should end by saying the install worked. Then **close PowerShell and open it again.** The new tool is not available in the old window.

## Step 4. Check your tools

You need two tools. Git does the downloading and saving. GitHub CLI handles signing in. Most computers already have Git.

First, Git:

```bash
git --version
```

It should print a version number. On a Mac, a window may appear instead, offering to install developer tools: click **Install**, wait for it to finish, then run the line again. If it fails any other way, install Git from [git-scm.com](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

Then GitHub CLI:

```bash
gh --version
```

It should print a version number. If it fails, go back to Step 3.

## Step 5. Sign in

```bash
gh auth login --hostname github.com --git-protocol https
```

This step goes back and forth between the terminal window and your web browser. Each line below says where you are and exactly what to press.

1. **In the terminal**, it asks whether to sign Git in with your GitHub credentials. Type `y`, then press Enter. This is the part that lets your assistant save.
2. **In the terminal**, it shows a short list of ways to sign in. This is not something you click. Use the up and down arrow keys until **Login with a web browser** is the highlighted line (it usually already is), then press Enter.
3. **In the terminal**, it shows a one-time code, eight characters with a dash in the middle. Leave the window where you can see it. This code is typed into GitHub's own page in the next steps and nowhere else.
4. **In the terminal**, press Enter. Your web browser opens on a GitHub page.
5. **In the browser**, sign in to GitHub if it asks you to. Check that the account shown is yours. Then click **Continue**.
6. **In the browser**, type the one-time code into the boxes, then click **Continue**.
7. **In the browser**, click **Authorize github**. If it asks for your GitHub password or a sign-in code from your phone, give it; that is GitHub checking it is really you.
8. **In the browser**, it should now say you are all set. Go back to the terminal window: it should say the login is complete and show your GitHub username. You need both. If the browser says yes and the terminal does not, run the line in the grey box above again.

Then tell Git who is saving, in two separate lines. For each one: paste it, **change the part inside the quotes, and only then press Enter.**

Your name. Replace `Your Name` with your own:

```bash
git config --global user.name "Your Name"
```

It prints nothing. That is correct.

Your email. Replace `you@example.com` with the email on your GitHub account:

```bash
git config --global user.email "you@example.com"
```

It prints nothing. That is correct.

## Step 6. Check that you can reach your copy, and that it is private

Paste this line, **replace `YOUR-USERNAME` with your GitHub username, and only then press Enter:**

```bash
gh api repos/YOUR-USERNAME/business-records --jq '.full_name + " is " + .visibility'
```

It should print your username, then `/business-records is private`. If it says **public**, go back to the end of Step 2 and make it private before you go on. If it says "Not Found," either the username is typed wrong or you signed in to a different account in Step 5.

## Step 7. Download your copy

Put it in your home folder, **not in Desktop or Documents if those sync to iCloud or OneDrive.** A syncing service and your assistant will fight over the same files.

First, move to your home folder. **Mac:**

```bash
cd ~
```

**Windows:**

```powershell
cd $HOME
```

It prints nothing. That is correct.

Then download your copy (the same line on Mac and Windows). **Replace `YOUR-USERNAME` before you press Enter:**

```bash
gh repo clone YOUR-USERNAME/business-records
```

It should end with a line saying it is done, with no error.

You now have a folder called `business-records` in your home folder. That is the last time you need the terminal window.

## Step 8. Install the Claude app and sign in

Download the Claude desktop app from [claude.com/download](https://claude.com/download), open it, and sign in with the account that has your paid Claude plan.

- **You need a paid plan.** On the free plan, the app cannot work in a folder on your computer at all. If you try, it shows an upgrade screen. That screen means your plan, not a mistake on your part.
- **Sign in with your own named email address,** not a shared one. The app signs you in by sending a link or code to that mailbox, so anyone who can read the mailbox can open your account and everything you have said in it.
- **Think about your plan's privacy settings before you hand it customer papers.** Business plans (Team and above) come under Anthropic's business terms. On a one-person plan, open **Settings**, then **Privacy**, read the setting about using your conversations to improve the models, and choose for yourself. On any plan, don't click the thumbs-up or thumbs-down under a reply in a conversation that holds a customer's papers: that sends the conversation as feedback.
- **On a Team plan,** you are the administrator. In the organization's admin settings, consider switching off anything that sends your work somewhere other than this computer and GitHub, such as cloud sessions, shared sessions and chat rating. Leave the setting that allows Claude Code on the desktop switched on: Step 9 depends on it. Setting names change often; look for what they describe.

Having your records on this computer is not permission to send them to any AI service you like. Use the one you have chosen and are paying for.

## Step 9. Open your folder in the Code tab

This is the step that matters most. The app has more than one place to start a conversation, and they look alike. Only the Code tab can save your work to GitHub. What follows describes the app as it looked in late 2026; if a name has moved, look for the thing it describes.

1. **In the Claude app**, look at the top left of the window. There are two small controls side by side: a speech bubble, and one that looks like `</>`. Click **`</>`**. This is the Code tab.
2. **Why this one.** A conversation started from the speech-bubble side runs in a sealed space. It can read your folder, but it cannot bring your folder up to date or save, because your GitHub sign-in is not available inside that space. The Code tab works on your computer as you, so your sign-in from Step 5 is there.
3. **In the Code tab**, under the message box, there is a small control with a folder on it. Click it and choose the **`business-records`** folder in your home folder. If a control beside it offers a choice between **Local** and something else, it should say **Local**.
4. **In the app**, a window may ask whether to trust this folder and show where it is. Check that it ends in `business-records`, then click to trust it. Your computer may also ask whether Claude may reach that folder. Click **Allow** (or **OK**).
5. **In the app**, you may see a note that an automatic mode is on. It means your assistant carries out routine steps without stopping to ask you about each one, and still stops for anything that looks risky. That is what you want.

Then go to **Your first session** at the bottom of this page.

---

## When something goes wrong

- **Never delete your folder to fix a problem.** Your records live there. Deleting and downloading again can lose work that was not saved yet.
- **If it says it cannot find your folder and stops,** it is working correctly and you are in the wrong place: a conversation on the speech-bubble side of the app, or a plan that cannot open folders. Click **`</>`** at the top left and start again from Step 9. Do not upload your folder to it, even if that would seem to get you going.
- **If it says it cannot bring the folder up to date, or mentions a username, credentials or signing in,** first check you are in the Code tab (`</>`). If you are, your GitHub sign-in may have expired. You can test it yourself. Open Terminal (or PowerShell) and paste the one line for your computer.

  **Mac:**

  ```bash
  git -C ~/business-records fetch
  ```

  **Windows:**

  ```powershell
  git -C $HOME\business-records fetch
  ```

  If it prints nothing, or a line or two about new changes, your sign-in is fine and the problem is where the conversation was started. If it asks for a username or says it could not read one, run the sign-in line in Step 5 again, then start a new session.
- **If it says your records on GitHub are public,** it has stopped saving on purpose. Say "help me make my records private," or follow the end of Step 2.
- **If it says saving didn't go through because there is newer work on GitHub,** someone saved to your records after your session started: you on another computer, or someone you gave access to. Usually your assistant brings the newer work in and saves on top by itself, and you never hear about it. It stops only if two people changed the very same thing, and then it changes nothing until a person has looked. Ask someone comfortable with GitHub. Nothing is lost.
- **If saving fails for any other reason,** it will stop and tell you. Treat it like the sign-in problem above.
- **If something it did looks wrong,** say **"Undo that."** Every save is kept.
- **If it seems confused about where things are,** close the conversation and start a new one with the opening lines below.
- **If you are stuck on a step,** your assistant can read this guide and walk you through it, once it is open in the Code tab: say "Help me get started."

## Your phone, and anywhere that is not your computer

The Claude app on your phone may be able to open your records too. Use it to ask and look things up: what the estimate on a job was, what was decided, what is still owed.

It cannot save the way your computer does. A change made from a phone is kept to one side on GitHub and does not reach your records on its own. So the rule is short: **read from your phone, change from your computer.**

Your assistant knows this. If something looks out of date while you are on your phone, it will say so and leave the fix for your next session at your computer. If a change is ever made from your phone anyway, your assistant looks for it at the start of your next session on your computer and brings it in if it can.

## Bringing someone in to help

1. **They make their own GitHub account.** Never share a login, yours included. Yours can change and delete everything.
2. **You invite that account to your records repository only.** They accept from the email GitHub sends them. Say "Help me give someone access" and your assistant walks you through it.
3. **You choose what they can do.** GitHub calls the two choices **Read** and **Write**. If you are not sure, start with Read. You can change it later.
4. **They need their own paid AI assistant plan.** Yours cannot be shared.
5. **They follow this guide,** skipping Step 2 (they use your copy, not a new one). In Step 6 and Step 7, they use **your** username in place of `YOUR-USERNAME`.

**If you gave them Write,** they work exactly as you do, with the same opening lines. Their saves go into your records under their name.

**If you gave them Read,** they and their assistant can see everything, including the papers saved there, and can save nothing. Their assistant must never write inside your records folder. So in Step 7 they set up differently: one folder that holds a download of your records and a `workspace` folder beside it. Three lines, one at a time, each run in the terminal window. In the third, **replace `OWNER-USERNAME` with your GitHub username before pressing Enter.**

Make the folders (Mac):

```bash
mkdir -p ~/records-help/workspace
```

On Windows:

```powershell
mkdir $HOME\records-help\workspace
```

It prints nothing on a Mac, and a line or two about the new folder on Windows. Both are correct.

Move into it (Mac):

```bash
cd ~/records-help
```

On Windows:

```powershell
cd $HOME\records-help
```

It prints nothing. That is correct.

Download your records:

```bash
gh repo clone OWNER-USERNAME/business-records
```

It should end with a line saying it is done, with no error.

In Step 9 they choose the **`records-help`** folder, and at the start of every session they paste these lines instead of yours:

```text
We're starting a working session in my records-help folder. I can read the business-records folder and I cannot save to it, so treat it as read-only: never create, change, or delete anything inside it. Everything you produce for me goes in the workspace folder beside it. Before anything else, read the instruction file at the top of the business-records folder and follow it, including bringing that folder up to date. If you can't read the folder or can't bring it up to date, say so plainly in one sentence and stop. Don't carry on with what you have, and don't offer to work from a copy I upload. If you find anything unsaved inside the business-records folder, tell me what it is in one sentence and wait for me: it should not be there. When you're ready, tell me in one line.
```

What they produce stays in `workspace` until they send it to you. It becomes part of your records when you hand it to your own assistant.

**When they stop helping,** take their access away the same day: say "Take someone's access away." They keep whatever copy is already on their computer, saved papers included. Give access only to people you would trust with those records.

## Papers you never hand your assistant

When your assistant reads a page, that page is sent to the AI service, whether or not anything is saved afterwards. So never give it:

- tax forms (a W-9 or 1099, for example)
- anything showing a Social Security number, a tax ID or your license number
- bank, card or payment account details
- copies of anyone's ID
- passwords, keys or sign-in codes
- insurance or bonding papers that show policy or bond numbers
- employee pay records

Tell it the fact instead: "We're insured through the end of next year, and the certificate is in the office." Everything else, like estimates, contracts, plans, permits, inspection reports, supplier quotes and photos, it can read.

## What you do not need to learn

You now know the one word that matters here, repository, because it is the word GitHub uses. The rest you can leave: branches, pull requests, commits, merges. Keeping your records safe is your assistant's job. If a task ever seems to need one of those words, say what you want in plain words and let your assistant handle it.

---

## Your first session

Every time you sit down to work: open the Claude app, click **`</>`** at the top left, start a new conversation, and check the folder under the message box says `business-records`. Then paste these lines as they are, and press Enter:

```text
We're starting a working session in my business-records folder. Before anything else, read the instruction file at the top of this folder and follow it, including bringing the folder up to date. If you can't read the folder or can't bring it up to date, say so plainly in one sentence and stop. Don't carry on with what you have, and don't offer to work from a copy I upload. If you find unsaved work already sitting there, tell me what it is in one sentence and wait for me. As we work, save each time something I've confirmed is written down, and tell me "Saved." When you're ready, tell me in one line.
```

You should get back one of three things:

- **One line saying it's up to date and ready.** Carry on.
- **A line saying there is unfinished work from last time,** asking whether to save it as it is or pick up where you left off. Nothing is wrong. Choose one.
- **A line saying it can't find your folder, can't bring it up to date, or that your records are public.** It has done the right thing by stopping. See "When something goes wrong" above.

You will see "Saved." often. That is it working. When you stop for the day, look at the last reply. If it doesn't end with "Saved.", say "Save that." before you close the app.

The first time, once it says it's ready, say:

> Help me get started.

Then open the [start page](START-HERE.md) to see what else you can say.
