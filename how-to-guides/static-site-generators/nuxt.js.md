---
description: Create a working contact form in nuxt 3 using web3forms.
---

# Nuxt.js

Here's a simple Contact form Example Code for Nuxt 3 with Web3Forms

```markup
<template>
  <form @submit.prevent="submitForm">
    <input type="text" name="name" v-model="form.name" />
    <input type="email" name="email" v-model="form.email" />
    <textarea name="message" v-model="form.message"></textarea>
    <button type="submit">Send Message</button>
  </form>
</template>

<script setup>
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
  try {
    status.value = "loading";
    const response = await $fetch("https://api.web3forms.com/submit", {
      method: "POST",
      body: form.value,
    });
    console.log(response);
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



## Nuxt UI

Here's another example if you are using Nuxt UI

```html
<template>
  <UForm :schema="schema" :state="state" class="space-y-4" @submit="onSubmit">
    <UFormGroup label="Name" name="name">
      <UInput v-model="state.name" />
    </UFormGroup>

    <UFormGroup label="Email" name="email">
      <UInput v-model="state.email" />
    </UFormGroup>

    <UFormGroup label="Message" name="message">
      <UTextarea v-model="state.message" type="text" />
    </UFormGroup>

    <UButton type="submit"> Submit </UButton>
  </UForm>
</template>

<script setup>
import { z } from "zod";

const schema = z.object({
  name: z.string().min(2, "Must be at least 2 characters"),
  email: z.string().email("Invalid email address"),
  message: z.string().min(10, "Must be at least 10 characters"),
  subject: z.string().min("Subject required"),
  access_key: z.string().min("Access key is required"),
});

const state = reactive({
  access_key: "YOUR_ACCESS_KEY_HERE",
  subject: "New Submission from Web3Forms",
  name: "",
  email: "",
  message: "",
});

async function onSubmit(event) {
  result.value = "Please wait...";
  try {
    const response = await $fetch("https://api.web3forms.com/submit", {
      method: "POST",
      headers: { "Content-Type": "application/json" },
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
}
</script>
```
