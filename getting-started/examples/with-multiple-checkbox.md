---
description: How to integrate Checkbox with Web3Forms Properly
---

# With Multiple Checkbox

There are some confusions on how  multiple checkboxes works and how to to integrate it with Web3Forms.&#x20;

If you simply added a checkbox like this and sent the data to a regular form action, `check` would return `on` or `off` based on whether the user checked or not.&#x20;

```html
<input type="checkbox" name="check">
```

However, if you need to add a value to your checkbox, you need to define it like this:

```
<input type="checkbox" name="check" value="checked">
```

Now, this would return `check: checked`&#x20;

### Multiple Checkboxes

You need to add the same **name** with different values for multiple checkboxes. See:

```html

<label>Interests</label>
<input type="checkbox" id="coding" name="interest" value="coding" />
<input type="checkbox" id="music" name="interest" value="music" />

```

Web3Forms will then automatically parse them to be comma-separated like this:&#x20;

```
Interests
coding,music
```

### Multiple Checkbox with Javascript

If you are using javascript, you have to manually stringify multiple data like this before sending the request to Web3Forms API. See example code:

```javascript
const formData = new FormData(form);
const interests = [];
 
form.querySelectorAll('input[name="interest"]:checked').forEach((checkbox) => {
    interests.push(checkbox.value);
});
  
formData.set('interest', interests);
```

This will set the checkbox as you intended.&#x20;

#### Live Demo

{% embed url="https://codepen.io/surjithctly/pen/eYobEbO" %}
[View Codepen](https://codepen.io/surjithctly/pen/eYobEbO?editors=1010)
{% endembed %}

