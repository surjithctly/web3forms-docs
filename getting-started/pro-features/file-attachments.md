# File Attachments

{% hint style="info" %}
Heads Up! This is a PRO feature. You must have an active membership to use this feature.
{% endhint %}

```markup
<input type="file" name="attachment" />
```

You will need to add `enctype="multipart/form-data"` to the Form Element to make the attachment work.&#x20;

```markup
<form action="https://api.web3forms.com/submit" enctype="multipart/form-data" method="POST">
  ...
  <input type="file" name="attachment" />
  ...  
</form>
```

{% hint style="info" %}
If you are using Javascript / Ajax to submit the form, make sure you set the Headers accordingly. Setting wrong headers will throw an error.&#x20;
{% endhint %}

### Multiple File Attachments

We support multiple file attachments on the contact form. We process them together and send them to you.

```html
<form action="https://api.web3forms.com/submit" enctype="multipart/form-data" method="POST">
  ...
  <label> Your Resume </label>
  <input type="file" name="resume" />
  
  <label> Your Photo </label>
  <input type="file" name="photo" />
  ...  
</form>
```

### Advanced File Uploader

Our Default HTML5 File uploader works only for single files up to 5 MB only. To upload multiple files or larger attachments, we recommend using our Advanced File Uploader. [Please see the guide here](file-attachments.md#undefined)

## File upload with Javascript&#x20;

#### Here's an example code with Javascript

```html
<form id="myForm" method="POST">
  ...
  <input type="file" id="attachment" name="attachment" />
  ...  
  <button type="submit">Submit Form</button>
</form>
```

```javascript
const form = document.getElementById("myForm");

form.addEventListener("submit", function (e) {
  e.preventDefault();
  
  const formData = new FormData(form);
  
  formData.append("access_key", "YOUR_ACCESS_KEY_HERE");
  formData.append("subject", "New Submission from Web3Forms");

  const file = document.getElementById("attachment");
  const filesize = file.files[0].size / 1024;

  if (filesize > 1000) {
    alert("Please upload file less than 1 MB");
    return;
  }
  
  // Don't add `headers` or `content-type` in this fetch call
  // Since it contains attachments, the browser auto-adds them. 
  fetch("https://api.web3forms.com/submit", {
    method: "POST",
    body: formData
  })
    .then(async (response) => {
      let json = await response.json();
      if (response.status == 200) {
        console.log(json.message);
      } else {
        console.log(response);
      }
    })
    .catch((error) => {
      console.log(error);
    })
    .then(function () {
      form.reset();
    });
});

```
