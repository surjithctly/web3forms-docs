
<form action="https://api.web3forms.com/submit" method="POST">
  <!-- Your Web3Forms access key -->
  <input type="hidden" name="access_key" value="afb19210-d804-4437-a687-82245d69fa41">

  <!-- Optional branding -->
  <input type="hidden" name="from_name" value="Elijohnology Technician Website">

  <input type="text" name="name" placeholder="Your Name" required>
  <input type="email" name="email" placeholder="Your Email" required>
  <textarea name="message" placeholder="Your Message" required></textarea>

  <button type="submit">Send Message</button>
</form>

<!-- Message display area -->
<p id="result"></p>

<script>
  const form = document.querySelector("form");
  const result = document.getElementById("result");

  form.addEventListener("submit", async (e) => {
    e.preventDefault();
    const formData = new FormData(form);
    const response = await fetch(form.action, {
      method: form.method,
      body: formData
    });

    if (response.ok) {
      result.innerHTML = "✅ Message sent successfully!";
      form.reset();
    } else {
      result.innerHTML = "❌ Failed to send message. Please try again.";
    }
  });
</script>
