---
description: >-
  hCaptcha is the privacy friendly alternative to Google reCaptcha. Used by
  Cloudflare, Shopify & more..
---

# hCaptcha

<figure><img src="../../../.gitbook/assets/CleanShot 2022-08-19 at 18.47.23.png" alt="" width="306"><figcaption><p>hCaptcha checkbox</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/CleanShot 2024-06-10 at 14.24.39@2x.png" alt="" width="375"><figcaption><p>hcaptcha solve problem</p></figcaption></figure>

Web3Forms provides zero-config integration with hCaptcha. You don't need to setup your own keys or register with them. Just use the following code and add a script. You're done.&#x20;

{% hint style="info" %}
Remember **hCaptcha's** captcha mostly feels a bit difficult for users to solve. In that case, you can either use hCaptcha Paid Plan or use alternatives like hidden [honeypot](spam-protection.md) (less secure) or [reCaptcha](../../pro-features/recaptcha-integration.md) / [Cloudflare Turnstile Captcha](../../pro-features/cloudflare-turnstile-captcha.md) method (Pro).&#x20;
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

### Configuration Options

You can provide all options provided by hCaptcha by default. You need to append the option with `data-*`  attribute. See example below

```markup
 <div class="h-captcha" 
      data-captcha="true" 
      data-lang="de" 
      data-theme="dark"
      data-onload="myFunction"
      data-render="explicit"
      data-size="compact"
      ></div>
```

For more configuration options, visit: [https://docs.hcaptcha.com/configuration](https://docs.hcaptcha.com/configuration)

### Activate hCaptcha to your form

Once everything's setup you need to activate hCaptcha on your form to make it mandatory on each form submissions. For that, submit the form by checking the checkbox once and send the form. Now your hCaptcha will be activated.&#x20;

{% hint style="info" %}
Add Client Side Validation as shown below to prevent form submission without checking the hCaptcha field.&#x20;
{% endhint %}

### Client Side Validation

Use this snippet if you are using the HTML form-embedded method without Javascript to check whether the hCaptcha is filled or not.&#x20;

Add this code block just above the closing of \</body> and make sure `YOUR_FORM_ID` is updated with your form id.&#x20;

```html
<script>
const form = document.getElementById('YOUR_FORM_ID');

form.addEventListener('submit', function(e) {

    const hCaptcha = form.querySelector('textarea[name=h-captcha-response]').value;

    if (!hCaptcha) {
        e.preventDefault();
        alert("Please fill out captcha field")
        return
    }
});
</script>
```

### Manual Setup

If you want to load hCaptcha directly instead of using web3forms proxy, make sure you use the following **sitekey** for free plans. You can set your own site key and secret key on all paid plans,&#x20;

```javascript
// hCaptcha Site Key for Web3Forms
data-sitekey="50b2fe65-b00b-4b9e-ad62-3ba471098be2"
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

## Usage with React / Next.js

To use hCaptcha with React or Next.js, please follow the instructions below.&#x20;

First, install the [@hcaptcha/react-hcaptcha ](https://www.npmjs.com/package/@hcaptcha/react-hcaptcha)package from NPM.&#x20;

```bash
npm install @hcaptcha/react-hcaptcha --save
# or
pnpm add @hcaptcha/react-hcaptcha
```

Then, add the \<HCaptcha/> component inside the form.&#x20;

Make sure you are using `50b2fe65-b00b-4b9e-ad62-3ba471098be2`as the `sitekey` for free plans. Also make sure `reCaptchaCompat` is false.&#x20;

You can use a custom site key if you are on a Paid plan.&#x20;

<pre class="language-jsx"><code class="lang-jsx">import { useForm } from "react-hook-form";
<strong>import HCaptcha from '@hcaptcha/react-hcaptcha';
</strong>
export default function ContactForm() {
  const { register, handleSubmit, setValue } = useForm();
  
<strong>  const onHCaptchaChange = (token) => {
</strong><strong>    setValue("h-captcha-response", token);
</strong><strong>  };
</strong>  
  const onSubmit = async (data) => {
    console.log(data);
    
    await fetch("https://api.web3forms.com/submit", {
      method: "POST",
      body: data
    }).then((res) => res.json());
  }

return (
  &#x3C;form onSubmit={handleSubmit(onSubmit)}>
     {/* // other form fields */}
<strong>      &#x3C;HCaptcha
</strong><strong>         sitekey="50b2fe65-b00b-4b9e-ad62-3ba471098be2"
</strong><strong>         reCaptchaCompat={false}
</strong><strong>         onVerify={onHCaptchaChange} 
</strong>      /> 
  &#x3C;/form>
)}
</code></pre>

That's it.&#x20;

Make sure you have enabled `hcaptcha` as the Block Spam option in the settings. Login to your dashboard to change it if not enabled already.

#### Other implementations

You can see the following guide for more examples. Just make sure you are using the correct `sitekey` as mentioned above.\
\
[https://www.npmjs.com/package/@hcaptcha/react-hcaptcha](https://www.npmjs.com/package/@hcaptcha/react-hcaptcha)&#x20;
