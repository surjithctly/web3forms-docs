---
description: Here are common issues with Web3Forms and how to fix them.
---

# Troubleshooting

## Form submitted successfully but email not received

Form Submission Emails are sent instantly and will reach your inbox in seconds. In rare cases, it can take up to 1-2 minutes. Even if you don't receive any email after waiting, please make sure you check the "Promotions" or "Updates" tab if you are using Gmail. Otherwise, you can check the "Spam/Junk" folder once to confirm the email is landed there.&#x20;

Once you have received the email, it is recommended to drag the email to your Primary Inbox and press "YES" when asked if you want to mark future emails as important. So all future emails from our `notify+{hash}@web3forms.com` will reach your primary inbox.&#x20;

### **Bounced Emails**

Another chance is that sometimes the email might be bounced. Thus it will prevent all subsequent request to that particular email. This usally happens when you create an Access key before the email is configured. \
\
If that's the case, [contact support](https://web3forms.com/help?contact=true) and we will remove it from the **suppression list**.&#x20;

### Missing MX Records

Make sure your domain has proper MX records set as suggested by your email provider. If no MX records found, we cannot deliver your message.&#x20;

Verify your MX records here:

{% embed url="https://dnschecker.org/mx-lookup.php" %}

{% embed url="https://mxtoolbox.com/MXLookup.aspx" %}

#### Google Workspace issues

If you are using Google workspace, [check this link](https://support.google.com/a/answer/16004259?sjid=8694392699073914797-NC\&visit_id=639034785281386808-3518368676\&rd=1) to setup MX records for your email domain. Also make sure web3forms.com domain is allowed:&#x20;

Contact Your Email Admin: If you are part of a larger organization, please check with your Google Workspace administrator to see if there are any current network issues or aggressive filtering rules for incoming mail.

Check: Google Workspace > Gmail > Spam, Phishing, and Malware screen

## Email received without any data

Ensure you have added a `name` attribute to each of your form elements. Form data is processed only if `name` attribute is present in the formData.&#x20;

```html
<!-- ❌ Wrong -->

<label>Full Name</label>
<input type="text" placeholder="Full Name" />

<!-- ✅ Correct -->

<label>Full Name</label>
<input type="text" name="full_name" placeholder="Full Name" />

```

## Emails going to Spam/Junk Folder

if your Web3Forms Submission emails lands in your email provider's spam/junk folder especially if you are using hotmail or outlook, follow the steps.&#x20;

1. Add _`notify@web3forms.com`_ email to your contact list
2. Add our domain `web3forms.com` to your safe sender's list

<figure><img src="../.gitbook/assets/CleanShot 2024-06-12 at 13.05.00@2x.png" alt=""><figcaption><p>enabling safe sender in outlook</p></figcaption></figure>

**In Gmail:**

1. Manually mark a few of the emails as Not Spam / Not Junk
2. Move a few emails to your Primary/Main Inbox Tab
3. Add a filter to enable "Never Send to Spam" for emails coming from Web3Forms.&#x20;

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

The `application/json` is however to be used while sending the formData from Javascript or from your framework. So the server will return `application/json` to the client as well. Now you can show success message based on the return json or redirect to another page.&#x20;

### How to fix the CORS Error in Web3Forms?

#### **301 Redirect Cors Error**

If you are using the javascript method to send the form, you should not use `redirect` in the HTML form. You should remove that and add the redirect inside the javascript success callback using `window.location.href`

```html
// ❌ Wrong

<form id="javascript_form" method="POST">
     ...
    <input type="hidden" name="redirect" value="https://web3forms.com/success">
     ...
</form> 



// ✅ Correct

<form id="javascript_form" method="POST">
     ... 
</form> 

<script>
// ...
.then(async (response) => {
  let json = await response.json();
  if (response.status == 200) {
      window.location.href = "success.html" // <-- add this line
  }
// ...   
</script>
```

#### Mixed Content-Type Error

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

## Form works locally, but not working on my hosted domain.&#x20;

To prevent spam & abuse, we block certain domains, sub-domains & LTDs by default. If your form works as expected in localhost and not working in your custom domain website,  please [contact us](https://web3forms.com/contact) with the domain name to review. Once approved, you can submit form as usual.&#x20;

To approve certain free sub-domains provided by some platforms won't be approved. So please add a custom domain and contact us if its not working. Otherwise, you would need a paid plan to allow the free sub-domain.&#x20;

## 403 : This method is not allowed

Web3Forms API is expected to run on client side for spam prevention. If you call the API on the server side, you might get this method is not allowed error.&#x20;

To fix this, make sure you run our API on the client side. Our API fetch should be visible in the network tab in browser developer console. Do not proxy it in another API or server side code. The access key can be public and safe to add in client side code.&#x20;

If your use-case require you to use server side code, then you must add your server IP address to our Safelist + you must have an active **Paid** subscription. Please contact support with your server IP to activate server side API calls.&#x20;

## 429: Rate limited because of too many requests

When we detect too many requests from single IP address in a short period of time, we block the IP for a certain period temporarily to prevent spamming or abuse of our system.&#x20;

If you get this error, which means you tried to submit forms too many times quickly. Please wait for one hour and try again. For testing, make sure you take some time for each submissions to avoid rate-limits.&#x20;

Rate-limits for your IP address will be removed automatically after one hour.&#x20;

