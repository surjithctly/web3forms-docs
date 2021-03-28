# Raw Contact Form (No CSS)

[Check it out on Codepen](https://codepen.io/surjithctly/pen/WNRwwdx)

## HTML

```html
<!-- 
    =======================================================================

    This is a working contact form. To receive email, 
    Replace YOUR_ACCESS_KEY_HERE with your actual Access Key.

    Create Access Key here 👉 https://web3forms.com/

    =======================================================================
 -->

<form action="https://api.web3forms.com/submit" method="POST" id="form">
  <fieldset>
    <legend>Contact Form</legend>
    <input type="hidden" name="apikey" value="YOUR_ACCESS_KEY_HERE" />
    <input type="hidden" name="subject" value="New Submission from Web3Forms" />
    <input
      type="hidden"
      name="redirect"
      value="https://web3forms.com/success"
    />
    <input type="checkbox" name="botcheck" id="" style="display: none;" />
    <div>
      <label for="name">Full Name</label><br />
      <input
        type="text"
        name="name"
        id="name"
        placeholder="John Doe"
        required
      />
      <br /><br />
    </div>
    <div>
      <label for="email">Email Address</label><br />
      <input
        type="email"
        name="email"
        id="email"
        placeholder="you@company.com"
        required
      /><br /><br />
    </div>
    <div>
      <label for="phone">Phone Number</label>
      <br />
      <input
        type="text"
        name="phone"
        id="phone"
        placeholder="+1 (555) 1234-567"
        required
      /><br /><br />
    </div>
    <div>
      <label for="message">Your Message</label>
      <br />
      <textarea
        rows="5"
        name="message"
        id="message"
        placeholder="Your Message"
        required
      ></textarea
      ><br /><br />
    </div>

    <button type="submit">Send Message</button>
  </fieldset>
</form>
```

## CSS

```css
form {
  max-width: 500px;
  margin: 150px auto;
}

fieldset {
  padding: 30px;
}

input,
textarea,
button {
  width: 100%;
}
```
