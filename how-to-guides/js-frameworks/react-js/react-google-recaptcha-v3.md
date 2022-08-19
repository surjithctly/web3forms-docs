---
description: Next.js Example
---

# React Google ReCaptcha v3

In this example, you can see a working google reCaptcha v3 (Invisible captcha) with React Hook Form.

{% hint style="warning" %}
Note: File Upload is only available for PRO users.&#x20;
{% endhint %}

### Live Demo

{% embed url="https://codesandbox.io/s/react-next-js-simple-google-recaptcha-v3-q21ov7?file=/pages/index.tsx" %}
Invisible Google reCaptcha.
{% endembed %}

Here's the code:

```jsx
import React from "react";
import { useForm } from "react-hook-form";
import Script from "next/script";

function App() {
  const { register, handleSubmit, setValue } = useForm();
  const [result, setResult] = React.useState("");
  const [captchatoken, setCaptchaToken] = React.useState("");

  React.useEffect(() => {
    setValue("recaptcha_response", captchatoken);
  });

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
        <input
          type="hidden"
          {...register("recaptcha_response")}
          id="recaptchaResponse"
        />
        <br />
        <input type="submit" />
      </form>
      <br />
      <span>{result}</span>

      <Script
        id="recaptcha-load"
        strategy="lazyOnload"
        src={`https://www.google.com/recaptcha/api.js?render=RECAPTCHA_SITE_KEY`}
        onLoad={() => {
          grecaptcha.ready(function () {
            grecaptcha
              .execute("RECAPTCHA_SITE_KEY", {
                action: "contact"
              })
              .then(function (token) {
                //console.log(token);
                setCaptchaToken(token);
              });
          });
        }}
      />
    </div>
  );
}

export default App;

```
