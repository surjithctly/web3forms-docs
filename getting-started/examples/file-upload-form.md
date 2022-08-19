# File Upload Form

### File Upload using Multipart/form-data

```html
<form action="https://api.web3forms.com/submit" enctype="multipart/form-data" method="POST">
  <input type="hidden" name="access_key" value="YOUR_ACCESS_KEY_HERE">
  <input type="text" name="name" required>
  <input type="email" name="email" required>
  <input type="file" name="attachment" />
  <button type="submit">Submit Form</button>
</form>
```

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
