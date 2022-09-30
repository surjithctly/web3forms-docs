# Nuxt.js

## Requirements

The following example uses [@nuxtjs/axios](https://axios.nuxtjs.org/setup) and [@nuxtjs/tailwindcss](https://tailwindcss.nuxtjs.org/setup) (optional) to make it work.

## Vue file

```markup
<template>
  <!-- 
    =======================================================================

    This is a working contact form. To receive email, 
    Replace YOUR_ACCESS_KEY_HERE with your actual Access Key.

    Create Access Key here 👉 https://web3forms.com/

    =======================================================================
 -->

  <div class="flex items-center min-h-screen bg-gray-50 dark:bg-gray-900">
    <div class="container mx-auto">
      <div class="max-w-md mx-auto my-10 bg-white p-5 rounded-md shadow-sm">
        <div class="text-center">
          <h1
            class="my-3 text-3xl font-semibold text-gray-700 dark:text-gray-200"
          >
            Contact Us
          </h1>
          <p class="text-gray-400 dark:text-gray-400">
            Fill up the form below to send us a message.
          </p>
        </div>
        <div class="m-7">
          <form @submit.prevent="submitForm">
            <input
              type="checkbox"
              name="botcheck"
              id=""
              style="display: none"
            />
            <div class="mb-6">
              <label
                for="name"
                class="block mb-2 text-sm text-gray-600 dark:text-gray-400"
                >Full Name</label
              >
              <input
                type="text"
                name="name"
                id="name"
                placeholder="John Doe"
                required
                v-model="form.name"
                class="w-full px-3 py-2 placeholder-gray-300 border border-gray-300 rounded-md focus:outline-none focus:ring focus:ring-indigo-100 focus:border-indigo-300 dark:bg-gray-700 dark:text-white dark:placeholder-gray-500 dark:border-gray-600 dark:focus:ring-gray-900 dark:focus:border-gray-500"
              />
            </div>
            <div class="mb-6">
              <label
                for="email"
                class="block mb-2 text-sm text-gray-600 dark:text-gray-400"
                >Email Address</label
              >
              <input
                type="email"
                name="email"
                id="email"
                placeholder="you@company.com"
                required
                v-model="form.email"
                class="w-full px-3 py-2 placeholder-gray-300 border border-gray-300 rounded-md focus:outline-none focus:ring focus:ring-indigo-100 focus:border-indigo-300 dark:bg-gray-700 dark:text-white dark:placeholder-gray-500 dark:border-gray-600 dark:focus:ring-gray-900 dark:focus:border-gray-500"
              />
            </div>
            <div class="mb-6">
              <label
                for="phone"
                class="text-sm text-gray-600 dark:text-gray-400"
                >Phone Number</label
              >
              <input
                type="text"
                name="phone"
                id="phone"
                placeholder="+1 (555) 1234-567"
                required
                v-model="form.phone"
                class="w-full px-3 py-2 placeholder-gray-300 border border-gray-300 rounded-md focus:outline-none focus:ring focus:ring-indigo-100 focus:border-indigo-300 dark:bg-gray-700 dark:text-white dark:placeholder-gray-500 dark:border-gray-600 dark:focus:ring-gray-900 dark:focus:border-gray-500"
              />
            </div>
            <div class="mb-6">
              <label
                for="message"
                class="block mb-2 text-sm text-gray-600 dark:text-gray-400"
                >Your Message</label
              >

              <textarea
                rows="5"
                name="message"
                id="message"
                placeholder="Your Message"
                v-model="form.message"
                class="w-full px-3 py-2 placeholder-gray-300 border border-gray-300 rounded-md focus:outline-none focus:ring focus:ring-indigo-100 focus:border-indigo-300 dark:bg-gray-700 dark:text-white dark:placeholder-gray-500 dark:border-gray-600 dark:focus:ring-gray-900 dark:focus:border-gray-500"
                required
              ></textarea>
            </div>
            <div class="mb-6">
              <button
                type="submit"
                class="w-full px-3 py-4 text-white bg-indigo-500 rounded-md focus:bg-indigo-600 focus:outline-none"
              >
                Send Message
              </button>
            </div>
            <p
              :class="`text-base text-center 

              ${status === 'success' ? 'text-green-500' : ''}
               ${status === 'error' ? 'text-red-500' : ''}
               ${status === '' ? 'text-gray-4500' : ''}
               `"
            >
              {{ result }}
            </p>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      form: {
        access_key: "YOUR_ACCESS_KEY_HERE",
        subject: "New Submission from Web3Forms",

        name: "",
        email: "",
        phone: "",
        message: "",
      },
      result: "",
      status: "",
    };
  },
  methods: {
    async submitForm(e) {
      this.result = "Please wait...";
      axios.create({
        headers: { "Content-Type": "application/json" },
      });
      await axios
        .post("https://api.web3forms.com/submit", this.form)
        .then(async (response) => {
          //let json = await response.json();
          //this.result = json.message;
          console.log(response);
          this.result = response.data.message;

          if (response.status === 200) {
            this.status = "success";
          } else {
            console.log(response);
            this.status = "error";
          }
        })
        .catch((error) => {
          console.log(error);
          this.status = "error";
          this.result = "Something went wrong!";
        })
        .then(() => {
          const form = this.form;
          form.name = "";
          form.email = "";
          form.phone = "";
          form.message = "";

          setTimeout(() => {
            this.result = "";
            this.status = "";
          }, 5000);
        });
    },
  },
};
</script>
```
