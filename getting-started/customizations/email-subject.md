---
description: Customize your notification email subject
---

# Email Subject line

## `subject`

There are two ways you can setup Email Subject.

## 1. Pre-defined Subject

You can add a pre-defined subject by adding a form `input` with `type="hidden"` along with your subject in `value`. See the code below.

```markup
<input type="hidden" name="subject" value="New Submission from Web3Forms">
```

## 2. User Generated Subject

In this case, the subject can be filled by the website visitor. For that, you can use an input `type="text"`. See Code below.

```markup
<input type="text" name="subject" />
```

{% hint style="info" %}
The Name attribute must be called `subject`
{% endhint %}

