---
description: Web3Forms supports cloudflare turnstile captcha in our forms.
---

# Cloudflare Turnstile Captcha

**Codepen Demo**: [https://codepen.io/surjithctly/pen/ExdGwpE](https://codepen.io/surjithctly/pen/ExdGwpE)

{% hint style="info" %}
Heads Up! This is a PRO feature. \
You must have an active subscription to use this feature.
{% endhint %}

## Steps

### 1. Create Turnstile Captcha Accounut <a href="#add-the-turnstile-widget-to-your-site" id="add-the-turnstile-widget-to-your-site"></a>

1. Log in to the [Cloudflare dashboard](https://dash.cloudflare.com/?to=/:account/turnstile) and select your account.
2. Go to **Turnstile**.
3. In the widget overview, select **Settings**.
4. Copy your **sitekey** and **secret key**.

### 2. Add the Turnstile Script to your website <a href="#add-the-turnstile-widget-to-your-site" id="add-the-turnstile-widget-to-your-site"></a>

To add the Turnstile script:

1. Insert the Turnstile script snippet in your HTML’s `<head>` element:

```
<script src="https://challenges.cloudflare.com/turnstile/v0/api.js" async defer></script>
```

### 3. Render the widget inside your form <a href="#add-the-turnstile-widget-to-your-site" id="add-the-turnstile-widget-to-your-site"></a>

To render the Turnstile widget in your form:

1. Insert the below code inside your `<form>` tag. Make sure to change `YOUR_SITE_KEY_HERE` with the actual site key.

```
<div class="cf-turnstile" data-sitekey="YOUR_SITE_KEY_HERE" data-theme="light"></div>
```

### 4. Add Secret Keys to your Web3Forms Dashboard <a href="#add-the-turnstile-widget-to-your-site" id="add-the-turnstile-widget-to-your-site"></a>

1. Visit the Web3Forms Dashboard and select your form.&#x20;
2. Open Settings and choose `turnstile` as your captcha provider
3. Enter the **Secret Key** in the Textbox below
4. Save Changes

That's it. Your form will automatically be protected with Cloudflare Captcha.&#x20;

\---

To read more detailed guide, visit the official docs here: [https://developers.cloudflare.com/turnstile/get-started/](https://developers.cloudflare.com/turnstile/get-started/)
