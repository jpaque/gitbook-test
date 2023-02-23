---
description: Exploring the differences between MKDocs and GitBook
---

# Usage and Billing API Reference

## Usage API Reference

The Usage REST APIs allow system administrators to retrieve usage data for each of their Applications and Applications they manage. An API key is required to authenticate with this API. API keys are created and managed in the [**API Keys**](https://docs.senetco.io/ap/adminApiKeys/#api-keys) view. \
[Static external link](https://docs.senetco.io/ap/adminApiKeys/#api-keys) (repeat)\
[relative internal link](api-keys-subpage.md) (dumby page)\
Response types vary from method to method.

{% hint style="warning" %}
The keys required for Usage API access and Onboarding API access are different, i.e. An Onboarding API key will not grant access to the Usage APIs and vice versa.
{% endhint %}

## Summary API

Returns a summary of all usage data for a given Application, month, and year.

#### Resource URL <a href="#resource-url" id="resource-url"></a>

[https://api.senetco.io/rest/integration/usage/summary](https://api.senetco.io/rest/integration/usage/summary)

{% embed url="https://api.senetco.io/rest/integration/usage/summary" %}
Example of an embedded URL with a caption
{% endembed %}

> [https://api.senetco.io/rest/integration/usage/summary](https://api.senetco.io/rest/integration/usage/summary) (this is a quote block)
>
> (this is an extended quote block)

{% code title="Resource URL (this is an optional caption) " overflow="wrap" %}
```
https://api.senetco.io/rest/integration/usage/summary
```
{% endcode %}

```
https://api.senetco.io/rest/integration/usage/summary
```

{% code overflow="wrap" lineNumbers="true" %}
```
https://api.senetco.io/rest/integration/usage/summary
```
{% endcode %}

{% swagger method="get" path="" baseUrl="https://api.senetco.io/rest/integration/usage/summary" summary="(can't delete "/users" is it there after publish?)" %}
{% swagger-description %}
An example API call for the Usage API
{% endswagger-description %}

{% swagger-parameter in="path" name="eui" type="eui" required="true" %}
The IEEE-64 identifier for the LoRa Application
{% endswagger-parameter %}

{% swagger-parameter in="path" name="month" type="month" required="true" %}
The month to retrieve usage data for.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="year" type="year" required="true" %}
The year to retrieve usage data for.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="" %}
section above should be query but doesn't let you cut and paste
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Request was successfully processed" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Invalid request due to insufficient or malformed parameters" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}

{% swagger-response status="403: Forbidden" description="Access to this resource has been rejected due to an authorization issue" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="Indicates that either the given Application cannot be found or there is no usage data for the given month/year" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}
{% endswagger %}

### Responses

| Code | Reason                        | Description                        |
| ---- | ----------------------------- | ---------------------------------- |
| 200  | Success                       | Request was successfully processed |
| 403  | Authorization Failure         |                                    |
| 400  | Bad Request                   |                                    |
| 404  | Application or File not found |                                    |
| 500  | Server is busy                |                                    |
|      |                               |                                    |

#### Fields

| FieldName  | DataType | Category | Description                                                                                                                                                                                                                                    |
| ---------- | -------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| devEui     | String   | Default  | 64-bit Extended Unique Identifier of the Device transmitting the message                                                                                                                                                                       |
| gwEui      | String   | Default  | 64-bit Extended Unique Identifier of the Base Station that received the message. Without Duplicates included this identifies Base Station that first relayed the message, though not necessarily the one preferred for downlink communication. |
| joinId     | Number   | Default  | Incrementing Integer used to Identify the last join                                                                                                                                                                                            |
| pdu        | String   | Default  | Protocol Data Unit or Customer Payload data                                                                                                                                                                                                    |
| port       | Number   | Default  | 0 indicates that the FRMPayload contains MAC commands only and 1..223 are Application specific                                                                                                                                                 |
| seqno      | Number   | Default  | Incrementing Integer used to Identify an uplink                                                                                                                                                                                                |
| txtime     | String   | Default  | Time the message was received by the Network Server                                                                                                                                                                                            |
| channel    | Number   | RF Field | Frequency Channel of the transmission                                                                                                                                                                                                          |
| datarate   | Number   | RF Field | Integer that maps to a spreading factor, bandwidth and bitrate                                                                                                                                                                                 |
| freq       | Number   | RF Field | Transmit Frequency in MHz                                                                                                                                                                                                                      |
| rssi       | Number   | RF Field | Received Signal Strength Indicator reported by receiving Gateway                                                                                                                                                                               |
| snr        | Number   | RF Field | Average Signal to Noise Ratio reported by receiving gateway                                                                                                                                                                                    |
| ismBand    | String   | RF Field | The ISMBand (US915,EU868,EU433,CN779,AU915,CN470, etc) reported by the receiving Gateway                                                                                                                                                       |
| maxPayload | Number   | RF Field | Max Payload size in bytes that can be sent at the current datarate by this Device                                                                                                                                                              |
| appEui     | String   | Optional | The Application's IEEE EUI-64 identifier.                                                                                                                                                                                                      |
| ack        | Boolean  | Optional | Flag indicating if the uplink was acknowledging the receipt of a downlink                                                                                                                                                                      |
| ackDnMsgId | Number   | Optional | When present, indicates that a Device has acknowledged a specific downlink message ID                                                                                                                                                          |
| devClass   | String   | Optional | LoRaWAN Class designation ("A", "B", "C") of the Device                                                                                                                                                                                        |
| devType    | String   | Optional | The type of the Device                                                                                                                                                                                                                         |
| dup\*      | Boolean  | Optional | Flag indicating if the uplink was already forwarded because it was heard by multiple Gateways                                                                                                                                                  |
| estLat\*   | Number   | Optional | Estimated latitude of the Device in decimal degrees                                                                                                                                                                                            |
| estLng\*   | Number   | Optional | Estimated longitude of the Device in decimal degrees                                                                                                                                                                                           |
| cfgLat     | Number   | Optional | Configured latitude of the Device in decimal degrees                                                                                                                                                                                           |
| cfgLng     | Number   | Optional | Configured longitude of the Device in decimal degrees                                                                                                                                                                                          |
| tags       | String   | Optional | A comma separated list of tags configured on this Device                                                                                                                                                                                       |
| metadata   | String   | Optional | The metadata value configured on this Device                                                                                                                                                                                                   |
| devProfile | String   | Optional | The name of the Profile applied to this Device                                                                                                                                                                                                 |
| fwVersion  | String   | Optional | The firmware version of this Device                                                                                                                                                                                                            |
| gwRxTime   | String   | Optional | Time the message was received by the Gateway                                                                                                                                                                                                   |

### Curl Example

{% code title="Curl Example" overflow="wrap" %}
```
curl -X GET \ 'https://api.senetco.io/rest/integration/usage/summary?eui=<EUI>&year=<YEAR>&month=<MONTH>' -H 'Authorization: <API_KEY_TO_USE>'
```
{% endcode %}

**Example:**

```JSON
{
   "ack":true,
   "ackDnMsgId": 100000,
   "devClass": "A" ,
   "devEui":"FFFFFFFFFFFFFFFF",
   "gwEui":"AAAAAAAAAAAAAAAA",
   "joinId":216,
   "pdu":"01000016D7011400060E06",
   "port":1,
   "seqno":1,
   "txtime":"2017-02-09T12:38:38.375Z"
}
```
