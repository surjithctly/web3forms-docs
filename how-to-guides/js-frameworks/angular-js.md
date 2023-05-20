# Integrate Web3Forms API in Angular

## Why Web3Forms?
We use Web3Forms for the needlessness of a back-end server, so no need to set-up a back-end API to send our emails.

## prerequisites

Angular basics:
- **_Services_**
- **_TemplateForms_**

---

## Let's move to the code part:
- Let's assume that you already initialized your app and you have your component that has the form.

1. Create a service (_<u>**mail**</u>_)
```
ng generate service services/mail
```
- define a method called (_<u>**sendEmail()**</u>_) that will return a _Promise_ and accept a parameter (<u>**_formData_**</u>) that has type of (_<u>**FormData**</u>_).
- in the method we are going to return the _Promise_ of the built in function (_**<u>fetch()</u>**_), which is accepting 2 arguments:

1. API endpoint: `https://api.web3forms.com/submit`.

2. Object with 2 properties:
`{
  method: 'POST',
  body: formData
}`

- our _**<u>service mail</u>**_ method should look like:

<img width="668" alt="angular service method to send Web3Forms emails" src="https://github.com/surjithctly/web3forms-docs/assets/78637183/e798321e-84dc-4451-a4c0-fd6225d42aee">

- that's it for the _**<u>mail service</u>**_.

---

- Now let's take a look at the HTML **_<u>form</u>_**:

_We splitted the Form HTML code into 2 images for a better view as well as we are you using TailwindCSS for styling_

<img width="668" alt="angular HTML form part 1" src="https://github.com/surjithctly/web3forms-docs/assets/78637183/9bf71113-daff-4b33-8a0f-4328f4b99a17"> 

<img width="668" alt="angular HTML form part 2" src="https://github.com/surjithctly/web3forms-docs/assets/78637183/1245cccc-3fb9-4eed-b9b7-134f0ae36515">

- As you can see we are assigning the values of the inputs to an object in our component class (<u>_**<u>contactFormValues</u>**_</u>) with the help of **_<u>template forms</u>_**, and we have a button being used to submit the form as well as we have (<u>_**<u>ng-container</u>**_</u>) and (<u>_**<u>ng-template</u>**_)</u> inside the button tag to display whether the text (**_send_**) or show a spinning animated (_**icon**_) that indicates the form is being submitted.

- Let's take a look at the component class properties and methods:

> - Class properties:

<img width="668" alt="angular component class properties" src="https://github.com/surjithctly/web3forms-docs/assets/78637183/1e3b76ca-fbdf-4ed3-a4af-51985d2ee2de">

> - Class methods:

<img width="668" alt="angular component class methods" src="https://github.com/surjithctly/web3forms-docs/assets/78637183/7ce07746-7134-4c1c-9295-63f90dbe133b">

## Class properties explanation:

- `showAlert: boolean = false;` To display alert message (success or fail).

- `alertMessage: string = '';` To hold the alert message.

- `onSubmit: boolean = false;` To set and track submit state.

- `iconLoad = faArrowRotateForward;` To define and rename the icon from (fontAwesome library).

- contactFormValues
```
contactFormValues = {
    name: '',
    email: '',
    body: '',
  };
```
 To hold the inputs' values with the help of the template forms of Angular.

## Class methods explanation:

- `hideAlert()` To hide the alert message after 5 seconds.

- `submitEmail(contactForm)` An async function that accepts an instance of the **_<u>NgForm</u>_** to handle the submit form and in this method let's explain 3 parts of it:

1. Create a formData instance and append values (contactFormValues) because it is the way that _Web3Forms_ accepts the form. 
 - `formData.append('name', this.contactFormValues.name);` add input value (_**name**_) from template to formData, follow the same steps to add the other inputs' values (**_email_**, **_body_**).
 - grab your **_<u>access key</u>_** from email you received earlier and add it into the environment variables, in our case we called it (**_<u>form_access_key</u>_**) see example below:
 - `formData.append('access_key', environment.form_access_key);` 
 - `formData.append('subject', 'Email Support From Your Site');` to set subject text.
 - `formData.append('from_name', 'Contact Notification');` to set a name for the form.
 
 You can read more about customizations here: [Web3Forms Customization](https://docs.web3forms.com/getting-started/customizations)

2. `try | catch` blocks, in the `try` block we are calling the `mailService.sendEmail()` method to submit the form and in case the form was successfully submitted we show a success message and reset the values to `null` by the help of the instance `NgForm` that has `reset()` method, in our case it is `contactForm.reset()`, and in case there is an error we added a _**guard clause**_ and inside its block we throw an error to force the code to jump to the `catch` block and show an error message.

3. and at the end of the method we reset `onSubmit` property to `false`, `showAlert` to `true` and call the `hideAlert()` method.

---

> _**<u>Congratulations! You are all set up and ready to go.</u>**_

---

>[Web3Forms home page](https://web3forms.com)

>[Web3Forms docs](https://docs.web3forms.com/)

---
### THIS TUTORIAL WRITTEN BY: [CoderNadir](https://dev.to/codernadir)
---
