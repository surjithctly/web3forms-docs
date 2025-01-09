---
description: Customize your notification email subject
---

# Email Subject line

## `subject`

There are two ways you can setup Email Subject.

## 1. Pre-defined Subject

You can add a pre-defined subject by adding a form `input` with `type="hidden"` along with your subject in `value`. See the code below.

```markup
<input type="hidden" name="subject" value="New Submission from Web3Forms">
```

## 2. User Generated Subject

In this case, the subject can be filled by the website visitor. For that, you can use an input `type="text"`. See Code below.

```markup
<input type="text" name="subject" />
```

{% hint style="info" %}
The Name attribute must be called `subject`
{% endhint %}

### 3. Custom Subject with User Input Value

You can also customize the subject value to include user submitted value such as their first name. This will be easier to manage in emails when you have multiple emails coming from different users.&#x20;

Below is a **javascript** example for creating custom subject. For react, [check this example](../../how-to-guides/js-frameworks/react-js/react-js.md).&#x20;

<pre class="language-javascript"><code class="lang-javascript">const form = document.getElementById('form');
const result = document.getElementById('result');

form.addEventListener('submit', function(e) {
    e.preventDefault();
    
    const formData = new FormData(form);
    
    // Get the name input value
<strong>    const name = formData.get('name');
</strong>    
    // Create a custom subject
<strong>    const subject = `${name} sent a message from website`;
</strong>    
    // Append the custom subject to the form data
    formData.append('subject', subject);
    
    const object = Object.fromEntries(formData);
    const json = JSON.stringify(object);
    
    result.innerHTML = "Please wait...";

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
</code></pre>

