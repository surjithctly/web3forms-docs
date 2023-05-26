# Gridsome

Here's a simple Contact form Working Example for Gridsome with Web3Forms

```markup
<template>
    <form @submit.prevent="submitForm">
      <input type="text" name="name" v-model="name"/>
      <input type="email" name="email"  v-model="email"/>
      <textarea name="message" v-model="message"></textarea>
      <button type="submit">Send Message</button>
    </form>
  </template>

  <script>
  const WEB3FORMS_ACCESS_KEY = "YOUR_ACCESS_KEY_HERE";

  export default {
    data() {
      return {
        name: "",
        email: "",
        message: "",
      };
    },
    methods: {
      async submitForm() {
        const response = await fetch("https://api.web3forms.com/submit", {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
            Accept: "application/json",
          },
          body: JSON.stringify({
            access_key: WEB3FORMS_ACCESS_KEY,
            name: this.name,
            email: this.email,
            message: this.message,
          }),
        });
        const result = await response.json();
        if (result.success) {
          console.log(result);
        }
      },
    },
  };
  </script>
```
