# Discord

Get instant notifications in your Discord server whenever you receive a new form submission. Perfect for community-driven projects, development teams, and keeping everyone in the loop.

{% hint style="info" %}
This is a **PRO feature**. You must have an active PRO plan subscription to use this integration.
{% endhint %}

## Features

- ✅ **Real-time Notifications**: Receive form submissions instantly in Discord
- ✅ **Server Integration**: Send to any channel in your Discord server
- ✅ **Rich Embeds**: Beautiful, formatted message embeds
- ✅ **Community Engagement**: Keep your community informed
- ✅ **Easy Setup**: Connect with just a webhook URL

## Setup Instructions

### Step 1: Create a Webhook in Discord

To receive notifications, you need to create a webhook in your Discord server:

1. Open Discord and go to your server
2. Right-click on the channel where you want to receive notifications
3. Select **Edit Channel** (or click the ⚙️ gear icon)
4. Navigate to the **Integrations** tab
5. Click **Webhooks** or **Create Webhook**
6. Click **New Webhook** button

**[SCREENSHOT PLACEHOLDER: Discord channel settings showing Integrations tab]**

### Step 2: Configure the Webhook

1. Give your webhook a name (e.g., "Web3Forms Notifications")
2. Optionally, upload a custom avatar for the webhook
3. Select the channel where notifications should be posted
4. Click **Copy Webhook URL**
5. The URL will look like: `https://discord.com/api/webhooks/123456789/XXXXXXXXXXXX`

**[SCREENSHOT PLACEHOLDER: Discord webhook configuration interface]**

### Step 3: Configure Web3Forms Integration

1. Log in to your [Web3Forms Dashboard](https://app.web3forms.com)
2. Select the form you want to connect
3. Navigate to the **Integrations** tab in your form settings
4. Find the **Discord** integration card
5. Toggle the switch to enable the integration
6. Paste your Webhook URL in the **Webhook URL** field
7. Click the **Save Settings** button

**[SCREENSHOT PLACEHOLDER: Discord integration card in Web3Forms dashboard]**

## How It Works

1. When a user submits your Web3Forms contact form, the data is processed
2. Web3Forms sends a formatted notification to your Discord webhook
3. The message appears instantly in your designated Discord channel
4. Your server members can see and respond to the submission

### Notification Format

Each form submission sends a rich embed message to Discord with:

- **Title**: "New Form Submission" with timestamp
- **Fields**: All submitted form data (name, email, message, etc.)
- **Color**: Distinctive color coding for visibility
- **Footer**: Form name and submission time

**[SCREENSHOT PLACEHOLDER: Example Discord embed message showing form submission]**

## Use Cases

### Community Projects
Receive feedback and suggestions from your community members in a dedicated channel.

### Developer Communities
Get bug reports and feature requests directly in your Discord server.

### Gaming Communities
Collect applications, reports, or feedback from your gaming community.

### Support Channels
Route support requests to a dedicated support channel for community helpers.

### Event Registrations
Notify your server when someone registers for community events or tournaments.

## Managing Your Integration

### Update Webhook URL

To change the destination channel:

1. Create a new webhook for a different channel in Discord
2. Go to your form's Integrations tab in Web3Forms
3. Update the Webhook URL field with the new URL
4. Click **Save Settings**

### Disable Notifications

To stop receiving Discord notifications:

1. Go to your form's Integrations tab
2. Toggle the Discord switch off
3. Your settings will be saved automatically

### Delete Webhook

To completely remove the webhook from Discord:

1. Go to your Discord channel settings
2. Navigate to **Integrations** → **Webhooks**
3. Find the webhook and click **Delete Webhook**
4. Remember to disable the integration in Web3Forms as well

## Troubleshooting

### Not Receiving Notifications

If you're not receiving Discord notifications:

- **Verify Webhook URL**: Ensure the URL is correct and complete
- **Check Integration Status**: Make sure the toggle is enabled in Web3Forms
- **Test the Webhook**: Send a test message using Discord's webhook testing
- **Check Channel**: Ensure you're looking at the correct Discord channel
- **Webhook Deleted**: Verify the webhook still exists in Discord settings
- **Test Your Form**: Submit a test entry and wait a few seconds

### Invalid Webhook URL Error

- Make sure you copied the entire webhook URL
- URLs should start with `https://discord.com/api/webhooks/`
- Don't include any extra spaces or characters
- Generate a new webhook URL if the old one isn't working

### Webhook Not Found Error

This means the webhook was deleted from Discord:

1. Create a new webhook in Discord
2. Update the webhook URL in Web3Forms
3. Save your settings

### Messages Not Appearing

- Check Discord channel permissions
- Ensure the webhook has permission to post in the channel
- Verify you haven't muted the channel
- Check if Discord is filtering webhook messages

## Privacy & Security

- Your webhook URL is stored securely and encrypted
- Only form submission data is sent to Discord
- No access keys or sensitive credentials are exposed
- You can delete webhook URLs anytime in Discord settings
- Webhook URLs are specific to your Discord server

## Advanced Tips

### Customizing the Webhook

Customize your Discord webhook:

1. Go to your Discord channel settings
2. Navigate to **Integrations** → **Webhooks**
3. Click on your webhook
4. Change the name and avatar
5. Move it to a different channel if needed

### Channel Organization

Best practices for organizing notifications:

- Create a dedicated `#form-submissions` channel
- Use channel categories to organize different form types
- Set up channel permissions to control who sees submissions
- Use thread creation for discussion on specific submissions

### Multiple Webhooks

To send notifications to multiple channels:

1. Create separate webhooks for each channel
2. Use different forms for different notification channels
3. Or use the [Webhook integration](../pro-features/webhooks.md) for more complex routing

### Webhook Security

Protect your webhook URL:

- Don't share webhook URLs publicly
- Regenerate webhook URLs if compromised
- Use channel permissions to restrict access
- Monitor the webhook activity regularly

### Discord Bots vs Webhooks

Webhooks are simpler than bots:
- **Webhooks**: One-way notifications (no interaction needed)
- **Bots**: Two-way communication (can respond and interact)
- For form notifications, webhooks are perfect and easier to set up

## Related Integrations

- [Slack Integration](slack.md) - Team notifications in Slack
- [Telegram Integration](examples/telegram-notifications.md) - Mobile notifications via Telegram
- [Webhook Integration](../pro-features/webhooks.md) - Send to custom endpoints

## Additional Resources

- [Discord Webhooks Documentation](https://discord.com/developers/docs/resources/webhook)
- [Discord Server Setup Guide](https://support.discord.com/hc/en-us/articles/206346498)

## Need Help?

If you encounter any issues with the Discord integration:
- Check [Discord's webhook documentation](https://discord.com/developers/docs/resources/webhook)
- Email [support@web3forms.com](mailto:support@web3forms.com)
- [Contribute to our documentation on Github](https://github.com/surjithctly/web3forms-docs)
