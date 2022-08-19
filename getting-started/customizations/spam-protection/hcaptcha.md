---
description: >-
  hCaptcha is the privacy friendly alternative to Google reCaptcha. Used by
  Cloudflare, Shopify & more..
---

# hCaptcha

![](<../../../.gitbook/assets/CleanShot 2022-08-19 at 18.47.23.png>)

Web3Forms provides zero-config integration with hCaptcha. You don't need to setup your own keys or register with them. Just use the following code and add a script. You're done.&#x20;

{% hint style="info" %}
We recommend adding **hCaptcha** if you don't mind showing the above captcha box to the users. If not, you may use the hidden [honeypot](spam-protection.md) or [reCaptcha](../../pro-features/recaptcha-integration.md) method.&#x20;
{% endhint %}

**Step 1: Add a \<div> inside your form**

```html
<form>
  ...
   <! -- Step 1: Add this line -->
   <div class="h-captcha" data-captcha="true"></div>
  ...
</form>
```

**Step 2: Add the script before the closing of \</body>**

```html
<! -- Step 2: Add the Web3Forms script -->
<script src="https://web3forms.com/client/script.js" async defer></script>
```

### Full Code

```html
<form action="https://api.web3forms.com/submit" method="POST">
    <input type="hidden" name="access_key" value="YOUR_ACCESS_KEY_HERE">
    <input type="text" name="name" required>
    <input type="email" name="email" required>
    <textarea name="message" required></textarea>
    
    <! -- Step 1: Add this line -->
    <div class="h-captcha" data-captcha="true"></div>
    
    <button type="submit">Submit Form</button>
</form>

<! -- Step 2: Add the script -->
<script src="https://web3forms.com/client/script.js" async defer></script>
```

If you add just two lines to your contact form, you will get a working hCaptcha to protect your form.&#x20;
