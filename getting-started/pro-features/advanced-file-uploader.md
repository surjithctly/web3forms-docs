---
description: >-
  For large attachments or multiple file uploads, use our advanced file
  uploader.
---

# Advanced File Uploader

Our Default HTML5 File Uploader only supports file attachments up to 5 MB. Also currently it does not support multiple files. If you need to upload large files or multiple files, use our advanced file uploader.

**Step 1: Add a hidden \<input> inside your form with \`**data-fileupload**\` attribute**

```html
<form>
  ...
   <! -- Step 1: Add this line -->
   <input type="hidden" data-fileupload="true" />
  ...
</form>
```

**Step 2: Add the following script before the closing of \</body>**

```html
<! -- Step 2: Add the Web3Forms script -->
<script src="https://web3forms.com/client/script.js" async defer></script>
```

{% hint style="info" %}
Heads Up! This is a PRO feature. You must have an active membership to use this feature.
{% endhint %}

### Full Code

```html
<form action="https://api.web3forms.com/submit" method="POST">
    <input type="hidden" name="access_key" value="YOUR_ACCESS_KEY_HERE">
    <input type="text" name="name" required>
    <input type="email" name="email" required>
    <textarea name="message" required></textarea>
    
    <! -- Step 1: Add this line -->
    <input type="hidden" data-fileupload="true" />
    
    <button type="submit">Submit Form</button>
</form>

<! -- Step 2: Add the script -->
<script src="https://web3forms.com/client/script.js" async defer></script>
```

If you add just two lines to your contact form, you will get an advanced file upload form.&#x20;

### File Upload Options

You may also pass many options to the file upload using data-\* attributes. Here are some of the following:

| Data Attribute          | Default Value   | Description                                                              |
| ----------------------- | --------------- | ------------------------------------------------------------------------ |
| `data-multiple`         | `false`         | Add this as `data-multiple="true"` if you want to allow multiple files.  |
| `data-maxsize`          | `NA`            | Maximum File Size in MB. eg: `"10"` for 10 MB `"0.5"` for 500 KB         |
| `data-button-text`      | `Upload a File` | File Upload Button Text                                                  |
| `data-background-color` | `#2a2a2a`       | File Upload button background color. Values in Hex                       |
| `data-text-color`       | `#FFFFFF`       | File Upload button text color. Values in Hex                             |

Our File Upload API is powered by [UploadCare](https://uploadcare.com/). So you can also add any `data-*` attributes supported by them. [See more available options here](https://uploadcare.com/docs/uploads/file-uploader-options/)
