# File Attachments

{% hint style="info" %}
Heads Up! This is a PRO feature. You must have an active membership to use this feature.
{% endhint %}

```markup
<input type="file" name="attachment" />
```

You will need to add `enctype="multipart/form-data"` to the Form Element to make the attachment work. 

```markup
<form action="https://api.web3forms.com/submit" enctype="multipart/form-data" method="POST">
  ...
  <input type="file" name="attachment" />
  ...  
</form>
```

{% hint style="info" %}
If you are using Javascript / Ajax to submit the form, make sure you set the Headers accordingly. Setting wrong headers will throw an error. 
{% endhint %}

#### Here's an example code with Javascript

```javascript
async function submitForm(form) {
    const formData = new FormData(form);
    try {
        const response = await fetch("https://api.web3forms.com/submit", {
            method: "POST",
            body: formData
        });
        // No need to set headers here
        // Javascript does that automatically
        let json = await response.json();
        this.submitting = false;

        if (response.status == 200) {
            this.success = true;
        } else {
            this.error = true;
        }
    } catch (error) {
        console.log(error);
    }
}

  
```

