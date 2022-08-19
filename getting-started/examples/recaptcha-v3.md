# Google reCaptcha v3

HTML (Styled using TailwindCSS)

```html
<div class="flex items-center min-h-screen bg-gray-100 dark:bg-gray-900">
  <div class="container mx-auto">
    <div class="max-w-md mx-auto my-10 bg-white p-5 rounded-md shadow-sm">
      <div class="text-center">
        <h1 class="my-3 text-3xl font-semibold text-gray-700 dark:text-gray-200">
          Contact Us
        </h1>
        <p class="text-gray-400 dark:text-gray-400">
          Fill up the form below to send us a message.
        </p>
      </div>
      <div class="m-7">
        <form action="https://api.web3forms.com/submit" method="POST" id="form">
          <input type="hidden" name="access_key" value="YOUR_ACCESS_KEY_HERE" />
          <input type="hidden" name="subject" value="New Submission from Web3Forms" />
          <input type="checkbox" name="botcheck" id="" style="display: none;" />
          <!-- Google reCaptcha v3: To Prevent SPAM Submission.PRO Plan only -->
          <input type="hidden" name="recaptcha_response" id="recaptchaResponse">

          <div class="mb-6">
            <label for="name" class="block mb-2 text-sm text-gray-600 dark:text-gray-400">Full Name</label>
            <input type="text" name="name" id="name" placeholder="John Doe" required class="w-full px-3 py-2 placeholder-gray-300 border border-gray-300 rounded-md focus:outline-none focus:ring focus:ring-indigo-100 focus:border-indigo-300 dark:bg-gray-700 dark:text-white dark:placeholder-gray-500 dark:border-gray-600 dark:focus:ring-gray-900 dark:focus:border-gray-500" />
          </div>
          <div class="mb-6">
            <label for="email" class="block mb-2 text-sm text-gray-600 dark:text-gray-400">Email Address</label>
            <input type="email" name="email" id="email" placeholder="you@company.com" required class="w-full px-3 py-2 placeholder-gray-300 border border-gray-300 rounded-md focus:outline-none focus:ring focus:ring-indigo-100 focus:border-indigo-300 dark:bg-gray-700 dark:text-white dark:placeholder-gray-500 dark:border-gray-600 dark:focus:ring-gray-900 dark:focus:border-gray-500" />
          </div>
          <div class="mb-6">
            <label for="phone" class="text-sm text-gray-600 dark:text-gray-400">Phone Number</label>
            <input type="text" name="phone" id="phone" placeholder="+1 (555) 1234-567" required class="w-full px-3 py-2 placeholder-gray-300 border border-gray-300 rounded-md focus:outline-none focus:ring focus:ring-indigo-100 focus:border-indigo-300 dark:bg-gray-700 dark:text-white dark:placeholder-gray-500 dark:border-gray-600 dark:focus:ring-gray-900 dark:focus:border-gray-500" />
          </div>
          <div class="mb-6">
            <label for="message" class="block mb-2 text-sm text-gray-600 dark:text-gray-400">Your Message</label>

            <textarea rows="5" name="message" id="message" placeholder="Your Message" class="w-full px-3 py-2 placeholder-gray-300 border border-gray-300 rounded-md focus:outline-none focus:ring focus:ring-indigo-100 focus:border-indigo-300 dark:bg-gray-700 dark:text-white dark:placeholder-gray-500 dark:border-gray-600 dark:focus:ring-gray-900 dark:focus:border-gray-500" required></textarea>
          </div>
          <div class="mb-6">
            <button type="submit" class="w-full px-3 py-4 text-white bg-indigo-500 rounded-md focus:bg-indigo-600 focus:outline-none">
              Send Message
            </button>
          </div>
          <p class="text-base text-center text-gray-400" id="result"></p>
        </form>
      </div>
    </div>
  </div>
</div>

<!-- Needed for Recaptcha -->

<script src="https://www.google.com/recaptcha/api.js?render=YOUR_PUBLIC_KEY_HERE"></script>
<script>
  grecaptcha.ready(function() {
    grecaptcha.execute('YOUR_PUBLIC_KEY_HERE', {
      action: 'contact'
    }).then(function(token) {
      recaptchaResponse.value = token;
    });
  });
</script>
```

Javascript

```javascript
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
      Accept: "application/json"
    },
    body: json
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
