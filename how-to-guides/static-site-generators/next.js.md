# Next.js
---
description: Simple example using in Next.js
---

This is a simple example of the easiest way the tool could be used in a Next.js project

```jsx
export function Contact() {
  async function handleSubmit(e) {
    e.preventDefault();
    const response = await fetch("https://api.web3forms.com/submit", {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
        Accept: "application/json",
      },
      body: JSON.stringify({
        apikey: "YOUR_ACCESS_KEY_HERE",
        name: e.target.name.value,
        email: e.target.email.value,
        message: e.target.message.value,
      }),
    });
    const result = await response.json();
    if (result.success) {
      console.log(result);
    }
  }

  return (
    <div>
      <div>
        <div>
          <div>
            <h1>CONTACT</h1>
          </div>

          <form onSubmit={handleSubmit}>
            <div>
              <label htmlFor="">NAME</label>
              <input
                type="text"
                name="name"
                required
                placeholder="What is your name"
              />
            </div>
            <div>
              <label htmlFor="">E-MAIL</label>
              <input
                type="email"
                name="email"
                required
                placeholder="Ex. name@email.com"
              />
            </div>
            <div>
              <label htmlFor="">MESSAGE</label>
              <textarea
                name="message"
                required
                rows="3"
                placeholder="Write your message here"
              ></textarea>
            </div>
            <button type="submit">SEND</button>
          </form>
        </div>
      </div>
    </div>
  );
}
```

