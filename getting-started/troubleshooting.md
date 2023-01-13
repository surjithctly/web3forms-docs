---
description: Here are common issues with Web3Forms and how to fix them.
---

# Troubleshooting

## Form submitted successfully but email not received

Form Submission Emails are sent instantly and will reach your inbox in seconds. In rare cases, it can take up to 1-2 minutes. Even if you don't receive any email after waiting, please make sure you check the "Promotions" or "Updates" tab if you are using Gmail. Otherwise, you can check the "Spam/Junk" folder once to confirm the email is landed there.&#x20;

Once you have received the email, it is recommended to drag the email to your Primary Inbox and press "YES" when asked if you want to mark future emails as important. So all future emails from our `notify+{hash}@web3forms.com` will reach your primary inbox.&#x20;

## Email received without any data

Ensure you have added a `name` attribute to each of your form elements. Form data is processed only if `name` attribute is present in the formData.&#x20;

```markup
<!-- ❌ Wrong -->

<label>Full Name</label>
<input type="text" placeholder="Full Name" />

<!-- ✅ Correct -->

<label>Full Name</label>
<input type="text" name="full_name" placeholder="Full Name" />

```

## CORS Error

Sometimes, you might receive a following error message while submitting form to web3forms.&#x20;

{% hint style="info" %}
_Access to fetch at `https://api.web3forms.com/submit` from origin `https://yourwebsite.com` has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header is present on the requested resource. If an opaque response serves your needs, set the request's mode to 'no-cors' to fetch the resource with CORS disabled._
{% endhint %}

This is not an issue with Web3Forms, but it can be easily fixed by modifying your code. By default Web3Forms allow CORS from any website, but here are few things you need to keep in mind to fix them:

Web3Forms supports two types of Content-Type

1. `x-www-form-urlencoded`
2. `application/json`

The first one is used by the browser automatically when submitting the form using the default HTML Method, There is nothing you need to configure and it works as expected in modern browsers.&#x20;

The `application/json` is however to be used while sending the formData from Javascript or from your framework. So the server will return `application/json` to the client as well. Now you can show success message based on the return json.&#x20;

### How to fix the CORS Error in Web3Forms?

The CORS error usually happens when you mix javascript and form-urlencoded together.&#x20;

You should never use `x-www-form-urlencoded` while sending data through Web3Forms as it returns a `301` redirect after form submission. This will result in a CORS error for the user while the message delivers as usual. &#x20;

To fix the issue, you must always use `application/json` for custom POST method or use the [FormData()](https://developer.mozilla.org/en-US/docs/Web/API/FormData) function provided by Javascript. This will ensure correct response from Web3Forms server.&#x20;

```javascript
// ❌ Wrong 

const response = await fetch('https://api.web3forms.com/submit', {
   method: 'POST',
   headers: {
     'Content-Type': 'x-www-form-urlencoded',
   },
   body: JSON.stringify(data),
});



// ✅ Correct

const response = await fetch('https://api.web3forms.com/submit', {
   method: 'POST',
   headers: {
     'Content-Type': 'application/json',
   },
   body: JSON.stringify(data),
});

```

## 403: Forbidden

In some rare cases, you/your customers might receive `{ message: forbidden }` error with HTTP code `403`  from our server. This is usually because the IP address might have triggered our firewall. This usually happens when the IP has been previously blacklisted for Spam activity. Sometimes, It happens on broadband connections with pooled IP as well.

If you got this error and you think it's a mistake, please contact support for further assistance.&#x20;

## Message Marked as Spam

Our server protects from spam attacks for our users. But occasionally, it might happen while testing the form. This is usually because some test words we use might trigger our spam server. So to fix it, make sure you add input data as natural as possible.&#x20;

If issue persists, please contact support.&#x20;

