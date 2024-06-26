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

### Fix Stale Form Data after clicking "Go Back"

You might have noticed, after successful form submission, the user will show success page as shown above. However, once user clicked the "Go Back" button, the contact form fileds will still show the form data. it will not clear. In that case, make sure you add the following code to fix that.&#x20;

```html
<script>
    window.onload = function() {
        // Reset the form fields when the page loads
        document.getElementById("form").reset();
    };
</script>
```

### Redirect to your your own Website / URL

To redirect the success page to your own website or another different URL, please use the custom redirection. See this guide [redirection.md](redirection.md "mention")for more details.&#x20;

### Show Success Message on the Same Page (Do not redirect)

To skip redirection after the contact form submission and instead, if you want to show a success message on the same page, you can use the Javascript Method or similar. See [html-and-javascript.md](../../how-to-guides/html-and-javascript.md "mention")page for sample code.&#x20;
