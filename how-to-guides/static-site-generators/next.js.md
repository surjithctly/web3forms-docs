# Next.js

## Simple example using in Next.js

A simple example of implementing Web3Forms in a Next.js project. You can see an advanced version using [react-hook-form here](https://docs.web3forms.com/how-to-guides/js-frameworks/react-js)

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
                access_key: "YOUR_ACCESS_KEY_HERE",
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
    <>
      <form onSubmit={handleSubmit}>
          <div>
              <label htmlFor="name">Name</label>
              <input type="text" name="name" required placeholder="Your name" />
          </div>
          <div>
              <label htmlFor="email">Email</label>
              <input type="email" name="email" required placeholder="email@example.com" />
          </div>
          <div>
              <label htmlFor="message">Message</label>
              <textarea name="message" required rows="3" placeholder="Enter Message"></textarea>
          </div>
          <button type="submit">Submit Form</button>
      </form>
    </>
  );
}
```

## File Upload Form in Next.js

Here's a simple example code for a file upload contact form in Next.js using React Hook Form.&#x20;

```jsx
import React from "react";
import { useForm } from "react-hook-form";

function App() {
    const { register, handleSubmit } = useForm();

    const onSubmit = async (data) => {
        const formData = new FormData(data);
        
        formData.append("access_key", "YOUR_ACCESS_KEY_HERE");
        formData.append("file", data.file[0]);

        const res = await fetch("https://api.web3forms.com/submit", {
            method: "POST",
            body: formData,
        }).then((res) => res.json());
        
        if (res.success) {
            console.log("Success", res);
        } else {
        console.log("Error", res);
        }
    };

    return (
        <div className="App">
            <form onSubmit={handleSubmit(onSubmit)}>
                <input type="text" name="name" />
                <input type="file" {...register("file")} />

                <input type="submit" />
            </form>
        </div>
    );
}

export default App;
```
