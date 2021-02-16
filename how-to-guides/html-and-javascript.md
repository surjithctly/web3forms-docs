# HTML & JavaScript

Sometimes you want to use JavaScript to submit the form and its possible with Web3Forms. If you use JavaScript, you can keep users on the same page instead of redirecting to other page. Also you will be able to code custom form validation or integration with other tools / services.

The initial steps are same as [Pure HTML](../getting-started/installation.md#step-01-get-access-key). Be sure to check to know how to create Access Key. Then use the following sample code to get started. Modify it according to your needs.

## HTML

```markup
<form method="POST" id="form">

    <input type="hidden" name="apikey" value="YOUR_ACCESS_KEY_HERE">
    <input type="hidden" name="subject" value="New Submission from Web3Forms">
    <input type="checkbox" name="botcheck" id="" style="display: none;">

    <!-- Custom Form Data -->
    <input type="email" name="email" required>
    <input type="text" name="name" required>
    <input type="text" name="phone" required>
    <textarea name="message" required></textarea>

    <button type="submit">Submit</button>

    <div id="result"></div>

</form>
```

## JavaScript

```javascript
const form = document.getElementById('form');
const result = document.getElementById('result');

form.addEventListener('submit', function(e) {
    const formData = new FormData(form);
    e.preventDefault();
    var object = {};
    formData.forEach((value, key) => {
        object[key] = value
    });
    var json = JSON.stringify(object);
    result.innerHTML = "Please wait..."

    fetch('https://api.web3forms.com/submit', {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json',
                'Accept': 'application/json'
            },
            body: json
        })
        .then(async (response) => {
            let json = await response.json();
            if (response.status == 200) {
                result.innerHTML = json.message;
            } else {
                console.log(response);
                result.innerHTML = json.message;
            }
        })
        .catch(error => {
            console.log(error);
            result.innerHTML = "Something went wrong!";
        })
        .then(function() {
            form.reset();
            setTimeout(() => {
                result.style.display = "none";
            }, 3000);
        });
});
```

