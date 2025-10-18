<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>D.I.Y + AI Startup Hub</title>
  <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
  <style>
    body::before {
      content: '';
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: radial-gradient(circle at center, rgba(128,0,255,0.15) 0%, transparent 70%),
                  repeating-linear-gradient(45deg, rgba(255,165,0,0.05) 0, rgba(255,165,0,0.05) 2px, transparent 2px, transparent 20px),
                  repeating-linear-gradient(-45deg, rgba(255,140,0,0.05) 0, rgba(255,140,0,0.05) 2px, transparent 2px, transparent 20px);
      animation: pulseGlow 8s infinite alternate;
      z-index: -1;
    }

    @keyframes pulseGlow {
      0% { opacity: 0.6; filter: hue-rotate(0deg) brightness(1); }
      100% { opacity: 0.9; filter: hue-rotate(45deg) brightness(1.2); }
    }
  </style>
</head>
<body class="bg-black text-gray-200 flex flex-col items-center justify-center min-h-screen">
  <main class="text-center max-w-lg px-6">
    <h1 class="text-4xl font-bold text-purple-400 mb-4">Welcome to D.I.Y + AI Startup Hub</h1>
    <p class="text-gray-400 mb-6">A community for innovators, hackers, and builders who love to merge do-it-yourself energy with cutting-edge AI creativity — inspired by the spirit of Instructables and the precision of cyber engineering.</p>

    <form id="subscribe-form" class="flex flex-col sm:flex-row gap-3 justify-center">
      <input type="email" id="email" name="email" required placeholder="Enter your email" class="px-4 py-2 w-full sm:w-72 bg-gray-800 border border-gray-700 rounded focus:outline-none focus:ring-2 focus:ring-purple-500">
      <button type="submit" class="bg-yellow-400 hover:bg-yellow-300 text-black font-bold px-6 py-2 rounded transition">Join the Workshop</button>
    </form>

    <p id="message" class="text-sm text-gray-500 mt-4 hidden"></p>

    <div class="mt-8 text-xs text-gray-600">
      <p>No spam. Just blueprints, code, and inspiration for your next creation.</p>
    </div>
  </main>

  <section class="max-w-md mx-auto p-6 mt-16 bg-gray-900 bg-opacity-70 rounded-lg shadow-lg">
    <h2 class="text-3xl font-bold text-yellow-400 mb-6 text-center">Contact Us</h2>
    <form id="contact-form" class="space-y-4">
      <div>
        <label for="name" class="block text-sm font-medium mb-2 text-purple-300">Name</label>
        <input type="text" id="name" name="name" required class="w-full px-3 py-2 bg-gray-800 border border-gray-700 rounded-md focus:outline-none focus:ring-2 focus:ring-purple-500">
      </div>

      <div>
        <label for="email" class="block text-sm font-medium mb-2 text-purple-300">Email</label>
        <input type="email" id="contactEmail" name="email" required class="w-full px-3 py-2 bg-gray-800 border border-gray-700 rounded-md focus:outline-none focus:ring-2 focus:ring-purple-500">
      </div>

      <div>
        <label for="message" class="block text-sm font-medium mb-2 text-purple-300">Message</label>
        <textarea id="messageInput" name="message" rows="5" required class="w-full px-3 py-2 bg-gray-800 border border-gray-700 rounded-md focus:outline-none focus:ring-2 focus:ring-purple-500"></textarea>
      </div>

      <button type="submit" id="sendBtn" class="w-full bg-yellow-400 hover:bg-yellow-300 text-black py-2 px-4 rounded-md font-bold transition">Send Message</button>
    </form>
  </section>

  <script>
    const form = document.getElementById('subscribe-form');
    const message = document.getElementById('message');
    const contactForm = document.getElementById('contact-form');
    const sendBtn = document.getElementById('sendBtn');

    form.addEventListener('submit', async (e) => {
      e.preventDefault();
      const email = document.getElementById('email').value;
      
      try {
        const response = await fetch('https://api.web3forms.com/submit', {
          method: 'POST',
          headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify({
            access_key: 'YOUR_ACCESS_KEY_HERE',
            email: email,
            subject: 'New D.I.Y + AI Hub Subscriber'
          })
        });

        if (response.ok) {
          message.textContent = '✅ Welcome to the lab. Your next project starts here.';
          message.classList.remove('hidden');
          message.classList.add('text-yellow-400');
          form.reset();
        } else {
          throw new Error('Network error');
        }
      } catch (err) {
        message.textContent = '⚠️ Something went wrong. Try again later.';
        message.classList.remove('hidden');
        message.classList.add('text-red-400');
      }
    });

    contactForm.addEventListener('submit', async (event) => {
      event.preventDefault();
      sendBtn.disabled = true;
      sendBtn.textContent = 'Sending...';

      const name = document.getElementById('name').value;
      const email = document.getElementById('contactEmail').value;
      const messageInput = document.getElementById('messageInput').value;

      try {
        const response = await fetch('https://api.web3forms.com/submit', {
          method: 'POST',
          headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify({
            access_key: 'YOUR_ACCESS_KEY_HERE',
            name: name,
            email: email,
            message: messageInput
          })
        });

        const result = await response.json();
        if (result.success) {
          alert('Message sent successfully!');
          contactForm.reset();
        } else {
          alert('Failed to send message. Please try again.');
        }
      } catch (error) {
        alert('An error occurred. Please try again.');
      } finally {
        sendBtn.disabled = false;
        sendBtn.textContent = 'Send Message';
      }
    });
  </script>
</body>
</html>
