# Fivetran

In this section, we provide guides and references to use the Fivetran connector.

# Requirements
To access Fivetran APIs, a Fivetran account on a Standard, Enterprise, or Business Critical plan is required.

You can find further information on the Fivetran connector in the [docs](https://docs.open-metadata.org/connectors/pipeline/fivetran).

## Connection Details

$$section
### API Key $(id="apiKey")

Follow the steps mentioned below to generate the Fivetran API key and API secret:

1. Click your user name in your Fivetran dashboard.

2. Click API Key.

3. Click Generate API key. (If you already have an API key, then the button text is Generate new API key.)

4. Make a note of the key and secret as they won't be displayed once you close the page or navigate away.

For more detailed documentation visit [here](https://fivetran.com/docs/rest-api/getting-started).

$$

$$section
### Host Port $(id="hostPort")

Hostport of the Fivetran instance that the connection will be made to
By default OpenMetadata will use `https://api.fivetran.com` to connect to the Fivetran APIs.
$$

$$section
### API Secret $(id="apiSecret")

Follow the steps mentioned below to generate the Fivetran API key and API secret:

1. Click your user name in your Fivetran dashboard.

2. Click API Key.

3. Click Generate API key. (If you already have an API key, then the button text is Generate new API key.)

4. Make a note of the key and secret as they won't be displayed once you close the page or navigate away.

For more detailed documentation visit [here](https://fivetran.com/docs/rest-api/.getting-started)

$$

$$section
### Limit $(id="limit")

This refers to the maximum number of records that can be returned in a single page of results when using Fivetran's API for pagination.
$$
