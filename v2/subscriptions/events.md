# Event List

These are all the events that we can utilize to send the payload to the provided webhook.

| Product               | Event | Description
| ------------------ | ------ | ------------ |
| SMS | sms:message:status | We will send the acknowledgment whether the message is delivered or undelivered. |
| Whatsapp | whatsapp:message:in | For receiving updates when user send message to Whatsapp number |
| Whatsapp | whatsapp:message:status | For receiving DLR Status from Whatsapp number to user |
| Rcs | rcs:message:in | For receiving Rcs message event |
| Rcs | rcs:message:status | For receiving Rcs delivery updates|
| Voice | voice:message:out | To receive acknowledgments after CDR events.|
| Interact | vmn:message:in | Once we receive the acknowledgment, we will send the same to the webhook.|
