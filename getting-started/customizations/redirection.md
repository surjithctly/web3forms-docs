---
description: Customize Success Redirection to another page
---

# Success Redirection

## `redirect`

{% hint style="danger" %}
This can be only used if you are using the HTML Only Form.

If you are using JavaScript or any other front-end Technology, Please use their redirection method instead. [See Javascript Example](../../how-to-guides/html-and-javascript.md)
{% endhint %}

By default, Web3Forms outputs JSON data, This will become less user friendly if you does not use any front-end validation. Thus, we have provided a handy option to set success redirection. You can set any URL you want. This could be a page on your website or a different website. See the code below.

```markup
<input type="hidden" name="redirect" value="https://web3forms.com/success">
```

{% hint style="info" %}
The Input type should be `hidden` and the name should be `redirect`
{% endhint %}

