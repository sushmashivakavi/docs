# Moengage SMS Integration

## Steps to configure a Custom Connector
To seamlessly integrate CpaaS as an SMS provider within MoEngage, follow these steps:
### Access MoEngage Dashboard:
Navigate to Settings > Channel > SMS & Connector on the MoEngage Dashboard, then select the SMS Connector Config tab.
### Create Custom Connector:

| Field | Description              |
| ---------------| -------------------------------------|
| Connecter Name | Enter a name to identify the custom connector.|
| Sender Name    | Specify the sender ID. |
### Configure Provider Endpoint:
Select the POST method and use the following API endpoint:

```
{domain}/api/v2/sms/moengage/send
```
### Define Headers:
Set the headers as follows:
![alt text](/images/docs/plugins/moengage/headers.png)

Include the key-value pairs:
| Key | value              |
| ---------------| -------------------------------------|
| Accept         | application/json                     |
| Authorization  | Bearer 7160f04c05870ee************** |
| Content-Type   | application/json                     |

### Body Configuration:
Choose the body type as JSON to pass data as key-value pairs.

![alt text](/images/docs/plugins/moengage/body.png)

| Key | value                      |
------------|----------------------|
| sender    | Ex: TXTSMS           | 
| to        | Moesms_destination   |
| message   | Moesms_message       |
| service   | T                    |


### OPTIONAL PARAMETERS

| Name        | Descriptions |
| ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| entity_id   | Principal Entityid registered in DLT portal (applicable for indian routes only)                                                                                         |
| template_id | TemplateId registered in DLT portal (applicable for indian routes only)                                                                                                 |
| webhook_id  | The `id` of the webhook created in Webhook Section for which the SMS response to be sent after delivery report from operator. [read more](/docs/{version}/webhook) |
| time        | Scheduled time (in format: yyyy-mm-dd hh:mm:ss) for sending the SMS|
| type        | Specifies if the SMS to be sent is Unicode, Normal, or Auto-detect (values: "U", "N", or "A")                                                                                           |
| flash       | Parameter for sending flash SMS via API (values: 1 or 0)                                                                                                  |
| custom      | Your own unique_id parameters|
| port | Port number to which SMS has to be delivered |

### Send Test SMS:
Click on the "Send Test SMS" button to send a test SMS. Choose the country, mobile number, and actual message. Once the test message is successfully submitted, save the configuration.

### Configure Delivery Tracking:
Click on the "Configure Delivery Tracking" button to obtain the delivery tracking URL. Copy the URL and create a generic webhook in CpaaS. [create here](/developer/webhooks).
### Paste the Webhook ID:
Copy the webhook ID from the CpaaS panel and paste it in the body section as a value for webhook_id. 
### Map Delivery Response:
Map the delivery response as illustrated below:
![alt text](/images/docs/plugins/moengage/dlr.png)

Follow these steps meticulously to ensure a successful integration of Mobtexting as an SMS provider within your MoEngage platform.