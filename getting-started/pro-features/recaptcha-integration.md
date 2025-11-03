# reCaptcha Integration

Web3forms supports Google's reCaptcha v3 for forms.&#x20;

**Codepen Demo**: [https://codepen.io/surjithctly/pen/BaZQLyR](https://codepen.io/surjithctly/pen/BaZQLyR)

{% hint style="info" %}
Heads Up! This is a PRO feature. You must have an active subscription to use this feature.
{% endhint %}

### Generate reCaptcha Keys <a href="#add-the-turnstile-widget-to-your-site" id="add-the-turnstile-widget-to-your-site"></a>

To setup, first you should register your domain on Google reCaptcha  and generate API keys from their website. Go to [reCaptcha Website](https://www.google.com/recaptcha/admin/create) to create new keys. Choose reCaptcha v3 from the option. Add your domain name and submit to create your keys. **You will need both Site Key and Secret Key**. Copy those code and save it in your notepad. We will need this later.&#x20;

![Registering reCaptcha](<../../.gitbook/assets/image (4) (2) (2) (2) (2).png>)

### Client-side Integration  <a href="#add-the-turnstile-widget-to-your-site" id="add-the-turnstile-widget-to-your-site"></a>

Now open your HTML file where your form exists and paste the following code just before the closing of `</body>` tag.&#x20;

<pre class="language-markup"><code class="lang-markup">&#x3C;!-- Recaptcha v3 -->

&#x3C;script src="https://www.google.com/recaptcha/api.js?render=<a data-footnote-ref href="#user-content-fn-1">YOUR_SITE_KEY_HERE</a>">&#x3C;/script>
&#x3C;script>
    grecaptcha.ready(function () {
        grecaptcha.execute('<a data-footnote-ref href="#user-content-fn-1">YOUR_SITE_KEY_HERE</a>', {
                action: 'contact'
            })
            .then(function (token) {
                recaptchaResponse.value = token;
            });
    });
    
&#x3C;/script>
</code></pre>

Now replace `YOUR_SITE_KEY_HERE` with your actual Site key you've obtained from the reCaptcha Website. You need to replace it in two places above. `LINE 3` & `LINE 6`

{% hint style="warning" %}
Heads Up! You'll need to change the SITE KEY in two places in the above code.&#x20;
{% endhint %}

Now add the following code inside your `<form>` tag.

```markup
<input type="hidden" name="recaptcha_response" id="recaptchaResponse">
```

### Add Secret Keys to your Web3Forms Dashboard <a href="#add-the-turnstile-widget-to-your-site" id="add-the-turnstile-widget-to-your-site"></a>

1. Visit the Web3Forms Dashboard and select your form.&#x20;
2. Open Settings and choose `recaptcha` as your captcha provider
3. Enter the **Secret Key** in the Textbox below
4. Save Changes

That's it. Your form will automatically be protected with reCaptcha v3.&#x20;



That's it. Now test your form and it should work without any extra configuration.&#x20;

#### How to know the reCaptcha is working as expected?

To test, right click the page and choose **Inspect Element**. Now inspect the `<form>` part where the above `recaptcha_response` will be populated with a large key value. If you don't see that, check `console.log()` for more info.&#x20;

[^1]: update site key here
