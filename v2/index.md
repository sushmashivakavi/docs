# API OVERVIEW

Our APIs are built using the `REST` standard, which enables you to effortlessly send messages to your end users, simplifying your work. With this feature, you can send alerts, reminders, notifications, and even verification messages containing one-time passcodes (OTP).

This documentation provides clear instructions on how to integrate our API using different _*HTTP*_ and _*JSON*_ APIs.

We are here to assist you in configuring, accessing, and utilizing our API for our services.

To integrate our API, you can use any HTTP recipient in any programming language of your choice.

@if(isset($products))

## PRODUCTS/SERVICES

List of product names and product codes

@foreach($products as $key => $name)
@if ($loop->index == 0)
| Product Code | Product Name |
| ---- | ---- |
@endif
| {{ $key }} | {{ $name }} |
@endforeach

@endif

#include "_include/endpoint.md"

#### Available HTTP methods

In our API, we utilize HTTP verbs to determine the action you wish to perform on an object. You can use (`GET`) to retrieve information, (`DELETE`) to remove an object, or (`POST`) to create a new one. In cases where your web application doesn't support `POST` or `DELETE` directly, we offer an alternative method by allowing you to specify the desired action using the query parameter `_method`.

## AUTHENTICATION

To authenticate your API requests, each request must include request headers with your access token.

Don't have an access token? You can find it in the menu bar under `Developers -> API Keys/Access Tokens`.

If your application is unable to send an Authorization header, you can provide your access key using the GET parameter `access_token`.

> "Please note that your API keys carry significant privileges. It is crucial to keep them completely secure and refrain from sharing your secret API keys in publicly accessible places such as GitHub. For more information, refer to [API Access Key Security](#content-api-access-key-security)."

On our platform, we offer incoming request whitelisting for our REST API. You can whitelist specific IP addresses when generating the access token.

### CURL Example

```shell
$ curl {endpoint}auth/me \
-H 'Authorization: Bearer 38e896f55670311982434e929559xxxx' \
-H 'Accept: application/json'
```

### GET Example

```shell
$ curl {endpoint}auth/me?access_token=38e896f55670311982434e92955xxxx \
-H 'Accept: application/json'
```

If possible, please use the Authorization header.

## IP ADDRESSES

Our API platform operates on a globally distributed infrastructure, which means you cannot whitelist the IP addresses of our platform. It's important to note that delivery reports and inbound messages may originate from various IP addresses.

## API ACCESS KEY SECURITY

Your API access key serves as your authentication token for API usage, making it crucial to handle them securely. It's essential to treat your API access keys with the same level of care as your passwords. Ensure they are stored securely and never shared with anyone.

One common mistake is unintentionally exposing API keys by committing them to public repositories on platforms like GitHub. This can lead to fraudsters discovering and misusing your API access key, potentially sending spam messages or depleting your account balance. There are several techniques to mitigate this risk. Storing your API access key in an environment variable, passing it as a command line argument, or utilizing a secrets manager can all help prevent accidental exposure. Remember, avoid hard-coding your API access key and refrain from checking it into public code repositories.

Similarly, be cautious when sharing code snippets on platforms such as PasteBin, GitHub Gists, or StackOverflow, as it can inadvertently expose your API access key. Ensure that both you and your developers are aware of this risk and take necessary precautions.

## RATE LIMITS

To keep you in compliance, We maintains the appropriate rate limits:

| API | VALUE                                                                                                                                                                   |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| All | `GET` Requests are rate limited to 1000 requests per minute. Once this limit has been crossed, your requests will be rejected with an HTTP 429 'Too Many Requests' code |

You can contact our support team to increase the limit. Our team will increase the limit case by case.

## ERROR CODES

We utilize standard HTTP status codes to indicate the outcome of an API request. HTTP status codes in the 2xx range signify that the request was successfully processed, while codes in the 4xx range indicate an error resulting from the information provided. Common examples of errors in the 4xx range include authentication issues, insufficient balance, or missing or incorrect parameters.

If an error occurs, the response body will provide a JSON-formatted message that precisely identifies the issue at hand. This informative response will clearly indicate the nature of the error and provide relevant details.

#### ATTRIBUTES

| Name    | Value                                                                                                                                     |
| ------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| status  | This represents the error type. OK or 200 is success and rest everything is failed.                                                       |
| code    | This represents the http code. This value is optional. Not be available in all responses.                                                 |
| message | A human-readable description of the error. You can provide your users with this information to indicate what they can do about the error. |

## HTTP STATUS CODES

| code | Descriptions                                                                     |
| ---- | -------------------------------------------------------------------------------- |
| 200  | OK - Everything went as planned.                                                 |
| 202  | Accepted - Request accepted.                                                     |
| 400  | Bad Request - Something in your header or request body was malformed.            |
| 401  | Unauthorized - Necessary credentials were either missing or invalid.             |
| 403  | Your credentials are valid, but you don't have access to the requested resource. |
| 404  | The resources cannot be found                                                    |
| 409  | Conflict - You might be trying to update the same resource concurrently.         |
| 422  | Validation error                                                                 |
| 429  | Too Many Requests - You are calling our APIs more frequently than we allow.      |
| 5xx  | Something went wrong on our end. Please try again                                |
