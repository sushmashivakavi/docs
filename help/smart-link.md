# Smart Link

URL shortening is a method used to reduce the length of a URL while still ensuring it directs users to the intended page. It involves employing an HTTP Redirect on a short domain name, which points to the web page with a longer URL.

This technique proves particularly useful in messaging technologies that impose strict character limitations on messages.

Additionally, Smart URL provides traffic tracking capabilities, allowing you to monitor the number of visits to the domain. Furthermore, it offers advanced analytics to determine the identities (mobile numbers) of visitors to the page.

#### Note :

Smart link requests are rate limited to 10 requests per 5 minutes. Once this limit has been crossed, your requests will be rejected with an HTTP 429 ‘Too Many Requests’ code.
Short links don’t implement additional security mechanisms and are available for everyone who has that short links.

#### Customizing the redirection of Smart URL

Use a single short URL in your SMS campaign and based on your customer's device details route them to different domain of your's.

Below are the replaceable parameters that can be used along with the URL to extract customer device/IP details

|Name|Description|Example|
|--- |--- |--- |
|client_ip|IP from which the URL was accessed|156.151.23.65|
|host|Domain name of the URL|Example.com|
|user_agent|User agent used by the URL|Mozilla/5.0 (iPad; U; CPU OS 3_2_1 like Mac OS X; en-us) AppleWebKit/531.21.10|
|browser|Browser in which the URL was accessed|msie|
|browser_version|Version of the browser in which the URL was accessed|11.0|
|browser_lang|Language of the operating system in which the URL was accessed|English|
|browser_engine|Browser engine in which the URL was accessed|Trident|
|platform|Operating system of the device in which the URL was accessed|androidos|
|platform_name|code of the OS from where the URL was accessed|(AN) for Android|
|platform_version|Version of the operating system of the device in which the URL was accessed|5.0|
|device_type|Type of device in which the URL was accessed|phone|
|device_brand|Brand of the device in which the URL was accessed|Motorola|
|device_version|Version number of the device in which the URL was accessed|XT1068|
|device_model|Model name of the device in which the URL was accessed|HTC Dream|
|touch_enabled|If or not the device from where the URL was accessed is touch enabled or not|yes|
|country_code|Country from where the URL was accessed|IN|
|country|Country from where the URL was accessed|india|
|region|State from where the URL was accessed|Karnataka|
|city|City from where the URL was accessed|Bangalore|
|created_at|requested time in unixtimestamp|1426243175|
|mobile|Short URL recepient mobile number|9999999999|

## WebHook

The concept of WebHooks is quite simple. A WebHook acts as an HTTP callback, specifically an HTTP GET request, which is triggered when a certain event occurs. It serves as a straightforward means of event notification through an HTTP GET.

In our implementation, we will send a `curl` request to your server, including the specified replaceable variables. You have the option to store these details in your crm or take any desired action based on the received data.
