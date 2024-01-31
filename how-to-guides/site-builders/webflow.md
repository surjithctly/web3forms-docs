---
description: >-
  Here's a guide on how to integrate Web3Forms with Webflow using Form Block and
  HTML Embed
---

# Webflow

**Example Demo:** [**https://web3forms-contact-form.webflow.io/**](https://web3forms-contact-form.webflow.io/)

### 1. Create a Form Block in Webflow

First, you need to drag the form block element from the Webflow sidebar to your website.&#x20;

<figure><img src="../../.gitbook/assets/CleanShot 2024-01-31 at 13.59.59@2x.png" alt="" width="282"><figcaption><p>Drag the form block the canvas</p></figcaption></figure>

### 2. Create a hidden input field in Webflow

To add our access key, we need to create a hidden input field in webflow to make our contact form work. For that, we use the HTML Embed Option.

<figure><img src="../../.gitbook/assets/CleanShot 2024-01-31 at 14.23.49@2x (1).png" alt="" width="245"><figcaption><p>Drag Embed Option inside the &#x3C;Form> Block</p></figcaption></figure>

### 3. Add Access Key inside the HTML Embed Block

Now, add the hidden HTML Code as shown below inside the code editor and click Save.&#x20;

<figure><img src="../../.gitbook/assets/CleanShot 2024-01-31 at 14.28.40@2x.png" alt="" width="563"><figcaption></figcaption></figure>

Make sure the embed block is inside the Form Block.

<figure><img src="../../.gitbook/assets/CleanShot 2024-01-31 at 14.30.49@2x.png" alt="" width="241"><figcaption></figcaption></figure>

### 4. Add Form Action URL

Now, setup the form action URL by selecting the form element and choose "Settings" from the right sidebar.  Make sure you select **`POST`** as method.&#x20;

Action URL: `https://api.web3forms.com/submit`

<figure><img src="../../.gitbook/assets/CleanShot 2024-01-31 at 14.33.30@2x.png" alt="" width="240"><figcaption></figcaption></figure>

### 5. Done.&#x20;

That's it. Web3forms Contact form will work with your Webflow Website now. You can add more customization features like custom redirect, email subject etc using the hidden field similar to step 3. Refer to the [Customizations](../../getting-started/customizations/) section for more details.
