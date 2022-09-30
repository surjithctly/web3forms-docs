# Gatsby

Gatsby Contact Form - Simple Working Example Code with Web3Forms

```jsx
import React from "react";

export default function ContactPage() {
  return (
      <form method="POST" action="https://api.web3forms.com/submit">

        <input type="hidden" name="access_key" value="YOUR_ACCESS_KEY_HERE">

        <input type="text" name="name"/>
        <input type="email" name="email"/>
        <textarea name="message"></textarea>
        <button type="submit">Submit Form</button>
      </form>
  );
}
```
