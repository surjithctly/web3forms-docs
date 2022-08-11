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

## File upload with Javascript&#x20;

#### Here's an example code with Javascript

```html
<form id="myForm" method="POST">
  ...
  <input type="file" name="attachment" />
  ...  
  <button type="submit">Submit Form</button>
</form>
```

```javascript
const form = document.getElementById("myForm");

form.addEventListener("submit", function (e) {
  const formData = new FormData(form);
  e.preventDefault();

  const file = document.getElementById("attachment");
  const filesize = file.files[0].size / 1024;

  if (filesize > 1000) {
    alert("Please upload file less than 1 MB");
    return;
  }

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
