---
description: Create a working contact form in nuxt 3 using web3forms.
---

# Nuxt.js

Here's a simple Contact form Example Code for Nuxt 3 with Web3Forms

```markup
<template>
  <form @submit.prevent="submitForm">
    <input type="text" name="name" v-model="form.name"/>
    <input type="email" name="email"  v-model="form.email"/>
    <textarea name="message" v-model="form.message"></textarea>
    <button type="submit">Send Message</button>
  </form>
</template>


<script setup>
import { ref } from 'vue';

const form = ref({
  access_key: "YOUR_ACCESS_KEY_HERE",
  subject: "New Submission from Web3Forms",
  name: "",
  email: "",
  message: "",

});

const result = ref("");
const status = ref("");

const submitForm = async () => {
  result.value = "Please wait...";
  try {
    const response = await $fetch('https://api.web3forms.com/submit', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: form.value,
    });

    console.log(response); // You can remove this line if you don't need it
    
    result.value = response.message;

    if (response.status === 200) {
      status.value = "success";
    } else {
      console.log(response); // Log for debugging, can be removed
      status.value = "error";
    }
  } catch (error) {
    console.log(error); // Log for debugging, can be removed
    status.value = "error";
    result.value = "Something went wrong!";
  } finally {
    // Reset form after submission
    form.value.name = "";
    form.value.email = "";
    form.value.message = "";

    // Clear result and status after 5 seconds
    setTimeout(() => {
      result.value = "";
      status.value = "";
    }, 5000);
  }
};
</script>
```
