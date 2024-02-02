---
description: >-
  You can customize the success / thank you page as you like. See the options
  below.
---

# Success / Thank You Page

{% hint style="info" %}
Tip: To use your own thank you page, visit [redirection.md](redirection.md "mention") page.&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/CleanShot 2024-02-02 at 13.16.55@2x (1).png" alt="" width="375"><figcaption><p>Default Success Page</p></figcaption></figure>

### Customize Title & Description

To customize the title and description of the success page after the form submission, use the `title` and `desc` params to the redirect URL.&#x20;

```html
<input 
type="hidden" 
name="redirect" 
value="https://web3forms.com/success?title=My%20Text&desc=Custom%20Description" />
```

<figure><img src="../../.gitbook/assets/CleanShot 2024-02-02 at 13.24.19@2x.png" alt="" width="375"><figcaption><p>After customization - French Text</p></figcaption></figure>

### Redirect to your your own Website / URL

To redirect the success page to your own website or another different URL, please use the custom redirection. See this guide [redirection.md](redirection.md "mention")for more details.&#x20;

### Show Success Message on the Same Page (Do not redirect)

To skip redirection after the contact form submission and instead, if you want to show a success message on the same page, you can use the Javascript Method or similar. See [html-and-javascript.md](../../how-to-guides/html-and-javascript.md "mention")page for sample code.&#x20;
