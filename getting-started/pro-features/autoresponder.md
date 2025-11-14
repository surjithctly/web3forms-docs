# Autoresponder (Auto-Reply)

{% hint style="info" %}
Heads Up! This is a PRO feature. You must have an active subscription to use this feature.
{% endhint %}

Autoresponder is available for all Pro/Agency users. Following details can be customised.&#x20;

### Enable Autoreponder

You can enable autoresponder from the Form Settings Page from our dashboard: [https://app.webforms.com](https://app.webforms.com/)

#### Available Options

1. From Name (Company Name)
2. Autoresponder Subject
3. Autoresponder Intro Text (eg: Thanks for submitting the form..)
4. Show copy of their submission in the email - Yes/No
5. Full `https://` path of your Logo Image (PNG preferred)\
   eg: `https://yoursite.com/img/logo.png`

<figure><img src="../../.gitbook/assets/CleanShot 2025-11-03 at 13.25.23@2x.png" alt=""><figcaption></figcaption></figure>

Also, to make the autoresponder work, you must make sure your `<form>` has an **email field** with name attribute `email` or `Email` is included in the form. The autoresponder will send emails to that particular email once user filled the form.&#x20;

```html
// example code     ⌄⌄⌄⌄⌄⌄⌄⌄⌄⌄⌄
<input type="email" name="email" placeholder="you@company.com" />
```
