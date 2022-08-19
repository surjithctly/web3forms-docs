# React Hook Form File Upload

File uploading is one of the major features of Web3Forms. Integrating it with React is tricky. Using the following example, you can copy-paste a fully-working React File upload form.&#x20;

If you are NOT using React Hook form, Please [see this guide](react-file-upload-form.md).&#x20;

{% hint style="warning" %}
Note: File Upload is only available for PRO users.&#x20;
{% endhint %}

### Live Demo

{% embed url="https://codesandbox.io/s/react-hook-form-file-upload-km3bsh?file=/src/App.js" %}
React Hook Form File Upload
{% endembed %}

Here's the code:

```jsx
import React from "react";
import { useForm } from "react-hook-form";

function App() {
  const { register, handleSubmit } = useForm();
  const [result, setResult] = React.useState("");

  const onSubmit = async (data) => {
    console.log(data);

    setResult("Sending....");
    const formData = new FormData();

    formData.append("access_key", "YOUR_ACCESS_KEY_HERE");

    for (const key in data) {
      if (key === "file") {
        formData.append(key, data[key][0]);
      } else {
        formData.append(key, data[key]);
      }
    }

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
      <h1>React Hook Form File Upload</h1>
      <form onSubmit={handleSubmit(onSubmit)}>
        <input type="text" placeholder="Name" {...register("name")} />
        <br />
        <br />
        <input type="email" placeholder="Email" {...register("email")} />
        <br />
        <br />
        <input type="file" {...register("file")} />
        <br />
        <br />
        <input type="submit" />
      </form>
      <br />
      <span>{result}</span>
    </div>
  );
}

export default App;

```
