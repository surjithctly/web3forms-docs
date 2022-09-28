# Simple React Contact Form

In this guide, you will learn how to setup a simple working contact form using React Framework and Web3Forms. No need to setup an SMTP or Custom Backend or Server. It all happens in the front end.  You can copy paste to your react app and it will work.&#x20;

Here's the code:

<pre class="language-jsx"><code class="lang-jsx">import React from "react";

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
    &#x3C;div className="App">
      &#x3C;h1>React File Upload Form&#x3C;/h1>
      &#x3C;form onSubmit={onSubmit}>
        &#x3C;input type="text" name="name"/>
<strong>        &#x3C;input type="email" name="email"/>
</strong>        &#x3C;textarea name="message">&#x3C;/textarea>
        &#x3C;input type="submit" />
      &#x3C;/form>
      &#x3C;span>{result}&#x3C;/span>
    &#x3C;/div>
  );
}

export default App;</code></pre>
