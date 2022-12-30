---
description: Set a custom reply-to email for your submission.
---

# Custom Reply-To

By default, we take `email` as the `replyto` address. So if your form has an `email` input, you don't need to configure anything. In the submission you receive, you can see the reply to email.&#x20;

However, If you want to add a custom `replyto` email address, you can use the following code.&#x20;

```markup
<input type="hidden" name="replyto" value="custom@gmail.com" />
```

**Here's an example with full code:**

```markup
<!-- // Default Form. Here, `email` is used as `replyto` -->

<form action="https://api.web3forms.com/submit" method="POST">
    <input type="hidden" name="access_key" value="YOUR_ACCESS_KEY_HERE">
    <input type="text" name="name" required>
    <!-- replyto set by this input. usually, it's the user who submits the form.  -->
    <input type="email" name="email" required>
    <button type="submit">Submit Form</button>
</form>


<!-- // Custom `replyto` Form -->

<form action="https://api.web3forms.com/submit" method="POST">
    <input type="hidden" name="access_key" value="YOUR_ACCESS_KEY_HERE">
    <!-- `replyto` email will be the given value.  -->
    <input type="hidden" name="replyto" value="custom@gmail.com" />
    <input type="text" name="name" required>
    <input type="email" name="email" required>
    <button type="submit">Submit Form</button>
</form>

```
