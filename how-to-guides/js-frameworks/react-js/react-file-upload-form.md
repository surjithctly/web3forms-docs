# React File Upload Form

File uploading is one of the major features of Web3Forms. Integrating it with React is tricky. Using the following example, you can copy-paste a fully-working React File upload form.&#x20;

If you are using React Hook form, Please [see this guide](react-hook-form-file-upload.md).&#x20;

{% hint style="warning" %}
Note: File Upload is only available for PRO users.&#x20;
{% endhint %}

### Live Demo

{% embed url="https://codesandbox.io/s/react-file-upload-form-o4deqz?file=/src/App.js" %}
React File Upload Form
{% endembed %}

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
        <input type="file" name="attachment" />
        <input type="submit" />
      </form>
      <span>{result}</span>
    </div>
  );
}

export default App;
```
