# Javascript Form Validation

[Check it out on Codepen](https://codepen.io/surjithctly/pen/LYxNPEm)

## HTML

```markup
<!-- 
    =======================================================================

    This is a working contact form. To receive email, 
    Replace YOUR_ACCESS_KEY_HERE with your actual Access Key.

    Create Access Key here 👉 https://web3forms.com/

    =======================================================================
 -->

<div class="flex items-center min-h-screen bg-gray-100 dark:bg-gray-900">
  <div class="container mx-auto">
    <div class="max-w-xl mx-auto my-10 bg-white p-5 rounded-md shadow-sm">
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
        <form
          action="https://api.web3forms.com/submit"
          method="POST"
          id="form"
          class="needs-validation"
          novalidate
        >
          <input type="hidden" name="apikey" value="YOUR_ACCESS_KEY_HERE" />
          <input
            type="hidden"
            name="subject"
            value="New Submission from Web3Forms"
          />
          <input type="checkbox" name="botcheck" id="" style="display: none;" />

          <div class="flex mb-6 space-x-4">
            <div class="w-full md:w-1/2">
              <label
                for="fname"
                class="block mb-2 text-sm text-gray-600 dark:text-gray-400"
                >First Name</label
              >
              <input
                type="text"
                name="name"
                id="first_name"
                placeholder="John"
                required
                class="w-full px-3 py-2 placeholder-gray-300 border-2 border-gray-200 rounded-md focus:outline-none focus:ring focus:ring-indigo-100 focus:border-indigo-300"
              />
              <div
                class="empty-feedback invalid-feedback text-red-400 text-sm mt-1"
              >
                Please provide your first name.
              </div>
            </div>
            <div class="w-full md:w-1/2">
              <label
                for="lname"
                class="block mb-2 text-sm text-gray-600 dark:text-gray-400"
                >Last Name</label
              >
              <input
                type="text"
                name="last_name"
                id="lname"
                placeholder="Doe"
                required
                class="w-full px-3 py-2 placeholder-gray-300 border-2 border-gray-200 rounded-md focus:outline-none focus:ring focus:ring-indigo-100 focus:border-indigo-300"
              />
              <div
                class="empty-feedback invalid-feedback text-red-400 text-sm mt-1"
              >
                Please provide your last name.
              </div>
            </div>
          </div>

          <div class="flex mb-6 space-x-4">
            <div class="w-full md:w-1/2">
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
                class="w-full px-3 py-2 placeholder-gray-300 border-2 border-gray-200 rounded-md focus:outline-none focus:ring focus:ring-indigo-100 focus:border-indigo-300"
              />
              <div class="empty-feedback text-red-400 text-sm mt-1">
                Please provide your email address.
              </div>
              <div class="invalid-feedback text-red-400 text-sm mt-1">
                Please provide a valid email address.
              </div>
            </div>

            <div class="w-full md:w-1/2">
              <label
                for="phone"
                class="block text-sm mb-2 text-gray-600 dark:text-gray-400"
                >Phone Number</label
              >
              <input
                type="text"
                name="phone"
                id="phone"
                placeholder="+1 (555) 1234-567"
                required
                class="w-full px-3 py-2 placeholder-gray-300 border-2 border-gray-200 rounded-md focus:outline-none focus:ring focus:ring-indigo-100 focus:border-indigo-300"
              />

              <div
                class="empty-feedback invalid-feedback text-red-400 text-sm mt-1"
              >
                Please provide your phone number.
              </div>
            </div>
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
              class="w-full px-3 py-2 placeholder-gray-300 border-2 border-gray-200 rounded-md focus:outline-none focus:ring focus:ring-indigo-100 focus:border-indigo-300"
              required
            ></textarea>
            <div
              class="empty-feedback invalid-feedback text-red-400 text-sm mt-1"
            >
              Please enter your message.
            </div>
          </div>
          <div class="mb-6">
            <button
              type="submit"
              class="w-full px-3 py-4 text-white bg-indigo-500 rounded-md focus:bg-indigo-600 focus:outline-none"
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

## CSS

```css
.invalid-feedback,
.empty-feedback {
  display: none;
}

.was-validated :placeholder-shown:invalid ~ .empty-feedback {
  display: block;
}

.was-validated :not(:placeholder-shown):invalid ~ .invalid-feedback {
  display: block;
}

.is-invalid,
.was-validated :invalid {
  border-color: #dc3545;
}
```

## Javascript

```javascript
(function () {
  "use strict";
  /*
   * Form Validation
   */

  // Fetch all the forms we want to apply custom validation styles to
  const forms = document.querySelectorAll(".needs-validation");
  const result = document.getElementById("result");
  // Loop over them and prevent submission
  Array.prototype.slice.call(forms).forEach(function (form) {
    form.addEventListener(
      "submit",
      function (event) {
        if (!form.checkValidity()) {
          event.preventDefault();
          event.stopPropagation();

          form.querySelectorAll(":invalid")[0].focus();
        } else {
          /*
           * Form Submission using fetch()
           */

          const formData = new FormData(form);
          event.preventDefault();
          event.stopPropagation();
          const object = {};
          formData.forEach((value, key) => {
            object[key] = value;
          });
          const json = JSON.stringify(object);
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
              form.classList.remove("was-validated");
              setTimeout(() => {
                result.style.display = "none";
              }, 5000);
            });
        }
        form.classList.add("was-validated");
      },
      false
    );
  });
})();
```

