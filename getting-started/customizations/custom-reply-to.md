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

<pre class="language-markup"><code class="lang-markup"><strong>&#x3C;!-- // Default Form. Here, `email` is used as `replyto` -->
</strong>
&#x3C;form action="https://api.web3forms.com/submit" method="POST">
    &#x3C;input type="hidden" name="access_key" value="YOUR_ACCESS_KEY_HERE">
    &#x3C;input type="text" name="name" required>
    &#x3C;!-- replyto set by this input. usually, it's the user who submits the form.  -->
    &#x3C;input type="email" name="email" required>
    &#x3C;button type="submit">Submit Form&#x3C;/button>
&#x3C;/form>


&#x3C;!-- // Custom `replyto` Form -->

&#x3C;form action="https://api.web3forms.com/submit" method="POST">
    &#x3C;input type="hidden" name="access_key" value="YOUR_ACCESS_KEY_HERE">
    &#x3C;!-- `replyto` email will be the given value.  -->
    &#x3C;input type="hidden" name="replyto" value="custom@gmail.com" />
    &#x3C;input type="text" name="name" required>
    &#x3C;input type="email" name="email" required>
    &#x3C;button type="submit">Submit Form&#x3C;/button>
&#x3C;/form>

</code></pre>
