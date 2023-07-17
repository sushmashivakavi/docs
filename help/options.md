# Mobile Number Masking

Sometimes customer don't want to display full mobile number in panel. In that case we will hide the last 4 digits of the mobile number by enabling below configuration.

In user options we need to set `mobile_secure` : 1 in options.

## Hide Message

For hiding complete message in the panel and reports we need to enable the following option.

In user options we need to set  `hide_msg`: 1 in options.

## Voice OTP

In some cases customer want to trigger an voice call when message is not getting delivered in speicified time like OTP messages. In order to work we need to enable following configuration in service(Transactional, promotional, Scrub) level.

In meta we need to enable voice option as `{"voice":{"bridge":918068057xxx,"access_token":"a19eb34810e672cxxxxxxxxxx","flow_id":191,"duration":30}}`

|Name|Description|Example|
|--- |--- |--- |
|bridge|Bridge number belongs to customer account|918068057xxx|
|access_token|API key of the customer|a19eb34810e672cxxxxxxxxxx|
|flow_id|Flow Id configured in customer account|191|
|duration|Duration for ending the call|Defaults to 30 Seconds|

