# Overview

Fuse API is an easy to use way to access and perform community-centric payments on the Fuse Network.

To start with an API please go to the [fuse studio](https://studio.fuse.io), sign up and open your economy. Economy is what defines the payment model your community is using. For example you start with choosing a currency that your economy is going to use.

After onboarding and creating a community you can get:

* API key to start using various Fuse API's
* JWT to access the[ Admin API](admin-api.md)

## Fuse API

Fuse provide a bundle of API's to access and perform community-centric payments on the Fuse Network. Most of the API do require a economy set up on Fuse Studio.

* [Token API](token-api.md) - fetching economy tokens
* [Economy API](economy-api.md) - accessing and manipulating the economy details
* [Wallet API](wallet-api.md) - accessing and deploying user wallets
* [Jobs API](jobs-api.md) - task execution API
* [Admin API ](jobs-api.md)- performing community payments.
* [Trade API](trade-api.md) - trading tokens and executing swaps

### API Key

The API key is used to access the Fuse API without a limit. The API key is associated with the economy you created on Fuse Studio. it does not have to be stored secretly as it's not used for authentication but for the measuring API quotas and metrics.&#x20;

To use the API key you need to append it to any request in a form of the query parameter `apiKey={YOUR_KEY}`.  For example, the URL for fetching a community should look like:

`https://studio.fuse.io/api/v1/communities/:communityAddress?apiKey={YOUR_KEY}`



