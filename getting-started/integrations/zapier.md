# Zapier

Connect Web3Forms with 5,000+ apps using Zapier webhooks. Automate your workflow without writing any code by creating powerful integrations between your forms and your favorite tools.

{% hint style="info" %}
This integration uses **Webhooks**, which is a PRO feature. You must have an active PRO plan subscription to use Zapier with Web3Forms.
{% endhint %}

## What is Zapier?

[Zapier](https://zapier.com/) is a popular automation platform that connects different apps and services together. With Zapier, you can automatically send your Web3Forms submissions to thousands of other apps including:

- **CRM**: Salesforce, HubSpot, Pipedrive, Zoho CRM
- **Email Marketing**: Mailchimp, ConvertKit, ActiveCampaign
- **Spreadsheets**: Google Sheets, Airtable, Excel Online
- **Communication**: Slack, Discord, Microsoft Teams
- **Project Management**: Trello, Asana, ClickUp, Monday.com
- **And 5,000+ more apps**

## Setup Instructions

### Step 1: Create a Zapier Account

1. Go to [zapier.com](https://zapier.com/)
2. Sign up for a free account or log in
3. Free plan includes 100 tasks per month

### Step 2: Create a New Zap

1. Click **Create Zap** in your Zapier dashboard
2. Give your Zap a descriptive name (e.g., "Web3Forms to Google Sheets")

**[SCREENSHOT PLACEHOLDER: Zapier dashboard with Create Zap button]**

### Step 3: Set Up the Trigger

1. In the **Trigger** section, search for "Webhooks by Zapier"
2. Select **Webhooks by Zapier**
3. Choose **Catch Hook** as the trigger event
4. Click **Continue**

**[SCREENSHOT PLACEHOLDER: Zapier webhook trigger selection]**

### Step 4: Copy the Webhook URL

1. Zapier will generate a custom webhook URL
2. It will look like: `https://hooks.zapier.com/hooks/catch/123456/abcdef/`
3. Click **Copy** to copy the webhook URL
4. Keep this tab open, you'll need it in a moment

**[SCREENSHOT PLACEHOLDER: Zapier webhook URL displayed]**

### Step 5: Add Webhook to Web3Forms

1. Open a new tab and go to your [Web3Forms Dashboard](https://app.web3forms.com)
2. Select your form
3. Navigate to the **Integrations** tab
4. Find the **Webhook** integration card
5. Toggle it on
6. Paste the Zapier webhook URL in the **Webhook URL** field
7. Click **Save Settings**

**[SCREENSHOT PLACEHOLDER: Web3Forms webhook integration settings]**

### Step 6: Test the Connection

1. Go back to Zapier
2. Click **Test trigger**
3. Submit a test entry through your Web3Forms form
4. Zapier will catch the webhook and display the test data
5. Click **Continue** once you see the test data

**[SCREENSHOT PLACEHOLDER: Zapier showing caught webhook data]**

### Step 7: Set Up the Action

1. Choose the app you want to send data to (e.g., Google Sheets)
2. Select the action (e.g., "Create Spreadsheet Row")
3. Connect your account for that app
4. Map the form fields to the destination fields
5. Test the action
6. Click **Publish** to activate your Zap

**[SCREENSHOT PLACEHOLDER: Zapier action configuration with field mapping]**

## Popular Zap Templates

### Send to Google Sheets

**Use Case**: Automatically add form submissions to a Google Sheets spreadsheet

**Setup**:
1. Trigger: Webhooks by Zapier → Catch Hook
2. Action: Google Sheets → Create Spreadsheet Row
3. Map fields: Name → Name, Email → Email, Message → Message

### Add to Mailchimp

**Use Case**: Automatically add email subscribers to your Mailchimp audience

**Setup**:
1. Trigger: Webhooks by Zapier → Catch Hook
2. Action: Mailchimp → Add/Update Subscriber
3. Map email field and any custom fields

### Create Trello Card

**Use Case**: Create a Trello card for each form submission

**Setup**:
1. Trigger: Webhooks by Zapier → Catch Hook
2. Action: Trello → Create Card
3. Use form data to populate card title and description

### Send Slack Notification

**Use Case**: Notify your team in Slack about new submissions

**Setup**:
1. Trigger: Webhooks by Zapier → Catch Hook
2. Action: Slack → Send Channel Message
3. Format message with form data

### Add to CRM

**Use Case**: Automatically create leads in your CRM

**Setup**:
1. Trigger: Webhooks by Zapier → Catch Hook
2. Action: Your CRM → Create Lead/Contact
3. Map all relevant form fields

## Multi-Step Zaps

Create complex workflows with multiple actions:

**Example: Lead Routing Workflow**

1. **Trigger**: Catch webhook from Web3Forms
2. **Action 1**: Add lead to Google Sheets
3. **Action 2**: Create contact in CRM
4. **Action 3**: Send notification to Slack
5. **Action 4**: Send thank you email via Gmail

**Example: Conditional Routing**

1. **Trigger**: Catch webhook from Web3Forms
2. **Filter**: Check if message contains "urgent"
3. **Action 1**: If urgent → Send SMS via Twilio
4. **Action 2**: If not urgent → Send to standard support queue

## Tips for Using Zapier

### Field Mapping

When mapping fields:
- Use the exact field names from your form
- Check the data preview to ensure correct mapping
- Test thoroughly before publishing

### Error Handling

Set up error notifications:
- Add your email to Zap error notifications
- Monitor your Zap history regularly
- Fix failing Zaps promptly

### Data Formatting

Format data correctly:
- Use Zapier's Formatter tool for date/time conversions
- Clean up text fields (trim whitespace, change case)
- Split full names into first/last names if needed

### Filters

Use filters to control when Zaps run:
- Only process submissions with specific values
- Skip test submissions
- Route different types of submissions differently

## Pricing

Zapier offers several pricing tiers:

- **Free**: 100 tasks/month, single-step Zaps
- **Starter**: $19.99/month, 750 tasks/month, multi-step Zaps
- **Professional**: $49/month, 2,000 tasks/month, advanced features
- **Team**: $299/month, 50,000 tasks/month, team collaboration

{% hint style="info" %}
Each form submission counts as 1 task in Zapier. Multi-step Zaps count each action as an additional task.
{% endhint %}

## Troubleshooting

### Webhook Not Triggering

- Verify the webhook URL is correct in Web3Forms
- Ensure the webhook integration is enabled (toggle on)
- Check that your Zap is turned on
- Submit a test form to trigger the webhook

### No Data Showing in Zapier

- Make sure you submitted the form after setting up the webhook
- Check that the form includes all expected fields
- Review the webhook payload in Zapier's history

### Zap Errors

Common errors and solutions:

**"Could not find record"**
- Check that the destination record exists
- Verify account connections are active

**"Required field missing"**
- Ensure all required fields are mapped
- Provide default values for optional fields

**"Invalid format"**
- Use Zapier's Formatter to convert data types
- Check date/time formats match expectations

### Rate Limits

If hitting Zapier task limits:
- Upgrade to a higher plan
- Use filters to reduce unnecessary tasks
- Consolidate multiple Zaps

## Alternatives to Zapier

If Zapier doesn't fit your needs, consider:

- **[Make (Integromat)](integromat.md)** - More complex automation, better free tier
- **[Pipedream](https://pipedream.com/)** - Developer-friendly with code support
- **[n8n](https://n8n.io/)** - Open-source, self-hostable
- **Custom Webhooks** - Build your own integration

## Advanced Use Cases

### Lead Scoring

1. Catch webhook
2. Analyze submission data
3. Calculate lead score based on criteria
4. Route high-value leads to sales team
5. Route low-value leads to nurture campaign

### Data Enrichment

1. Catch webhook
2. Look up company data via Clearbit/Hunter
3. Enrich contact information
4. Add to CRM with enriched data

### Multi-Channel Notifications

1. Catch webhook
2. Send to Slack
3. Send to Discord
4. Send to Telegram
5. Create calendar event for follow-up

## Related Resources

- [Webhooks Documentation](../pro-features/webhooks.md) - Complete webhook guide
- [Make (Integromat) Integration](integromat.md) - Alternative automation platform
- [Google Sheets Integration](examples/google-sheets.md) - Direct spreadsheet sync

## External Links

- [Zapier Official Website](https://zapier.com/)
- [Zapier Webhooks Documentation](https://zapier.com/page/webhooks/)
- [Zapier App Directory](https://zapier.com/apps)
- [Zapier University](https://learn.zapier.com/)

## Need Help?

If you encounter any issues with Zapier integration:
- Check [Zapier's support documentation](https://help.zapier.com/)
- Email [support@web3forms.com](mailto:support@web3forms.com)
- [Contribute to our documentation on Github](https://github.com/surjithctly/web3forms-docs)

