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

## LIMITATIONS

BICS CPaaS platform has its own set of limitations that you should be aware of to ensure effective utilization and management.

### SMS Channel

#### File Upload Limits

| Feature                            | Limitation                                                                                                                                  |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| Campaign                           | Maximum of 200 MB.                                                                                                                          |
| Global Other than Campaign Manager | Maximum of 100 MB.                                                                                                                          |
| Impact of Exceeding Limit          | Exceeding the file upload limits may result in rejection of the file, leading to delays in campaign deployment or file processing failures. |
| Workaround                         | Consider compressing files or breaking them down into smaller segments before uploading.                                                    |

#### Campaign Limits

| Feature                   | Limitation                                                                                                          |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| Quick Campaign            | Up to 50,000 messages.                                                                                              |
| Bulk Upload               | Maximum of 500,000 messages. Campaigns exceeding this limit may face delays or failures.                            |
| Impact of Exceeding Limit | Campaigns exceeding the message limits may experience delays in delivery or complete failure of campaign execution. |
| Workaround                | Divide the campaign into smaller segments or batches and send them sequentially.                                    |

#### API Rate Limits

| Feature                   | Limitation                                                                                                                                      |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| Status API                | Up to 1000 requests per minute.                                                                                                                 |
| Balance API               | Up to 1000 requests per minute.                                                                                                                 |
| Impact of Exceeding Limit | Exceeding API rate limits may result in request throttling or blocking, preventing further access to API functionalities from the affected API. |

#### Opt-out Tags

Maximum of 3 opt-out tags can be applied per outbound campaign.

| Feature                   | Limitation                                                                                                                                                           |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Impact of Exceeding Limit | Applying more than 3 opt-out tags may lead to incomplete opt-out management, potentially resulting in unwanted messages being sent to recipients who have opted out. |

#### Campaign Schedule Period

Must be less than 3 months and more than 5 minutes.

| Feature                   | Limitation                                                                                                                    |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| Impact of Exceeding Limit | Scheduling campaigns beyond the specified period may result in scheduling errors or failure to execute campaigns as intended. |

#### Split Schedule Limits

| Feature                   | Limitation                                                                                                                             |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| Batch Size                | For Mobtexting 1000 to 500,000 numbers.                                                                                                |
| Batch Size                | For BICS 1000 to 100,000 numbers                                                                                                       |
| Time Interval             | 5 minutes to 1 hour.                                                                                                                   |
| Impact of Exceeding Limit | Splitting schedules beyond the specified batch size or time interval may lead to scheduling conflicts or errors in campaign execution. |

#### Smart Link Limits

Maximum of 10 requests in 5 minutes per IP.

| Feature                   | Limitation                                                                                                                                                                  |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Impact of Exceeding Limit | Exceeding the smart link request limit may result in IP-based throttling or blocking, preventing further access to smart link functionalities from the affected IP address. |

#### Authentication

Password reset and 2FA requests are limited to 3 attempts within a 5-minute window.
New user activation is limited to 3 requests within a 2-minute window.
API tokens, once lost, cannot be retrieved, and must be recreated.
Impact of Exceeding Limit: Exceeding authentication attempt limits may temporarily lock users out of their accounts or disrupt API access until new tokens are generated.

#### Data Retention and Report Requests

Campaign and media link data retention varies by region and is detailed in the policy.
Requested reports are available for the last 3 months and are archived thereafter.

| Feature                   | Limitation                                                                                                                                                                  |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Impact of Exceeding Limit | Attempting to access archived reports or data beyond the specified retention period may result in unavailability or loss of access to historical campaign data and reports. |

#### Operational Limitations

Ongoing campaigns cannot be aborted or cancelled.
No reseller limit within the application.
Customers cannot transfer credits between transactional and promotional or other services.
Deleted content is irretrievable.
Impact of Exceeding Limit: Violating operational limitations may lead to disruptions in operations, loss of data, or failure to manage account settings as intended.

### SMS Delivery: Loop Protection and Fraud Prevention

#### Message Repetition

To prevent spam and potential scams, a limit is placed on the number of identical SMS messages sent from the same sender (a-nr) to the same recipient (b-nr) within a specified timeframe (x minutes).
No identical messages with the same content can be sent from the same a-nr to the same b-nr within x minutes (where x is a specific time period defined by the service provider).
This rule targets individuals or programs attempting to bombard recipients with repetitive messages.
It allows for legitimate communication while protecting users from unwanted spam.

| Feature                   | Limitations                                                                                                                  |
| ------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| Impact of Exceeding Limit | Violating the message repetition rule may trigger anti-spam mechanisms, resulting in message blocking or account suspension. |

### Voice Channel

#### Data Retention

Voice files, including call logs and recordings, are retained for 60 days before archival.

| Feature                   | Limitation                                                                                                                                       |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| Impact of Exceeding Limit | Exceeding the data retention period may result in loss of access to voice files, call logs, or recordings beyond the specified retention period. |

#### Sticky Agent

Limited to a 2-hour duration.

| Feature                   | Limitation                                                                                                  |
| ------------------------- | ----------------------------------------------------------------------------------------------------------- |
| Impact of Exceeding Limit | Exceeding the sticky agent duration may result in loss of agent assignments or disruptions in call routing. |

#### Bulk Upload

Maximum of 50,000 limits.

| Feature                   | Limitation                                                                                                                       |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| Impact of Exceeding Limit | Attempting to upload bulk data exceeding the specified limit may result in rejection of the upload request or processing errors. |

#### Voice Recording URL Validity

Webhook URLs for recordings are valid for 2 hours only.

| Feature                   | Limitation                                                                                                                                                                                                  |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Impact of Exceeding Limit | Exceeding the recording URL validity period may lead to expired URLs, preventing access to call recordings or triggering errors in webhook processing and can be achieved the same URL from recordings API. |

### VMN Messaging Logs

Retained for 60 days.

| Feature                   | Limitation                                                                                                                                  |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| Impact of Exceeding Limit | Accessing messaging logs beyond the specified retention period may result in unavailability or loss of access to historical messaging data. |

### WhatsApp/RCS/Viber

#### Bulk Upload Limit

Maximum of 2,00,000 messages across these platforms.

| Feature                   | Limitation                                                                                 |
| ------------------------- | ------------------------------------------------------------------------------------------ |
| Impact of Exceeding Limit | Exceeding the bulk upload limit may result in delay or failure in delivering the messages. |

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
