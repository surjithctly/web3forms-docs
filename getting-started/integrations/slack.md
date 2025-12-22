# Slack

Get instant notifications in your Slack channel for every form submission. Keep your team informed in real-time and collaborate on responses directly within Slack.

{% hint style="info" %}
This is a **PRO feature**. You must have an active PRO plan subscription to use this integration.
{% endhint %}

## Features

* ✅ **Real-time Notifications**: Receive form submissions instantly in Slack
* ✅ **Team Collaboration**: Share submissions with your entire team
* ✅ **Formatted Messages**: Clean, professional message formatting
* ✅ **Channel Flexibility**: Send to any public or private channel
* ✅ **Easy Setup**: Connect with just a webhook URL

## Setup Instructions

### Step 1: Create an Incoming Webhook in Slack

To receive notifications, you need to create an Incoming Webhook in your Slack workspace:

1. Go to your Slack workspace
2. Navigate to **Apps** or visit [https://api.slack.com/apps](https://api.slack.com/apps)
3. Click **Create New App** (or use an existing app)
4. Select **From scratch**
5. Give your app a name (e.g., "Web3Forms Notifications")
6. Choose your workspace
7. Click **Create App**

### Step 2: Enable Incoming Webhooks

1. In your app settings, click **Incoming Webhooks** from the left sidebar
2. Toggle **Activate Incoming Webhooks** to **On**
3. Scroll down and click **Add New Webhook to Workspace**
4. Select the channel where you want to receive notifications
5. Click **Allow**

### Step 3: Copy Your Webhook URL

1. After authorization, you'll see your webhook URL
2. It will look like: `https://hooks.slack.com/services/T00000000/B00000000/XXXXXXXXXXXX`
3. Click **Copy** to copy the webhook URL

### Step 4: Configure Web3Forms Integration

1. Log in to your [Web3Forms Dashboard](https://app.web3forms.com)
2. Select the form you want to connect
3. Navigate to the **Integrations** tab in your form settings
4. Find the **Slack** integration card
5. Toggle the switch to enable the integration
6. Paste your Webhook URL in the **Webhook URL** field
7. Click the **Save Settings** button

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

## How It Works

1. When a user submits your Web3Forms contact form, the data is processed
2. Web3Forms sends a formatted notification to your Slack webhook
3. The message appears instantly in your designated Slack channel
4. Your team can see and respond to the submission

### Notification Format

Each form submission sends a formatted message to Slack with:

* **Header**: "New Form Submission" with a notification icon
* **Form Fields**: All submitted data (name, email, message, etc.)

## Managing Your Integration

### Update Webhook URL

To change the destination channel:

1. Create a new Incoming Webhook for a different channel in Slack
2. Go to your form's Integrations tab in Web3Forms
3. Update the Webhook URL field with the new URL
4. Click **Save Settings**

### Disable Notifications

To stop receiving Slack notifications:

1. Go to your form's Integrations tab
2. Toggle the Slack switch off
3. Your settings will be saved automatically



## Troubleshooting

### Not Receiving Notifications

If you're not receiving Slack notifications:

* **Verify Webhook URL**: Ensure the URL is correct and complete
* **Check Integration Status**: Make sure the toggle is enabled in Web3Forms
* **Test the Webhook**: Use Slack's webhook testing tool to verify it's working
* **Check Channel**: Ensure you're looking at the correct Slack channel
* **App Permissions**: Verify the Slack app hasn't been removed or disabled
* **Test Your Form**: Submit a test entry and wait a few seconds

### Invalid Webhook URL Error

* Make sure you copied the entire webhook URL
* URLs should start with `https://hooks.slack.com/services/`
* Don't include any extra spaces or characters
* Generate a new webhook URL if the old one isn't working

### Messages Not Formatting Correctly

* Web3Forms sends standard Slack message formatting
* Custom field names will appear as-is in messages
* Use descriptive field names for better readability



## Advanced Tips

### Customizing the Slack App

You can customize your Slack app:

1. Go to your app settings at [api.slack.com/apps](https://api.slack.com/apps)
2. Add a custom icon for your notifications
3. Change the app name and description
4. Customize the display name shown in messages

## Related Integrations

* [Telegram Integration](telegram-notifications.md) - Mobile notifications via Telegram
* [Discord Integration](discord.md) - Notifications in Discord
* [Webhook Integration](../pro-features/webhooks.md) - Send to custom endpoints

