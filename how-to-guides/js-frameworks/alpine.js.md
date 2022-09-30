# Alpine.js

Here's a simple Alpine.js Contact Form Code example with Web3Forms

```markup
<form x-data="contactForm()" @submit.prevent="submit">
    <input type="hidden" name="access_key" value="YOUR_ACCESS_KEY_HERE">
    <input type="text" name="name" required />
    <input type="email" name="email" required />
    <textarea name="message" required rows="3"></textarea>
    <button type="submit" :disabled="loading">Submit</button>
    <div x-text="status"></div>
</form>

<script>
function contactForm() {
  return {
    buttonText: "Submit",
    loading: false,
    status: "",
    async submit(event) {
      const formData = new FormData(event.target);
      const object = Object.fromEntries(formData);
      const json = JSON.stringify(object);

      this.status = "Submitting...";
      this.loading = true;

      const response = await fetch("https://api.web3forms.com/submit", {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
          Accept: "application/json"
        },
        body: json
      });
      const result = await response.json();
      if (result.success) {
        console.log(result);
        this.status = result.message || "Success";
      }
      this.loading = false;
    }
  };
}
</script>
```
