# Installation

## Step 01: Get Access Key

First step is to get an Access Key from Web3Forms. [Create Access Key](https://web3forms.com/#start)

Once you submit the form, you will get the Access key in your Email. Copy that key so that we can use this later.

## Step 2: Create HTML Form

Create a form in your website with our form endpoint inside action attribute. Following is a simple example on how it should look like:

{% tabs %}
{% tab title="Basic Example" %}
```markup
<form action="https://api.web3forms.com/submit" method="POST">

    <input type="hidden" name="access_key" value="YOUR_ACCESS_KEY_HERE">

    <input type="text" name="name" required>
    <input type="email" name="email" required>
    <textarea name="message" required></textarea>
    <input type="hidden" name="redirect" value="https://web3forms.com/success">
    <button type="submit">Submit Form</button>

</form>
```
{% endtab %}

{% tab title="Advanced Example" %}
```markup
<form action="https://api.web3forms.com/submit" method="POST">

    <!-- REQUIRED: Your Access key here. Don't worry this can be public -->
    <!-- Create your Access key here: https://web3forms.com/ -->
    <!-- <input type="hidden" name="apikey" value="YOUR_ACCESS_KEY_HERE"> -->
    <input type="hidden" name="access_key" value="YOUR_ACCESS_KEY_HERE">

    <!-- Optional: Can be type="hidden" or type="text" for subject -->
    <input type="hidden" name="subject" value="New Submission from Web3Forms">
  
    <!-- Optional: From Name you want to see in the email
          Default is "Notifications". you can overwrite here -->
    <input type="hidden" name="from_name" value="Your Website Name">
  
    <!-- Optional: To send the form submission as CC email -->
    <input type="hidden" name="ccemail" value="partner@example.com">

    <!-- Optional: default replyto will be "email" (if available), 
         you may overwrite here -->
    <input type="hidden" name="replyto" value="customer@example.com">

    <!-- Required: if submitting without Javascript 
         (because by default web3form outputs json) -->

    <!-- If javascript, use "window.location.hash" for redirects -->
    <input type="hidden" name="redirect" value="https://web3forms.com/success">

    <!-- Optional: But Recommended: To Prevent SPAM Submission. 
         Make sure its hidden by default -->
    <input type="checkbox" name="botcheck" id="" style="display: none;">
    
    <!-- Webhooks: Send your form data to Notion, Google Sheets or Zapier.
         This feature available to PRO & Starter Plan users only -->
    <input type="hidden" name="webhook" value="WEBHOOK_URL_HERE" />

    <!-- Google reCaptcha v3: To Prevent SPAM Submission.PRO Plan only -->
    <input type="hidden" name="recaptcha_response" id="recaptchaResponse">
    
    <!-- Attachments: Make sure the <form> has enctype="multipart/form-data"
         This feature available to PRO Plan users only -->
    <input type="file" name="attachment" />

    <!-- Custom Form Data: 
     Then you can include your own form data you wish to receive in email. -->
    <input type="email" name="email" required>
    <input type="text" name="First Name" required>
    <input type="text" name="Phone Number" required>
    <textarea name="message" cols="30" rows="10" required></textarea>

    <button type="submit">Submit Form</button>

</form>
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Make sure you added \`name\` attribute, form action URL and the \`access\_key\` to make the form work as expected &#x20;
{% endhint %}

## Step 3: Add your Access Key

Add your access key to start receiving email submissions.

```markup
<input type="hidden" name="apikey" value="YOUR_ACCESS_KEY_HERE">
```

## Step 4: Done

That's it. Run your code on a browser and it should work. This is a simple starting example. However you can customize it with unlimited possibilities. Checkout other pages to know more.
