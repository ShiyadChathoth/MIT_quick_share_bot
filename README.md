# MIT_quick_share_bot
Secure Sender for Telegram
A simple, self-hosted web page to quickly send text snippets or notes to a specific Telegram group. This tool uses a secure webhook to bypass browser CORS (Cross-Origin Resource Sharing) limitations, ensuring reliable delivery from any device with a web browser.

It's perfect for quickly sharing links, thoughts, or copied text from your desktop or mobile to a personal or team Telegram chat without needing to open the Telegram app itself.

How It Works
Directly calling the Telegram API from a browser-based JavaScript application is blocked by modern web security policies (CORS). This project solves that problem by using a simple, serverless "middleman" architecture:

Your Browser (index.html) → Make.com Webhook → Telegram Bot API → Your Telegram Group

The index.html file sends the text to a unique, secure webhook URL. An automation scenario on Make.com (or a similar service) listens at this URL, receives the text, and then uses the official Telegram Bot API to post the message into your designated group. This is a robust and secure method that requires no backend server or complex setup.

Features
Direct Sending: Paste text and send it directly to any Telegram group with a single click.

CORS-Safe: Uses a webhook to reliably send messages without running into browser security errors.

Private & Secure: Your credentials (bot token, chat ID) are not stored in the web page. The frontend only needs the public webhook URL.

Zero Backend: The entire application is a single index.html file.

Easy Hosting: Can be hosted for free on services like GitHub Pages.

Responsive Design: Clean and simple interface that works well on both desktop and mobile devices.

Setup Instructions
You only need to do this one-time setup. It takes about 5-10 minutes.

Prerequisites
A Telegram account.

A free Make.com account.

Step 1: Create Your Telegram Bot
Open Telegram and start a chat with the official bot manager, @BotFather.

Send the /newbot command.

Follow the prompts to give your bot a name and a username.

@BotFather will send you a message containing your Bot Token. Copy this token and save it somewhere safe.

Step 2: Get Your Group's Chat ID
Create a new Telegram group (or use an existing one).

Add your new bot to the group as a member.

Add the @userinfobot to your group. It will immediately post a message that includes the group's Chat ID. It will be a number starting with a hyphen (e.g., -100123456789).

Copy this Chat ID and save it. You can now remove @userinfobot from the group.

Step 3: Create the Make.com Webhook
Log in to your Make.com account and create a new scenario.

Click the + button and add a Webhook module. Select the Custom webhook trigger.

Click "Add" to create a new webhook. Give it a name (e.g., "Telegram Sender") and click Save.

Your unique webhook URL will be displayed. Copy this URL.

Add another module to your scenario by clicking the + on the right side of the webhook module.

Search for and select the Telegram Bot module. Choose the action Send a Text Message or a Reply.

Connect your bot: Click "Add" next to the Connection field and paste your Bot Token from Step 1.

Configure the fields:

Chat ID: Paste your group's Chat ID from Step 2.

Text: Click in the field and select the text variable that appears from the Webhook module.

Click OK to save the Telegram module.

At the bottom-left of the scenario editor, turn the scheduling switch ON.

Step 4: Configure the Web App
Open the index.html file.

Click the gear icon (⚙️) in the top-right corner.

Paste your Make.com Webhook URL from Step 3 into the input field.

Click Save. The URL will be saved in your browser's local storage for future use.

Usage
Open the index.html file in your browser (or navigate to its hosted URL).

Type or paste the text you want to send into the text area.

Click the "Send to Telegram" button.

The message will instantly appear in your configured Telegram group.

Hosting
You can easily host this single file for free on GitHub Pages.

Create a new public GitHub repository named your-username.github.io.

Upload the index.html file to this repository.

Your website will be live at https://your-username.github.io.

Technology Stack
Frontend: HTML5, Tailwind CSS, Vanilla JavaScript

Automation/Backend: Make.com (Webhook)

Target API: Telegram Bot API
