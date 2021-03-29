# Contact Form with Dark Mode

[Check it out on Codepen](https://codepen.io/surjithctly/pen/MWJygKb)

## HTML

```html
<!-- 
    =======================================================================

    This is a working contact form. To receive email, 
    Replace YOUR_ACCESS_KEY_HERE with your actual Access Key.

    Create Access Key here 👉 https://web3forms.com/

    =======================================================================
 -->

<div class="flex items-center min-h-screen bg-gray-900">
  <div class="container mx-auto">
    <div class="max-w-md mx-auto my-10 bg-gray-800 p-5 rounded-md shadow-sm">
      <div class="text-center">
        <h1 class="my-3 text-3xl font-semibold text-gray-100">Contact Us</h1>
        <p class="text-gray-400 dark:text-gray-400">
          Fill up the form below to send us a message.
        </p>
      </div>
      <div class="m-7">
        <form action="https://api.web3forms.com/submit" method="POST" id="form">
          <input type="hidden" name="apikey" value="YOUR_ACCESS_KEY_HERE" />
          <input
            type="hidden"
            name="subject"
            value="New Submission from Web3Forms"
          />
          <input type="checkbox" name="botcheck" id="" style="display: none;" />

          <div class="mb-6">
            <label for="name" class="block mb-2 text-sm text-gray-400"
              >Full Name</label
            >
            <input
              type="text"
              name="name"
              id="name"
              placeholder="John Doe"
              required
              class="w-full px-3 py-2 h-12 rounded-sm placeholder-gray-500 text-gray-900 bg-gray-100 text-sm focus:outline-none"
            />
          </div>
          <div class="mb-6">
            <label for="email" class="block mb-2 text-sm text-gray-400"
              >Email Address</label
            >
            <input
              type="email"
              name="email"
              id="email"
              placeholder="you@company.com"
              required
              class="w-full px-3 py-2 h-12 rounded-sm placeholder-gray-500 text-gray-900 bg-gray-100 text-sm focus:outline-none"
            />
          </div>
          <div class="mb-6">
            <label for="phone" class="block mb-2 text-sm text-gray-400"
              >Phone Number</label
            >
            <input
              type="text"
              name="phone"
              id="phone"
              placeholder="+1 (555) 1234-567"
              required
              class="w-full px-3 py-2 h-12 rounded-sm placeholder-gray-500 text-gray-900 bg-gray-100 text-sm focus:outline-none"
            />
          </div>
          <div class="mb-6">
            <label for="message" class="block mb-2 text-sm text-gray-400"
              >Your Message</label
            >

            <textarea
              rows="5"
              name="message"
              id="message"
              placeholder="Your Message"
              class="w-full px-3 py-2 rounded-sm placeholder-gray-500 text-gray-900 bg-gray-100 text-sm focus:outline-none"
              required
            ></textarea>
          </div>
          <div class="mb-6">
            <button
              type="submit"
              class="w-full bg-indigo-600 inline-block text-white no-underline hover:text-indigo-100 py-4 px-4 rounded-sm focus:outline-none"
            >
              Send Message
            </button>
          </div>
          <p class="text-base text-center text-gray-400" id="result"></p>
        </form>
      </div>
    </div>
  </div>
</div>
```

## Javascript

```js
const form = document.getElementById("form");
const result = document.getElementById("result");

form.addEventListener("submit", function (e) {
  const formData = new FormData(form);
  e.preventDefault();
  var object = {};
  formData.forEach((value, key) => {
    object[key] = value;
  });
  var json = JSON.stringify(object);
  result.innerHTML = "Please wait...";

  fetch("https://api.web3forms.com/submit", {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
      Accept: "application/json",
    },
    body: json,
  })
    .then(async (response) => {
      let json = await response.json();
      if (response.status == 200) {
        result.innerHTML = json.message;
        result.classList.remove("text-gray-500");
        result.classList.add("text-green-500");
      } else {
        console.log(response);
        result.innerHTML = json.message;
        result.classList.remove("text-gray-500");
        result.classList.add("text-red-500");
      }
    })
    .catch((error) => {
      console.log(error);
      result.innerHTML = "Something went wrong!";
    })
    .then(function () {
      form.reset();
      setTimeout(() => {
        result.style.display = "none";
      }, 5000);
    });
});
```
