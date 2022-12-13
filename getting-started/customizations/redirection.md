---
description: Customize Success Redirection to your website after form submission
---

# Custom Redirection

## `redirect`

{% hint style="danger" %}
This can be only used if you are using the Default HTML Form without Javascript.

If you are using JavaScript or any other front-end Technology, Please use appropriate redirection method instead. [See Javascript Example](../../how-to-guides/html-and-javascript.md)
{% endhint %}

By default, Web3Forms redirects to our website after form submission, However if you have a custom URL on your website if you want to redirect after a successful form redirection, you can use the `redirect` option. You can set any URL you want. This could be a page on your website or a different website. See the code below. Make sure its an absolute URL with `https://` not relative.&#x20;

#### Examples

```markup
<!-- Default URL -->
<input type="hidden" name="redirect" value="https://web3forms.com/success">

<!-- Custom URL -->
<input type="hidden" name="redirect" value="https://yourwebsite.com/thanks.html">

<!-- Redirect to another website -->
<input type="hidden" name="redirect" value="https://partnerwebsite.com/someaction/">
```

Also, make sure you provide full URL as the value instead of relative URL

```markup

<!-- ❌ Wrong. This won't work -->
<input type="hidden" name="redirect" value="/thanks.html">

<!-- ✅ Correct. Full URL with https:// -->
<input type="hidden" name="redirect" value="https://yourwebsite.com/thanks.html">

```

{% hint style="info" %}
The Input type should be `hidden` and the name should be `redirect`
{% endhint %}
