---
description: >-
  Here's a guide on how to integrate Custom Contact Forms in Framer using
  Web3Forms
---

# Framer

Here's a step by step instructions on how to setup Web3Forms with the new Framer Forms feature.&#x20;

### Framer forms Pricing&#x20;

Framer forms is providing only 50 submissions per month for free. Once you upgrade to Basic which is $15/m or Pro for $30/mo, you will get 500 & 2500 submissions per month respectively.&#x20;

In contrast, using Web3Forms, you will get 250 free submissions per month. Web3Forms provides unlimited submissions for Pro plans which start from $8/mo.

_Source:_ [_https://www.framer.com/pricing/_](https://www.framer.com/pricing/) _&_ [_https://web3forms.com/pricing_](https://web3forms.com/pricing)

However, you can now use Web3Forms in Framer. Here are the step by step instructions on how you can use it.&#x20;

{% hint style="info" %}
Currently, Framer uses their own proxy for the Web3Forms endpoint which is causing to hit the Framer limit once 50 submissions are reached. You must contact Framer support and ask them to remove the proxy and let you use our endpoint directly.&#x20;
{% endhint %}

## Step 1: Drag and Drop the form builder

Once you are on the framer project, Click on Insert -> Form -> Form Builder. The drag them to your canvas.&#x20;

<figure><img src="../../.gitbook/assets/CleanShot 2024-06-28 at 12.54.58@2x.png" alt=""><figcaption></figcaption></figure>

## Step 2: Add Web3Forms Access Key

Once you drag and drop the form, you can then add a hidden access\_key you have generated from Web3Forms Home Page.&#x20;

Click on the + button below the form and add a new "Text" field.&#x20;

<div align="center">

<figure><img src="../../.gitbook/assets/CleanShot 2024-06-28 at 13.12.23@2x.png" alt="" width="563"><figcaption></figcaption></figure>

</div>

Click on the **Label** and remove it. We do not need that for this input.&#x20;

Now, click on that textbox field which opens up a right side panel. Click on the **+** button right to the text Input and choose **Hidden.** Now click the + again to add the **Value** field.&#x20;

<figure><img src="../../.gitbook/assets/CleanShot 2024-06-28 at 13.28.03@2x.png" alt=""><figcaption></figcaption></figure>

Now, edit the following:

Change Type to Text.&#x20;

Name: access\_key

Value: Insert your access\_key here

Placeholder: Remove Value

Required: Yes

<figure><img src="../../.gitbook/assets/CleanShot 2024-06-28 at 13.21.59@2x.png" alt="" width="334"><figcaption></figcaption></figure>

## Step 3: Add Web3Forms Endpoint

Now, click on the main Form wrapper which opens up a Form panel in the right sidebar.&#x20;

Click on the Send To dropdown and choose Webhook. Then add the Web3Forms API endpoint in the Popup. Our endpoint is: `https://api.web3forms.com/submit`

<figure><img src="../../.gitbook/assets/CleanShot 2024-06-28 at 13.35.41@2x.png" alt="" width="563"><figcaption></figcaption></figure>

## Step 4: Test & Publish

That's it. Done. You can customize form fields as per your requirement or add more hidden inputs for customizing email subject, from\_name etc. Once done. Click on the Play button to preview the website. If everything's good, you can publish the framer website. Now you have a fully customizable working contact form in Framer.&#x20;

{% hint style="danger" %}
Currently, Framer uses their own proxy for the Web3Forms endpoint which is causing to hit the Framer limit once 50 submissions are reached. You must contact Framer support and ask them to remove the proxy and let you use our endpoint directly.&#x20;
{% endhint %}

If this method does not work for you, you can choose the old method which still works. Here are the steps:

## Framer Forms - Old Method

Framer default contact form is limited. It only allows 2-3 fields and only support a single form backend solution. Using Web3Forms, you can setup a free custom contact form in framer without any custom code. Open the demo website, duplicate the page and you can copy-paste the section to your own project and add unlimited fields and inputs without limitation.&#x20;

**Example Demo:** [**https://web3forms.framer.website/**](https://web3forms.framer.website/)

### **Step 1: Remix / Duplicate the Form Component**

Visit our demo link above and click on the Remix / Duplicate link in the top right corner. Then a copy of the same page will be opened in your Framer Workspace.&#x20;

<figure><img src="../../.gitbook/assets/CleanShot 2024-02-03 at 13.57.32@2x.png" alt="" width="563"><figcaption><p>Remix Button in the Pre-made Demo</p></figcaption></figure>

### Step 2: Add Access Key in a hidden input field

Once you duplicated the project, you can copy it again to your project. Once it's on the page you wanted, click on the Web3Forms Form Area and it will open the Sidebar with customization options.&#x20;

<figure><img src="../../.gitbook/assets/CleanShot 2024-02-03 at 14.01.32@2x.png" alt="" width="252"><figcaption><p>Web3Forms Customization Options</p></figcaption></figure>

Now, Click on the **Inputs** and choose Access Key in the bottom. &#x20;

<div align="center">

<figure><img src="../../.gitbook/assets/CleanShot 2024-02-03 at 14.03.10@2x.png" alt="" width="250"><figcaption></figcaption></figure>

</div>

Then, in the panel, replace the `YOUR_ACCESS_KEY_HERE` value with your own access key from Web3Forms.&#x20;

<figure><img src="../../.gitbook/assets/CleanShot 2024-02-03 at 14.04.29@2x (1).png" alt="" width="248"><figcaption><p>Replace Access Key with yours</p></figcaption></figure>

### Step 3: Customize yourself

You can add more inputs, change name, values or even style by double clicking and edit the code.  Have fun!
