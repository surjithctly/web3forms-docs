# Vue JS

```html
<script setup lang="ts">
import { ref } from "vue";
const WEB3FORMS_ACCESS_KEY = "YOUR_ACCESS_KEY_HERE";
const name = ref("")
const email = ref("")
const message = ref("")

const submitForm = async () => {
  const response = await fetch("https://api.web3forms.com/submit", {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
      Accept: "application/json",
    },
    body: JSON.stringify({
      access_key: WEB3FORMS_ACCESS_KEY,
      name: name.value,
      email: email.value,
      message: message.value,
    }),
  });
  const result = await response.json();
  if (result.success) {
    console.log(result);
  }
}
</script>
<template>
  <form @submit.prevent="submitForm">
    <input type="text" name="name" v-model="name"/>
    <input type="email" name="email"  v-model="email"/> 
    <textarea name="message" v-model="message"></textarea>
    <button type="submit">Send Message</button>
  </form>
</template>
```
