# Autoresponder (Auto-Reply)

{% hint style="info" %}
Heads Up! This is a PRO feature. You must have an active membership to use this feature.
{% endhint %}

Autoresponder is available for all Pro users. Contact support with the following details.&#x20;

1. From Name (Company Name)
2. Autoresponder Subject
3. Autoresponder Intro Text (eg: Thanks for submitting the form..)
4. Show copy of their submission in the email - Yes/No
5. Full `https://` path of your Logo Image (PNG preferred)\
   eg: `https://yoursite.com/img/logo.png`

Also, to make the autoresponder work, you must make sure an **email field** with name attribute `email` or `Email` is included in the form. The autoresponder will send emails to that particular email once user filled the form.&#x20;

```html
// example code     ⌄⌄⌄⌄⌄⌄⌄⌄⌄⌄⌄
<input type="email" name="email" placeholder="you@company.com" />
```
