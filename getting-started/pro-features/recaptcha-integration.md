# reCaptcha Integration

Web3forms supports Google's reCaptcha for forms. We recommend to use the v3 version since its easy for humans and hard for bots.&#x20;

**Codepen Demo**: [https://codepen.io/surjithctly/pen/BaZQLyR](https://codepen.io/surjithctly/pen/BaZQLyR)

{% hint style="info" %}
Heads Up! This is a PRO feature. You must have an active membership to use this feature.
{% endhint %}

To setup, first you should register your domain on Google reCaptcha  and generate API keys from their website. Go to [reCaptcha Website](https://www.google.com/recaptcha/admin/create) to create new keys. Choose reCaptcha v3 from the option. Add your domain name and submit to create your keys. You will need both Site Key and Secret Key. Copy those code and save it in your notepad. We will need this later.&#x20;

![Registering reCaptcha](<../../.gitbook/assets/image (4) (2) (2) (2) (2).png>)

Now go to [https://web3forms.com/pro](https://web3forms.com/pro) page and add your reCaptcha Secret Key and save the form.&#x20;

Now open your HTML file where your form exists and paste the following code just before the closing of `</body>` tag.&#x20;

```markup
<!-- Recaptcha v3 -->

<script src="https://www.google.com/recaptcha/api.js?render=YOUR_SITE_KEY_HERE"></script>
<script>
    grecaptcha.ready(function () {
        grecaptcha.execute('YOUR_SITE_KEY_HERE', {
                action: 'contact'
            })
            .then(function (token) {
                recaptchaResponse.value = token;
            });
    });
    
</script>
```

Now replace `YOUR_SITE_KEY_HERE` with your actual Site key you've obtained from the reCaptcha Website. You need to replace it in two places above. `LINE 3` & `LINE 6`

{% hint style="warning" %}
Heads Up! You'll need to change the SITE KEY in two places in the above code.&#x20;
{% endhint %}

Now add the following code inside your `<form>` tag.

```markup
<input type="hidden" name="recaptcha_response" id="recaptchaResponse">
```

That's it. Now test your form and it should work without any extra configuration.&#x20;

#### How to know the reCaptcha is working as expected?

To test, right click the page and choose **Inspect Element**. Now inspect the `<form>` part where the above `recaptcha_response` will be populated with a large key value. If you don't see that, check `console.log()` for more info.&#x20;
