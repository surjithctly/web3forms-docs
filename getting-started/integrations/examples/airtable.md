# Airtable

Store your Web3Forms submissions in Airtable, the flexible database that combines the power of a database with the simplicity of a spreadsheet. Perfect for organizing, filtering, and collaborating on form data.

{% hint style="info" %}
This integration uses **Webhooks**, which is a PRO feature. You must have an active PRO plan subscription to use Airtable with Web3Forms.
{% endhint %}

## What is Airtable?

[Airtable](https://airtable.com/) is a cloud-based collaboration platform that combines the features of a database, spreadsheet, and project management tool. It's ideal for storing and organizing form submissions because it offers:

- **Rich Field Types**: Text, numbers, attachments, checkboxes, dates, and more
- **Views**: Grid, calendar, kanban, gallery, and form views
- **Filtering & Sorting**: Powerful data organization tools
- **Collaboration**: Share with team members and set permissions
- **Automations**: Trigger actions based on new submissions
- **Integrations**: Connect with thousands of other apps

## Integration Methods

There are two ways to integrate Web3Forms with Airtable:

### Method 1: Using Zapier or Make (Recommended)

The easiest way to connect Web3Forms to Airtable is through automation platforms:

- **Zapier**: Simple setup with no-code interface
- **Make**: More advanced features and better free tier

### Method 2: Direct Webhook Integration

For developers, you can use Airtable's API with a custom webhook endpoint or services like Pipedream.

## Setup via Zapier

### Step 1: Create Airtable Base

1. Log in to [Airtable](https://airtable.com/)
2. Create a new base or open an existing one
3. Create a table for form submissions (e.g., "Contact Forms")
4. Add fields matching your form data:
   - Name (Single line text)
   - Email (Email)
   - Phone (Phone number)
   - Message (Long text)
   - Submitted At (Date)

**[SCREENSHOT PLACEHOLDER: Airtable base with form submission fields]**

### Step 2: Set Up Zapier Integration

1. Go to [Zapier](https://zapier.com/) and create a new Zap
2. **Trigger**: Choose "Webhooks by Zapier" → "Catch Hook"
3. Copy the webhook URL
4. Add the webhook URL to your Web3Forms integration settings
5. Test by submitting your form

**[SCREENSHOT PLACEHOLDER: Zapier webhook trigger setup]**

### Step 3: Configure Airtable Action

1. **Action**: Search for "Airtable" and select it
2. Choose **Create Record** as the action event
3. Connect your Airtable account
4. Select your base and table
5. Map form fields to Airtable fields:
   - Name → Name field
   - Email → Email field
   - Message → Message field
   - etc.

**[SCREENSHOT PLACEHOLDER: Zapier Airtable action with field mapping]**

### Step 4: Test and Activate

1. Test the Zap to ensure data is being created correctly
2. Check your Airtable base for the test record
3. Turn on your Zap
4. Submit a form to verify end-to-end functionality

## Setup via Make (Integromat)

### Step 1: Create Airtable Base

Follow the same steps as in the Zapier method to create your Airtable base and table.

### Step 2: Set Up Make Scenario

1. Go to [Make](https://www.make.com/) and create a new scenario
2. Add a **Webhooks** module → **Custom webhook**
3. Create a new webhook and copy the URL
4. Add the webhook URL to Web3Forms

**[SCREENSHOT PLACEHOLDER: Make webhook module configuration]**

### Step 3: Add Airtable Module

1. Click **+** after the webhook module
2. Search for "Airtable" and select it
3. Choose **Create a Record** as the action
4. Connect your Airtable account (you'll need an API key)
5. Select your base and table
6. Map the webhook data to Airtable fields

**[SCREENSHOT PLACEHOLDER: Make Airtable module with field mapping]**

### Step 4: Test and Activate

1. Run the scenario once to test
2. Submit a test form
3. Verify the record appears in Airtable
4. Activate your scenario

## Airtable Field Types

When setting up your base, use these field types for optimal results:

| Form Data | Recommended Airtable Field Type |
|-----------|--------------------------------|
| Name | Single line text |
| Email | Email |
| Phone | Phone number |
| Message/Comments | Long text |
| Date/Time | Date or Date and time |
| Checkbox | Checkbox |
| Dropdown selection | Single select |
| Multiple selections | Multiple select |
| File uploads | Attachment |

## Advanced Airtable Features

### Views

Create different views for your submissions:

- **Grid View**: Default spreadsheet-like view
- **Form View**: Create a form to manually add submissions
- **Calendar View**: See submissions by date
- **Kanban View**: Track submissions by status (New, In Progress, Completed)
- **Gallery View**: Visual representation with images

### Filtering & Sorting

Organize your data:
- Filter by date range (e.g., "Last 7 days")
- Sort by priority or status
- Group by category or source
- Hide completed or archived submissions

### Linked Records

Connect to other tables:
- Link submissions to customer records
- Connect to project management tables
- Reference product or service tables

### Automations

Set up Airtable automations to:
- Send email notifications when new records are created
- Assign submissions to team members
- Update status fields automatically
- Create tasks in other tools

## Use Cases

### Lead Management

Create a CRM-like system:
1. Store all leads in one base
2. Add status field (New, Contacted, Qualified, Closed)
3. Use kanban view to move leads through pipeline
4. Set up automations for follow-up reminders

### Customer Support

Track support requests:
1. Capture support tickets from forms
2. Assign priority levels
3. Link to customer database
4. Track resolution status

### Event Registrations

Manage event sign-ups:
1. Store attendee information
2. Use calendar view to see registration dates
3. Track attendance status
4. Export attendee lists for event day

### Content Submissions

Collect user-generated content:
1. Store submissions with file attachments
2. Add review status field
3. Use gallery view for visual content
4. Collaborate on approval process

## Airtable API Key Setup

If using Make or direct API integration, you'll need an Airtable API key:

1. Go to [Airtable Account Settings](https://airtable.com/account)
2. Click **Generate API key** in the API section
3. Copy your API key (keep it secure!)
4. Use this key when connecting to Make or other services

{% hint style="warning" %}
Never share your Airtable API key publicly or commit it to version control.
{% endhint %}

## Getting Your Base ID

To use the Airtable API, you need your Base ID:

1. Go to [Airtable API Documentation](https://airtable.com/api)
2. Select your base from the list
3. The Base ID appears in the introduction section
4. It starts with "app" (e.g., `appXXXXXXXXXXXXXX`)

## Troubleshooting

### Records Not Creating

- **Check Field Names**: Ensure field names in Airtable match your mapping
- **Field Types**: Verify field types are compatible (e.g., email field for email data)
- **API Permissions**: Make sure your API key has write permissions
- **Base Limits**: Check if you've reached Airtable plan limits

### Authentication Errors

- **Regenerate API Key**: Create a new API key in Airtable settings
- **Reconnect Account**: In Zapier/Make, reconnect your Airtable account
- **Check Permissions**: Ensure the API key has access to the specific base

### Missing Data

- **Field Mapping**: Review field mappings in your automation
- **Required Fields**: Ensure all required Airtable fields are mapped
- **Data Format**: Check that data formats match (dates, numbers, etc.)

### Rate Limits

Airtable has API rate limits:
- **Free Plan**: 5 requests per second per base
- **Paid Plans**: Higher limits available
- If you hit limits, consider batching or reducing frequency

## Airtable Pricing

Airtable offers several pricing tiers:

- **Free**: 1,200 records per base, 2GB attachments
- **Plus**: $10/month, 5,000 records per base, 5GB attachments
- **Pro**: $20/month, 50,000 records per base, 20GB attachments
- **Enterprise**: Custom pricing, unlimited records

{% hint style="info" %}
The free tier is sufficient for most small to medium-sized contact forms.
{% endhint %}

## Comparison: Airtable vs Google Sheets

| Feature | Airtable | Google Sheets |
|---------|----------|---------------|
| **Setup** | Requires webhook automation | Direct integration available |
| **Field Types** | Rich (email, phone, select, etc.) | Basic (text, number, date) |
| **Views** | Multiple (grid, calendar, kanban) | Single spreadsheet view |
| **Collaboration** | Advanced permissions | Share with edit/view access |
| **Automations** | Built-in automation builder | Requires Apps Script |
| **Best For** | Complex data management | Simple data storage |

## Tips for Success

### Organize Your Base

- Use descriptive field names
- Add field descriptions for team members
- Create multiple views for different purposes
- Use color coding for status fields

### Maintain Data Quality

- Set required fields in Airtable
- Use field validation where possible
- Regularly review and clean up data
- Archive old submissions

### Leverage Automations

- Set up email notifications for new submissions
- Auto-assign submissions to team members
- Update timestamps automatically
- Sync data to other tools

### Performance Optimization

- Don't create unnecessary fields
- Use linked records instead of duplicating data
- Regular archive old records to stay within limits
- Consider your plan's record limits when scaling

## Related Integrations

- [Google Sheets Integration](google-sheets.md) - Alternative spreadsheet solution
- [Zapier Integration](../zapier.md) - Automation platform guide
- [Make Integration](../integromat.md) - Advanced automation
- [Webhooks Documentation](../../pro-features/webhooks.md) - Direct API integration

## External Resources

- [Airtable Official Website](https://airtable.com/)
- [Airtable API Documentation](https://airtable.com/api)
- [Airtable University](https://support.airtable.com/hc/en-us/categories/360003894253-Airtable-University)
- [Airtable Community](https://community.airtable.com/)
- [Airtable Templates](https://airtable.com/templates)

## Need Help?

If you encounter any issues with the Airtable integration:
- Check [Airtable's support documentation](https://support.airtable.com/)
- Visit the [Airtable Community](https://community.airtable.com/)
- Email [support@web3forms.com](mailto:support@web3forms.com)
- [Contribute to our documentation on Github](https://github.com/surjithctly/web3forms-docs)

