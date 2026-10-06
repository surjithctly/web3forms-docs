# Submissions API

Read your form submissions programmatically — including metadata like user IP address — and create submissions straight from your own backend. This is a REST API, separate from the public form endpoint your HTML form posts to.

{% hint style="info" %}
The Submissions API is a **PRO feature**. Create and manage API keys from your [dashboard](https://app.web3forms.com/account/api-keys).
{% endhint %}

## Base URL

```
https://api.web3forms.com/v1
```

## Authentication

Every request must include a Bearer token in the `Authorization` header. Your API key looks like `w3f_live_…`.

```bash
curl https://api.web3forms.com/v1/forms \
  -H "Authorization: Bearer w3f_live_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
```

{% hint style="warning" %}
Your API key is shown **only once** when you create it. Store it somewhere safe. If you lose it, revoke it and create a new one.
{% endhint %}

### Managing keys

Go to **Dashboard → Account → API Keys**:

* **Create** a key — give it a label (e.g. "Production backend") and pick its permissions. The full key is shown once.
* **Revoke** a key — takes effect immediately; any request using it returns `401`.
* You can hold up to **10 active keys** at a time.

A key is scoped to your account and works for any form you own.

### Permissions

| Permission             | Grants                                                                     |
| ---------------------- | -------------------------------------------------------------------------- |
| **Read submissions**   | `GET /forms`, `GET /submissions`, `GET /submissions/{id}`. Always enabled. |
| **Create submissions** | `POST /submissions`. Opt-in when you create the key.                       |

Keys are read-only unless you tick **Create submissions**. A key without that permission gets `403` on `POST /submissions`.

{% hint style="warning" %}
Permissions are fixed for the life of a key. To change them, revoke the key and create a new one.
{% endhint %}

## Rate limits

Requests are throttled at **20 requests/second** (burst 50) per account. Exceeding this returns `429` with a `Retry-After` header (in seconds).

***

## List forms

<mark style="color:green;">`GET`</mark> `https://api.web3forms.com/v1/forms`

Returns all forms you own.

#### Response

```json
{
  "data": [
    {
      "form_id": "0a1b2c3d-....",
      "form_name": "Contact Form",
      "created_at": "2026-01-15T10:30:00.000Z",
      "total_count": 142
    }
  ]
}
```

***

## List submissions

<mark style="color:green;">`GET`</mark> `https://api.web3forms.com/v1/submissions`

Returns submissions for a form, newest first.

#### Query Parameters

| Name                                       | Type    | Description                                  |
| ------------------------------------------ | ------- | -------------------------------------------- |
| form\_id<mark style="color:red;">\*</mark> | string  | The form to fetch submissions for.           |
| limit                                      | integer | Page size. Default `50`, min `1`, max `100`. |
| cursor                                     | string  | Pagination cursor from a previous response.  |

#### Example

```bash
curl "https://api.web3forms.com/v1/submissions?form_id=FORM_ID&limit=50" \
  -H "Authorization: Bearer w3f_live_…"
```

#### Response

```json
{
  "data": [
    {
      "id": "sub_a1b2c3d4e5f6",
      "form_id": "0a1b2c3d-....",
      "submitted_at": "2026-05-26T18:21:09.123Z",
      "ip_address": "203.0.113.42",
      "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) ...",
      "site_url": "https://example.com/contact",
      "fields": {
        "name": "Jane Doe",
        "email": "jane@example.com",
        "message": "Hello!"
      },
      "attachments": []
    }
  ],
  "has_more": true,
  "next_cursor": "eyJQSyI6Ii4uLiJ9"
}
```

### Pagination

When `has_more` is `true`, pass `next_cursor` back as the `cursor` parameter to fetch the next page. Repeat until `has_more` is `false`.

```bash
curl "https://api.web3forms.com/v1/submissions?form_id=FORM_ID&cursor=NEXT_CURSOR" \
  -H "Authorization: Bearer w3f_live_…"
```

***

## Get a submission

<mark style="color:green;">`GET`</mark> `https://api.web3forms.com/v1/submissions/{id}`

Returns a single submission by its `id`.

#### Example

```bash
curl "https://api.web3forms.com/v1/submissions/sub_a1b2c3d4e5f6" \
  -H "Authorization: Bearer w3f_live_…"
```

#### Response

```json
{
  "data": {
    "id": "sub_a1b2c3d4e5f6",
    "form_id": "0a1b2c3d-....",
    "submitted_at": "2026-05-26T18:21:09.123Z",
    "ip_address": "203.0.113.42",
    "user_agent": "Mozilla/5.0 ...",
    "site_url": "https://example.com/contact",
    "fields": { "name": "Jane Doe", "email": "jane@example.com" },
    "attachments": []
  }
}
```

***

## Create a submission

<mark style="color:blue;">`POST`</mark> `https://api.web3forms.com/v1/submissions`

Submits a form from your own server. The submission is processed exactly like one sent from a browser: it's stored, your notification email and autoresponder go out, and your integrations run.

Requires a Secret API key with the **WRITE** permission.

{% hint style="info" %}
Use this when the data never passes through a browser — a server-side form handler, a CRM sync, a queue worker, an AI agent. For normal HTML forms, keep posting to [the regular endpoint](installation.md) with public access key.
{% endhint %}

#### Body Parameters

| Name                                       | Type   | Description                                                                                                                                              |
| ------------------------------------------ | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| form\_id<mark style="color:red;">\*</mark> | string | The form to submit to. Must be a form you own.                                                                                                           |
| fields<mark style="color:red;">\*</mark>   | object | Your form fields as name/value pairs. At least 1, at most 100.                                                                                           |
| subject                                    | string | Overrides the notification email subject.                                                                                                                |
| from\_name                                 | string | Overrides the sender name.                                                                                                                               |
| replyto                                    | string | Reply-To address for the notification email.                                                                                                             |
| cc                                         | string | CC address.                                                                                                                                              |
| bcc                                        | string | BCC address.                                                                                                                                             |
| preheader                                  | string | Email preheader text.                                                                                                                                    |
| metadata                                   | object | Attribution for the original submitter: `ip`, `user_agent`, `site_url`. See [Passing the real submitter](submissions-api.md#passing-the-real-submitter). |
| attachments                                | array  | Files to attach. See [Attachments](submissions-api.md#attachments).                                                                                      |

#### Example

```bash
curl -X POST https://api.web3forms.com/v1/submissions \
  -H "Authorization: Bearer w3f_live_…" \
  -H "Content-Type: application/json" \
  -d '{
    "form_id": "0a1b2c3d-....",
    "fields": {
      "name": "Jane Doe",
      "email": "jane@example.com",
      "message": "Hello from my backend!"
    },
    "subject": "New lead from the pricing page"
  }'
```

#### Response

`201 Created`

```json
{
  "data": {
    "id": "sub_a1b2c3d4e5f6",
    "form_id": "0a1b2c3d-....",
    "submitted_at": "2026-05-26T18:21:09.123Z"
  }
}
```

Use that `id` with [Get a submission](submissions-api.md#get-a-submission) to read the stored record back.

### Form fields go in `fields`

Everything the person filled in belongs inside `fields`. Email options like `subject` sit at the **top level** of the request, next to `form_id`.

```json
{
  "form_id": "0a1b2c3d-....",
  "fields": { "name": "Jane", "subject": "Billing question" },
  "subject": "New support request"
}
```

### Passing the real submitter

If the data started with a real visitor — say your server validates a form before forwarding it — pass their details in `metadata` so your dashboard, spam check and notification email show the visitor instead of your server:

```json
{
  "form_id": "0a1b2c3d-....",
  "fields": { "name": "Jane Doe", "email": "jane@example.com" },
  "metadata": {
    "ip": "203.0.113.42",
    "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) …",
    "site_url": "https://example.com/contact"
  }
}
```

All three are optional. Omit them and the submission is attributed to your server.

### Attachments

Send files as base64. Each needs a `filename` and `content`; `content_type` is optional.

```json
{
  "form_id": "0a1b2c3d-....",
  "fields": { "name": "Jane Doe" },
  "attachments": [
    {
      "filename": "resume.pdf",
      "content": "JVBERi0xLjQKJc…",
      "content_type": "application/pdf"
    }
  ]
}
```

Up to **10 files**, **5 MB total** (measured after decoding). Files are stored and linked from the notification email, the same as a browser upload.

### What's checked, and what isn't

Because the API key already proves you own the form, the browser-oriented guards don't apply:

| Not applied                   | Why                                                                               |
| ----------------------------- | --------------------------------------------------------------------------------- |
| Captcha                       | A server has no captcha token. Works even on forms that require one for browsers. |
| Domain / referer restrictions | There's no referring page to check.                                               |
| Per-IP rate limit             | All your calls come from one server. The per-form limit still applies.            |

Everything else is unchanged: submissions **count toward your monthly quota**, spam filtering still runs, and your form's per-hour rate limit still applies.

{% hint style="warning" %}
There's no idempotency key. If a request times out and you retry it, you may create a duplicate submission — check [List submissions](submissions-api.md#list-submissions) before retrying, or de-duplicate on your side.
{% endhint %}

{% hint style="danger" %}
Never put an API key in frontend code, a mobile app, or a public repo. Anyone holding a key with WRITE can post to every form on your account and burn your quota. Call this endpoint from your server only.
{% endhint %}

***

## Errors

Errors return a non-2xx status and a JSON body:

```json
{
  "error": {
    "code": "unauthorized",
    "message": "Invalid API key"
  }
}
```

| Status | Code                  | Meaning                                                                            |
| ------ | --------------------- | ---------------------------------------------------------------------------------- |
| `400`  | `bad_request`         | Missing or invalid parameter (e.g. no `form_id`, a reserved field name)            |
| `400`  | `submission_rejected` | The submission was refused — see `message` (quota reached, plan limit, empty data) |
| `401`  | `unauthorized`        | Missing, malformed, or revoked key                                                 |
| `403`  | `forbidden`           | Key not authorized for that form, or missing a required permission                 |
| `404`  | `not_found`           | Form or submission doesn't exist (or isn't yours)                                  |
| `429`  | `rate_limit_exceeded` | Too many requests — retry after the header value                                   |
| `500`  | `server_error`        | Something went wrong on our end                                                    |

`submission_rejected` carries the reason straight through, so show or log the `message`:

```json
{
  "error": {
    "code": "submission_rejected",
    "message": "You have reached your monthly submission limit."
  }
}
```
