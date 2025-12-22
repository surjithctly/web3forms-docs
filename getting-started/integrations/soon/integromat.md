# Make (Integromat)

Build powerful automation workflows with Web3Forms and Make (formerly Integromat). Create complex, multi-step scenarios that connect your forms with hundreds of apps and services.

{% hint style="info" %}
This integration uses **Webhooks**, which is a PRO feature. You must have an active PRO plan subscription to use Make with Web3Forms.
{% endhint %}

## What is Make?

[Make](https://www.make.com/) (formerly known as Integromat) is an advanced automation platform that allows you to design sophisticated workflows visually. Make is known for:

* **Visual Workflow Builder**: Drag-and-drop interface for creating scenarios
* **Advanced Logic**: Routers, filters, aggregators, and iterators
* **Better Free Tier**: More operations than competitors
* **Detailed Execution History**: See exactly how your data flows
* **Developer-Friendly**: JSON/XML processing, HTTP requests, custom code

## Setup Instructions

### Step 1: Create a Make Account

1. Go to [make.com](https://www.make.com/)
2. Sign up for a free account or log in
3. Free tier includes 1,000 operations per month

### Step 2: Create a New Scenario

1. Click **Create a new scenario** in your Make dashboard
2. Give your scenario a descriptive name (e.g., "Web3Forms to Google Sheets")

**\[SCREENSHOT PLACEHOLDER: Make dashboard with Create Scenario button]**

### Step 3: Add a Webhook Module

1. Click the **+** button to add a new module
2. Search for "Webhooks"
3. Select **Webhooks** from the results
4. Choose **Custom webhook**

**\[SCREENSHOT PLACEHOLDER: Make module selection showing Webhooks]**

### Step 4: Create a Webhook

1. Click **Add** to create a new webhook
2. Give it a name (e.g., "Web3Forms Contact Form")
3. Click **Save**
4. Make will generate a webhook URL
5. Click **Copy address to clipboard**

**\[SCREENSHOT PLACEHOLDER: Make webhook creation dialog]**

### Step 5: Add Webhook to Web3Forms

1. Open a new tab and go to your [Web3Forms Dashboard](https://app.web3forms.com)
2. Select your form
3. Navigate to the **Integrations** tab
4. Find the **Webhook** integration card
5. Toggle it on
6. Paste the Make webhook URL in the **Webhook URL** field
7. Click **Save Settings**

**\[SCREENSHOT PLACEHOLDER: Web3Forms webhook integration settings]**

### Step 6: Determine the Data Structure

1. Go back to Make
2. The webhook module will be waiting for data
3. Submit a test entry through your Web3Forms form
4. Make will capture the data structure automatically
5. Click **OK** once you see the test data

**\[SCREENSHOT PLACEHOLDER: Make showing webhook data structure]**

### Step 7: Add Actions

1. Click the **+** button after the webhook module
2. Choose your desired app (e.g., Google Sheets, Airtable, Slack)
3. Select the action you want to perform
4. Map the webhook data to the action fields
5. Test your scenario
6. Click the toggle to activate your scenario

**\[SCREENSHOT PLACEHOLDER: Make scenario with webhook and action modules]**

## Popular Make Scenarios

### Send to Google Sheets

**Use Case**: Automatically add form submissions to a Google Sheets spreadsheet

**Modules**:

1. Webhooks → Custom webhook
2. Google Sheets → Add a row
3. Map webhook data to spreadsheet columns

### Add to Airtable

**Use Case**: Store submissions in an Airtable base

**Modules**:

1. Webhooks → Custom webhook
2. Airtable → Create a record
3. Map all form fields to Airtable fields

### Multi-Platform Notifications

**Use Case**: Send notifications to multiple platforms

**Modules**:

1. Webhooks → Custom webhook
2. Slack → Create a message
3. Discord → Create a message
4. Email → Send an email

### Conditional Routing

**Use Case**: Route submissions based on content

**Modules**:

1. Webhooks → Custom webhook
2. Router (splits into multiple paths)
3. Path 1 (VIP leads) → Send to Sales CRM
4. Path 2 (Support) → Create ticket in Help Desk
5. Path 3 (General) → Add to Google Sheets

## Advanced Make Features

### Routers

Route data to different paths based on conditions:

```
Webhook → Router
  ├─ Path 1 (if email contains @company.com) → Send to Sales
  ├─ Path 2 (if message contains "urgent") → SMS Alert
  └─ Path 3 (default) → Standard Processing
```

### Filters

Add filters between modules to control data flow:

* **Filter by Field Value**: Only process if email domain is specific
* **Filter by Time**: Only during business hours
* **Filter by Content**: Only if message contains keywords
* **Filter by Length**: Only if message is longer than X characters

### Aggregators

Combine multiple submissions:

* Collect submissions over 1 hour
* Aggregate into single email or report
* Send batch updates instead of individual notifications

### Iterators

Process arrays and multiple items:

* Split multi-value fields
* Process each item individually
* Handle file attachments separately

### Data Transformation

Make offers powerful data tools:

* **Text Parser**: Extract specific information
* **JSON Parser**: Parse complex JSON data
* **Date/Time**: Format dates and times
* **Math**: Calculate values
* **Encryption**: Hash or encrypt sensitive data

## Troubleshooting

### Webhook Not Receiving Data

* Verify the webhook URL is correct in Web3Forms
* Ensure webhook integration is enabled (toggle on)
* Check that your scenario is active (toggle on)
* Submit a test form after setting up the webhook

### Scenario Errors

Common errors and solutions:

**"Invalid data structure"**

* Re-determine the data structure
* Check field mappings
* Ensure data types match

**"Connection failed"**

* Reconnect your app accounts
* Check API credentials
* Verify account permissions

**"Rate limit exceeded"**

* Reduce scenario frequency
* Implement throttling
* Upgrade to higher tier

### Data Mapping Issues

* Use the mapping panel to select correct fields
* Check data preview before mapping
* Test with real data, not empty values

## Best Practices

### Scenario Organization

* Use descriptive names for scenarios
* Add notes to complex modules
* Group related scenarios in folders
* Document your workflow logic

### Error Handling

* Enable error notifications
* Add error handlers to critical scenarios
* Set up fallback actions
* Monitor execution history regularly

### Performance Optimization

* Use filters early to reduce operations
* Combine multiple actions when possible
* Avoid unnecessary loops
* Cache frequently accessed data

### Testing

* Always test with real data
* Test all router paths
* Check edge cases
* Verify error handling

## Templates and Examples

### Basic Form to Sheet

```
[Webhook] → [Google Sheets: Add Row]
```

### Form to CRM with Notification

```
[Webhook] → [HubSpot: Create Contact] → [Slack: Send Message]
```

### Conditional Lead Routing

```
[Webhook] → [Router]
  ├─ [Filter: VIP] → [Salesforce: Create Lead] → [SMS Alert]
  ├─ [Filter: Regular] → [HubSpot: Create Contact] → [Email]
  └─ [Filter: Default] → [Google Sheets: Add Row]
```

### Daily Digest

```
[Webhook] → [Data Store: Add] → [Scheduler: Daily 9AM]
  → [Data Store: Search] → [Aggregator] → [Email: Send Digest]
```
