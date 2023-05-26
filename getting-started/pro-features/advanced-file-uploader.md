---
description: >-
  For large attachments or multiple file uploads, use our advanced file
  uploader.
---

# Advanced File Uploader

{% hint style="info" %}
Heads Up! This is a PRO feature. You must have an active membership to use this feature.
{% endhint %}

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

### Live Demo on Codepen

{% embed url="https://codepen.io/surjithctly/pen/NWMeJzQ" %}
[https://codepen.io/surjithctly/pen/NWMeJzQ](https://codepen.io/surjithctly/pen/NWMeJzQ)
{% endembed %}

### Full Code

```html
<form action="https://api.web3forms.com/submit" method="POST">
    <input type="hidden" name="access_key" value="YOUR_ACCESS_KEY_HERE">
    <input type="text" name="name" required>
    <input type="email" name="email" required>
    <textarea name="message" required></textarea>
    
    <! -- Step 1: Add this line -->
    <input type="hidden" data-fileupload="true" data-maxsize="2" data-images-only="true" />
    
    <button type="submit">Submit Form</button>
</form>

<! -- Step 2: Add the script -->
<script src="https://web3forms.com/client/script.js" async defer></script>
```

If you add just two lines to your contact form, you will get an advanced file upload form.&#x20;

{% hint style="info" %}
Note: You do not need to use `multipart/form-data` if you are using our advanced file uploader. You can just use the normal method.&#x20;
{% endhint %}

### File Upload Options

You may also pass many options to the file upload using data-\* attributes. Here are some of the following:

<table><thead><tr><th width="264">Data Attribute</th><th width="169">Default Value</th><th>Description</th></tr></thead><tbody><tr><td><code>data-multiple</code></td><td><code>false</code></td><td>Set to <code>true</code> if you want to allow multiple files. </td></tr><tr><td><code>data-maxsize</code></td><td><code>NA</code></td><td>Maximum File Size in MB. eg: <code>"10"</code> for 10 MB <code>"0.5"</code> for 500 KB</td></tr><tr><td><code>data-images-only</code></td><td><code>false</code></td><td>Set to <code>true</code> to allow only image files. </td></tr><tr><td><code>data-button-text</code></td><td><code>Upload a File</code></td><td>File Upload Button Text</td></tr><tr><td><code>data-background-color</code></td><td><code>#2a2a2a</code></td><td>File Upload button background color. Values in Hex</td></tr><tr><td><code>data-text-color</code></td><td><code>#FFFFFF</code></td><td>File Upload button text color. Values in Hex</td></tr></tbody></table>

Our File Upload API is powered by [UploadCare](https://uploadcare.com/). So you can also add any `data-*` attributes supported by them. [See more available options here](https://uploadcare.com/docs/uploads/file-uploader-options/)



### Client Side Validation

Use this snippet to make file upload a required filed and to validate if the file is uploaded or not.&#x20;

Add the following code block just above the closing of \</body> and make sure `YOUR_FORM_ID` is updated with your form id.&#x20;

```html
<script>
const form = document.getElementById('YOUR_FORM_ID');

form.addEventListener('submit', function(e) {

    const fileInput = form.querySelector('[data-fileupload="true"]').value;

    if (!fileInput) {
        e.preventDefault();
        alert("Please upload files first!")
        return
    }
});
</script>
```

## React & React Hook Form

If you are using React with React Hook form, The attachment field might not send properly. To set up, use the following method.&#x20;

You can use the Web3Forms Public Key (as shown below) or create your own from UploadCare if you want to store data.&#x20;

```jsx
import { useForm, Controller } from "react-hook-form";
import { Widget } from "@uploadcare/react-widget";

export default function Support() {
  const { register, handleSubmit } = useForm({
    mode: "onTouched",
  });

  const onSubmit = async (data, e) => {
    // Replace with actual call to Web3Forms
    console.log(data);
  };

  const css = `.uploadcare--widget__button.uploadcare--widget__button_type_open {
  background-color: #dfdfdf;
  color:  #444444;
  }`;

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input type="text" {...register("name")} />
      <Controller
        control={control}
        name="attachment"
        render={({ field }) => (
          <Widget
            publicKey="a0e4fd45fb9d5fed7599"
            name="attachment"
            multiple
            systemDialog
            onChange={(e) => field.onChange(e.cdnUrl)}
            previewStep="true"
          />
        )}
      />
      <style>{css}</style>
      <button type="submit">Submit</button>
    </form>
  );
}

```
