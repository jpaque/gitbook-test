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

### Curl Example

{% code title="Curl Example" overflow="wrap" %}
```
curl -X GET \ 'https://api.senetco.io/rest/integration/usage/summary?eui=<EUI>&year=<YEAR>&month=<MONTH>' -H 'Authorization: <API_KEY_TO_USE>'
```
{% endcode %}
