---
description: >-
  For large attachments or multiple file uploads, use our advanced file
  uploader.
---

# Advanced File Uploader

{% hint style="info" %}
Heads Up! This is a PRO feature. You must have an active subscription to use this feature.
{% endhint %}

<figure><img src="../../.gitbook/assets/CleanShot 2024-11-04 at 18.21.54@2x.png" alt="" width="375"><figcaption></figcaption></figure>

Our Default HTML5 File Uploader only supports file attachments up to 5 MB. Also currently it does not support multiple files. If you need to upload large files or multiple files, use our advanced file uploader.

**Step 1: Add a File input inside your form with \`**&#x64;ata-advance&#x64;**\` attribute**

<pre class="language-html"><code class="lang-html">&#x3C;form action="https://api.web3forms.com/submit" method="POST">
  ...
   &#x3C;! -- Step 1: Add this line -->
<strong>   &#x3C;input type="file" data-advanced="true" name="attachment" style="display:none;" />
</strong>  ...
&#x3C;/form>
</code></pre>

{% hint style="info" %}
For advanced uploader, `enctype=""` is not required and must be removed from the `<form>`
{% endhint %}

**Step 2: Add the following script before the closing of \</body>**

```html
<! -- Step 2: Add our script to load the file uploader -->
<script src="https://web3forms.com/client/script.js" async defer></script>
```

### Advanced Options

You can configure some options in the advanced uploader like multiple, accept types, max file size etc. See below:&#x20;

```html
 <input type="file" 
 name="attachment"
 data-advanced="true"                       (enable advanced file upload)
 accept="image/*, application/pdf"          (accept only some file types)
 data-max-files="3"                         (Total number of files allowed)
 data-max-file-size="5MB"                   (Maximum file size for single item)
 data-content="Drag & Drop or <i>Browse<i>" (Custom Label in your language)
  />
```

### Live Demo on Codepen

[https://codepen.io/surjithctly/pen/RwXBQZR](https://codepen.io/surjithctly/pen/RwXBQZR)

### Example Code

```html
<form action="https://api.web3forms.com/submit" method="POST">
    <input type="hidden" name="access_key" value="YOUR_ACCESS_KEY_HERE">
    <input type="text" name="name" required>
    <input type="email" name="email" required>
    <textarea name="message" required></textarea>
    
    <! -- Step 1: Add this line (showing advanced options) -->
  <input
        type="file"
        name="attachment"
        data-advanced="true"
        multiple
        data-max-file-size="3MB"
        data-max-files="3" />
    
    <button type="submit">Submit Form</button>
</form>

<! -- Step 2: Add the script -->
<script src="https://web3forms.com/client/script.js" async defer></script>
```

If you add just two lines to your contact form, you will get an advanced file upload form.&#x20;

{% hint style="info" %}
Note: You do not need to use `multipart/form-data` if you are using our advanced file uploader. You can use the normal method.&#x20;
{% endhint %}

### Styling & Theme

You can set your own theme & style as you wish by overwriting the class names provided by filepond. Here's how a dark theme would look like:

```html
<!-- Dark Theme -->

<style>
  .filepond--panel-root {
    background-color: #2c2c2c;
  }
  .filepond--drop-label {
    color: #d4d4d4;
  }
</style>

```



### Client Side Validation

Use this snippet to make the file upload field required  and to validate if the file is uploaded or not.&#x20;

Add the following code block just above the closing of \</body> and make sure `YOUR_FORM_ID` is updated with your form id.&#x20;

```html
<script>
const form = document.getElementById('YOUR_FORM_ID');

form.addEventListener('submit', function(e) {

    const fileInput = form.querySelector('[name="attachment"]').value;

    if (!fileInput) {
        e.preventDefault();
        alert("Please upload files first!")
        return
    }
});
</script>
```

## Usage with React

Iif you are using react, we suggest you to use the Filepond Library directly.&#x20;

Also check: [Filepond React](https://github.com/pqina/react-filepond)

**File Uploader Widget**

```jsx
import React, { useState } from 'react';
import { FilePond, registerPlugin } from 'react-filepond';
import 'filepond/dist/filepond.min.css';

// Register plugins if needed
// registerPlugin(FilePondPluginImageExifOrientation, FilePondPluginImagePreview);

function FileUploader() {
  const [files, setFiles] = useState([]);

  const getPresignedUrl = async (file) => {
    try {
      const response = await fetch(`https://api.web3forms.com/upload?file=${file.name}`);
      const data = await response.json();
      return data;
    } catch (error) {
      console.error('Error generating pre-signed URL:', error);
      throw error;
    }
  };

  return (
    <FilePond
      files={files}
      onupdatefiles={setFiles}
      allowMultiple={true}
      maxFiles={3}
      name="attachment"
      labelIdle='Drag & Drop your files or <span class="filepond--label-action">Browse</span>'
      server={{
        process: async (fieldName, file, metadata, load, error, progress, abort, transfer, options) => {
          try {
            const { url, key } = await getPresignedUrl(file);
            
            const response = await fetch(url, {
              method: 'PUT',
              body: file,
              headers: {
                'Content-Type': file.type,
              },
            });

            if (response.ok) {
              load(key);
            } else {
              error('Upload failed');
            }
          } catch (err) {
            error('Error uploading file');
          }
        },
      }}
    />
  );
}

export default FileUploader;
```

**Using it with Vanilla React**

```jsx
import React from 'react';
import FileUploader from './FileUploader';

function App() {
  return (
    <div className="App">
      <h1>File Upload Example</h1>
      <form method="POST" action="https://api.web3forms.com/submit">
        <input
          type="hidden"
          name="access_key"
          value="c00d70af-1ca3-466d-98a7-c82408e76e91"
        />
        <input type="text" name="First Name" />
        <FileUploader />
        <input type="submit" value="Submit" />
      </form>
    </div>
  );
}

export default App;
```



**Usage with React Hook Form**

```jsx
import { useForm, Controller } from "react-hook-form";
import FileUploader from './FileUploader';

export default function Support() {
  const { register, handleSubmit } = useForm({
    mode: "onTouched",
  });

  const onSubmit = async (data, e) => {
    // Replace with actual call to Web3Forms
    console.log(data);
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input type="text" {...register("name")} />
      <Controller
        control={control}
        name="attachment"
        render={({ field }) => (
          <FileUploader
            onChange={(e) => field.onChange(e.cdnUrl)}
          />
        )}
      />
      <button type="submit">Submit</button>
    </form>
  );
}

```
