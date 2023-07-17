# Overview

Our SMS API provides a convenient way to send text messages to users worldwide using straightforward RESTful APIs.

Key features of our SMS API include:

- Programmatically send and receive a high volume of SMS messages globally.
- Seamlessly integrate with the web technologies you already use, allowing your apps to scale effortlessly.
- Experience low latency and high delivery rates when sending SMS.
- Receive SMS for free using SMS-enabled local numbers available in various countries.
- Pay only for the SMS messages you send, without any additional charges.

With our SMS API, you can efficiently reach your users through text messages, leveraging the benefits of global coverage, reliability, and cost-effectiveness.

#### Available HTTP methods

Our API relies on HTTP verbs to determine the desired action for an object: reading (`GET`), deleting (`DELETE`), or creating (`POST`). In cases where your web application lacks support for `POST` or `DELETE` operations, we offer a solution. You can specify the desired method by including the query parameter `_method`.

#### Number format

Numbers are a key concept to understand when working with the API. The following points should be considered before developing your Application.

All phone numbers in the APIs use E.164 format. This means that numbers:

- Omit both a leading `+` and the international access code such as `00`.
- Contain no special characters, such as a space, `()` or `-`

For example, a US number would have the format `14155550101`. A UK number would have the format `447700900123`.

#### Sender ID

Every text message sent through our API is associated with a sender ID. When utilizing the API to send a text message, you have the option to use any of the approved sender IDs associated with your account.

If you haven't created a sender ID yet, don't worry! You can easily create one within our application. Once your Sender ID is approved, you can immediately begin sending messages using it.

#### Message Templates

Message Templates are message formats for common reusable messages a business may want to send. Businesses must use Message Templates for sending notifications to customers.

## SMS Length Summary

#### Standard GSM Characters

| No.of SMS | No.of Characters          |
| --------- | ------------------------- |
| 1         | 160 characters.           |
| 2         | (2 x 153) 306 characters. |
| 3         | (3 x 153) 459 characters. |

#### Unicode Characters

| No.of SMS | No.of Characters         |
| --------- | ------------------------ |
| 1         | 70 characters.           |
| 2         | (2 x 67) 134 characters. |
| 3         | (3 x 67) 201 characters. |
