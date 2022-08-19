# Simple React Contact Form

In this guide, you will learn how to setup a simple working contact form using React Framework and Web3Forms. No need to setup an SMTP or Custom Backend or Server. It all happens in the front end.  You can copy paste to your react app and it will work.&#x20;

Here's the code:

```jsx
import React from "react";

function App() {
  const [result, setResult] = React.useState("");

  const onSubmit = async (event) => {
    event.preventDefault();
    setResult("Sending....");
    const formData = new FormData(event.target);

    formData.append("access_key", "YOUR_ACCESS_KEY_HERE");

    const res = await fetch("https://api.web3forms.com/submit", {
      method: "POST",
      body: formData
    }).then((res) => res.json());

    if (res.success) {
      console.log("Success", res);
      setResult(res.message);
    } else {
      console.log("Error", res);
      setResult(res.message);
    }
  };

  return (
    <div className="App">
      <h1>React File Upload Form</h1>
      <form onSubmit={onSubmit}>
        <input type="text" name="name"/>
        <input type="email" name="email"/>
        <textarea name="message"></textarea>
        <input type="submit" />
      </form>
      <span>{result}</span>
    </div>
  );
}

export default App;
```
