# n8n

Build powerful, self-hosted automation workflows with Web3Forms and n8n. Create custom integrations, process data with code, and maintain complete control over your automation infrastructure.

{% hint style="info" %}
This integration uses **Webhooks**, which is a PRO feature. You must have an active PRO plan subscription to use n8n with Web3Forms.
{% endhint %}

### What is n8n?

[n8n](https://n8n.io/) is a fair-code licensed workflow automation tool that allows you to connect different apps and services together. Unlike other automation platforms, n8n can be self-hosted, giving you complete control over your data and workflows.

#### Why Choose n8n?

* **Self-Hosted**: Run on your own infrastructure for complete data control
* **Open Source**: Fair-code license with access to source code
* **Cloud Option**: Managed cloud hosting also available
* **No Vendor Lock-in**: Export and migrate your workflows anytime
* **Code Support**: Write custom JavaScript/Python for complex logic
* **Visual Editor**: Intuitive drag-and-drop workflow builder
* **400+ Integrations**: Pre-built nodes for popular services
* **Generous Free Tier**: Self-hosted version is completely free

#### Step 1: Create a New Workflow

1. Access your n8n instance (default: http://localhost:5678)
2. Click **Create new workflow**
3. Give your workflow a descriptive name (e.g., "Web3Forms to Database")

**\[SCREENSHOT PLACEHOLDER: n8n new workflow creation]**

#### Step 2: Add a Webhook Node

1. Click the **+** button to add a new node
2. Search for "Webhook"
3. Select **Webhook** from the list
4. Configure the webhook:
   * **HTTP Method**: POST
   * **Path**: Choose a custom path (e.g., web3forms)
   * **Authentication**: None (or configure if needed)
5. Click **Execute Node** to activate the webhook
6. Copy the **Test URL** or **Production URL**

**\[SCREENSHOT PLACEHOLDER: n8n webhook node configuration]**

#### Step 3: Add Webhook to Web3Forms

1. Log in to your [Web3Forms Dashboard](https://app.web3forms.com/)
2. Select your form
3. Navigate to the **Integrations** tab
4. Find the **Webhook** integration card
5. Toggle it on
6. Paste your n8n webhook URL
7. Click **Save Settings**

**\[SCREENSHOT PLACEHOLDER: Web3Forms webhook settings with n8n URL]**

#### Step 4: Test the Connection

1. Go back to n8n
2. The webhook node should be waiting for data
3. Submit a test entry through your Web3Forms form
4. n8n will capture the data and display it
5. Click **Execute Node** to process the test data

**\[SCREENSHOT PLACEHOLDER: n8n showing captured webhook data]**

#### Step 5: Add Processing Nodes

1. Click **+** after the webhook node
2. Add your desired processing nodes:
   * Database operations (PostgreSQL, MongoDB, MySQL)
   * HTTP requests to APIs
   * Data transformation
   * Conditional logic
   * Error handling
3. Connect nodes together
4. Map data from webhook to each node
5. Test your workflow

**\[SCREENSHOT PLACEHOLDER: n8n workflow with multiple connected nodes]**

#### Step 6: Activate Your Workflow

1. Toggle the **Active** switch in the top right
2. Your workflow is now live and will process all submissions
3. Monitor executions in the **Executions** tab

**\[SCREENSHOT PLACEHOLDER: n8n workflow activation toggle]**

### Integration Examples

#### Web3Forms → Notion Database

1. **Webhook** → Receive form data
2. **Set** → Format data for Notion
3. **Notion** → Create database item
4. **Slack** → Send notification

#### Web3Forms → Custom API

1. **Webhook** → Receive form data
2. **Function** → Validate and transform data
3. **HTTP Request** → POST to your API
4. **IF** → Check response status
5. **Email** → Send success/error notification

#### Web3Forms → CRM + Marketing

1. **Webhook** → Receive lead
2. **Switch** → Route by criteria
   * Hot lead → Salesforce + SMS
   * Warm lead → HubSpot + Email sequence
   * Cold lead → Mailchimp list
3. **Set** → Log outcome
4. **Webhook Response** → Send confirmation

### Troubleshooting

#### Webhook Not Receiving Data

* **Check Activation**: Ensure workflow is active (toggle on)
* **Verify URL**: Confirm webhook URL is correct in Web3Forms
* **Test Mode**: Use test URL first, then switch to production
* **Firewall**: Ensure n8n is accessible from internet
* **Logs**: Check n8n execution logs for errors

#### Workflow Not Executing

* **Check Trigger**: Ensure webhook node is properly configured
* **Execution Mode**: Verify workflow is in production mode
* **Resource Limits**: Check if server has enough memory/CPU
* **Permissions**: Ensure n8n has write permissions for data directory

#### Data Mapping Issues

* **Field Names**: Check exact field names from webhook data
* **Data Types**: Ensure types match (string, number, boolean)
* **Empty Values**: Handle optional fields with default values
* **Nested Data**: Use expressions to access nested properties

#### Performance Issues

* **Optimize Queries**: Use efficient database queries
* **Reduce API Calls**: Batch operations when possible
* **Use Caching**: Cache frequently accessed data
* **Queue Mode**: Enable for high-volume workflows
