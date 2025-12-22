# Notion

Store your Web3Forms submissions directly in Notion databases, the all-in-one workspace for notes, tasks, wikis, and databases. Perfect for teams that want to manage form submissions alongside their other work.

{% hint style="info" %}
This integration uses **Webhooks**, which is a PRO feature. You must have an active PRO plan subscription to use Notion with Web3Forms.
{% endhint %}

## What is Notion?

[Notion](https://www.notion.so/) is an all-in-one workspace that combines notes, docs, wikis, and project management. Notion databases are perfect for storing form submissions because they offer:

* **Flexible Databases**: Create custom properties for any type of data
* **Multiple Views**: Table, board, timeline, calendar, gallery, and list views
* **Rich Content**: Add notes, files, and links to each submission
* **Collaboration**: Share with team members and set permissions
* **Templates**: Create templates for processing submissions
* **Powerful Filtering**: Filter and sort by any property

## Integration Methods

There are several ways to integrate Web3Forms with Notion:

### Method 1: Using Zapier (Easiest)

The simplest way to connect Web3Forms to Notion with a user-friendly interface.

### Method 2: Using Make (Most Flexible)

More advanced automation with better free tier and visual workflow builder.

### Method 3: Using Pipedream (For Developers)

Developer-friendly platform with code support and generous free tier.

### Method 4: Direct API Integration

Use Notion's API directly for custom implementations.

## Setup via Zapier

### Step 1: Create Notion Database

1. Open [Notion](https://www.notion.so/)
2. Create a new page or open an existing workspace
3. Add a **Database** (full page or inline)
4. Name it "Form Submissions" or similar
5. Add properties to match your form fields:
   * Name (Title or Text)
   * Email (Email)
   * Phone (Phone)
   * Message (Text)
   * Status (Select or Multi-select)
   * Submitted (Date or Created time)

**\[SCREENSHOT PLACEHOLDER: Notion database with form submission properties]**

### Step 2: Set Up Zapier Integration

1. Go to [Zapier](https://zapier.com/) and create a new Zap
2. **Trigger**: Choose "Webhooks by Zapier" → "Catch Hook"
3. Copy the webhook URL
4. Add the webhook URL to Web3Forms integration settings
5. Submit a test form to send data to Zapier

**\[SCREENSHOT PLACEHOLDER: Zapier webhook setup for Notion]**

### Step 3: Configure Notion Action

1. **Action**: Search for "Notion" and select it
2. Choose **Create Database Item** as the action event
3. Click **Sign in to Notion** and connect your account
4. Grant Zapier access to your workspace
5. Select the database you created
6. Map form fields to Notion properties:
   * Form Name → Name (Title)
   * Form Email → Email
   * Form Message → Message
   * etc.

**\[SCREENSHOT PLACEHOLDER: Zapier Notion action with property mapping]**

### Step 4: Test and Activate

1. Test the Zap to ensure the item is created correctly
2. Check your Notion database for the test entry
3. Turn on your Zap
4. Submit a form to verify everything works

## Setup via Make (Integromat)

### Step 1: Create Notion Database

Follow the same steps as in the Zapier method to create your Notion database.

### Step 2: Get Notion Integration Token

1. Go to [Notion Integrations](https://www.notion.so/my-integrations)
2. Click **New integration**
3. Give it a name (e.g., "Web3Forms")
4. Select your workspace
5. Click **Submit**
6. Copy the **Internal Integration Token** (keep it secure!)

**\[SCREENSHOT PLACEHOLDER: Notion integration token creation]**

### Step 3: Share Database with Integration

1. Open your Notion database
2. Click **Share** in the top right
3. Click **Invite**
4. Select your integration from the list
5. Click **Invite**

**\[SCREENSHOT PLACEHOLDER: Sharing Notion database with integration]**

### Step 4: Set Up Make Scenario

1. Go to [Make](https://www.make.com/) and create a new scenario
2. Add a **Webhooks** module → **Custom webhook**
3. Create webhook and copy the URL
4. Add the URL to Web3Forms

**\[SCREENSHOT PLACEHOLDER: Make webhook configuration]**

### Step 5: Add Notion Module

1. Click **+** after the webhook module
2. Search for "Notion" and select it
3. Choose **Create a Database Item**
4. Create a new connection using your integration token
5. Select your database
6. Map webhook data to Notion properties

**\[SCREENSHOT PLACEHOLDER: Make Notion module with field mapping]**

### Step 6: Test and Activate

1. Run the scenario once
2. Submit a test form
3. Verify the entry appears in Notion
4. Activate your scenario

## Setup via Pipedream

### Step 1: Create Notion Database

Follow the same steps to create your Notion database and integration token.

### Step 2: Create Pipedream Workflow

1. Go to [Pipedream](https://pipedream.com/)
2. Create a new workflow
3. Select **HTTP / Webhook** as the trigger
4. Copy the endpoint URL
5. Add it to Web3Forms webhook settings

**\[SCREENSHOT PLACEHOLDER: Pipedream HTTP trigger]**

### Step 3: Add Notion Step

1. Click **+** to add a new step
2. Search for "Notion" and select **Create Page**
3. Connect your Notion account
4. Select your database
5. Map form data to Notion properties using the data from step 1

**\[SCREENSHOT PLACEHOLDER: Pipedream Notion action]**

### Step 4: Deploy and Test

1. Click **Deploy** to activate your workflow
2. Submit a test form
3. Check Notion for the new entry
4. Review execution logs in Pipedream

## Notion Property Types

When setting up your database, use these property types for optimal results:

| Form Data        | Recommended Notion Property |
| ---------------- | --------------------------- |
| Name             | Title or Text               |
| Email            | Email                       |
| Phone            | Phone number                |
| Message/Comments | Text (long form)            |
| URL/Website      | URL                         |
| Date/Time        | Date or Created time        |
| Status           | Select or Status            |
| Categories       | Multi-select                |
| Priority         | Select                      |
| Checkbox/Boolean | Checkbox                    |
| Files            | Files & media               |

## Getting Your Database ID

To use the Notion API, you need your Database ID:

1. Open your database in Notion
2. Click the **•••** menu → **Copy link**
3. The URL looks like: `https://notion.so/workspace-name/DATABASE_ID?v=...`
4. Extract the 32-character ID (before the `?`)
5. Format: `xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

**Example:**

```
URL: https://notion.so/myworkspace/a1b2c3d4e5f6...?v=...
Database ID: a1b2c3d4e5f6...
```

## Troubleshooting

### Items Not Creating

* **Integration Access**: Ensure database is shared with your integration
* **Property Names**: Check that property names match exactly (case-sensitive)
* **Required Properties**: Title property must be mapped
* **Token Valid**: Verify integration token is correct

### Authentication Errors

* **Regenerate Token**: Create a new integration token in Notion
* **Workspace Access**: Ensure integration has access to workspace
* **Database Permissions**: Re-share database with integration

### Missing Data

* **Property Mapping**: Review all property mappings
* **Property Types**: Ensure data types match (email → email property)
* **Empty Values**: Check if form fields are empty
* **Character Limits**: Notion has limits on text length

### Integration Not Appearing

When sharing database:

* Refresh the integrations list
* Make sure integration is created in the correct workspace
* Check that integration status is "Active"

## Related Integrations

* [Airtable Integration](airtable.md) - Alternative database solution
* [Google Sheets Integration](../google-sheets.md) - Spreadsheet storage
* [Zapier Integration](zapier.md) - Automation platform guide
* [Make Integration](integromat.md) - Advanced automation
* [Webhooks Documentation](../../pro-features/webhooks.md) - Direct API integration

