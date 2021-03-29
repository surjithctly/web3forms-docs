# API Reference

{% api-method method="post" host="https://api.web3canvas.com" path="/submit" %}
{% api-method-summary %}
Form Submission
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to submit form submissions. Currently accepts the following options as Form Data. These names are reserved so you should not use these names for your custom form input names.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-form-data-parameters %}
{% api-method-parameter name="apikey" type="string" required=true %}
This is where you should pass your Access Key. It is required to send the form to your email address.
{% endapi-method-parameter %}

{% api-method-parameter name="email" type="string" required=false %}
User Email. This will be used to set reply to address. So its easy to follow-up.
{% endapi-method-parameter %}

{% api-method-parameter name="subject" type="string" required=false %}
Email Subject. It can be submitted by user or prefilled using `hidden` attribute.
{% endapi-method-parameter %}

{% api-method-parameter name="ccemail" type="string" required=false %}
**PRO feature:** Add your co-workers to your email notification.
{% endapi-method-parameter %}

{% api-method-parameter name="replyto" type="string" required=false %}
Reply to Email. If you don't want to use `email` as replyto, you can assign a custom email here.
{% endapi-method-parameter %}

{% api-method-parameter name="redirect" type="string" required=false %}
URL. You can use a custom URL to redirect to a page when the form submits successfully.  
`NOTE: Only recommended when using without JavaScript`
{% endapi-method-parameter %}

{% api-method-parameter name="botcheck" type="boolean" required=false %}
Hidden. To prevent Spam Submissions. Make sure its hidden by adding `display:none;`
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Form Submitted Successfully
{% endapi-method-response-example-description %}

```json
{
   "statusCode":200,
   "success":true,
   "body":{
      "data":{
        [USER SUBMITTED DATA]
      },
      "message":"Email sent successfully!"
   }
}
```

{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Could not complete the request due to client error!
{% endapi-method-response-example-description %}

```json
{
   "statusCode":400,
   "success":false,
   "body":{
      "data":{
        [USER SUBMITTED DATA]
      },
      "message":"Error Description"
   }
}
```

{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}
Something wrong happened in the server!
{% endapi-method-response-example-description %}

```json
{
   "statusCode":500,
   "success":false,
   "body":{
      "data":{
        [USER SUBMITTED DATA]
      },
      "message":"Something went wrong. "
   }
}
```

{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}
