---
description: 'NOT RECOMMENDED: Prevent bots and spammers using your forms to send emails.'
---

# Honeypot

{% hint style="danger" %}
**Warning:** This feature is depreciated. Please use any other captcha.&#x20;

_Honeypot seems to be less effective in forms to prevent spam submissions. So, we suggest you add a proper captcha to protect your form._&#x20;
{% endhint %}

Bots and Spam Submissions are prevented using the Honeypot Spam Prevention method. By now, these bots are getting advanced, so we have made sure to add some extra layer of protection for this Honeypot. This will stop most bots from submitting your form.

### `botcheck`

{% hint style="info" %}
Honeypot is optional to include, however we recommend adding this if you are not using the [hCaptcha](hcaptcha.md) or [reCaptcha Integration](../../pro-features/recaptcha-integration.md)
{% endhint %}

See the code below.

```markup
<input type="checkbox" name="botcheck" class="hidden" style="display: none;">
```

{% hint style="info" %}
The Input type should be `checkbox` and the name should be `botcheck`
{% endhint %}

