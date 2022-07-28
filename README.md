# Overview

Fuse API is an easy to use way to access and perform community-centric payments on the Fuse Network.

To start with an API please go to the [fuse studio](https://studio.fuse.io/), sign up and open your economy. Economy is what defines the payment model your community is using. For example you start with choosing a currency that your economy is going to use.

After onboarding and creating a community you can get:

* API key to start using various Fuse API's
* JWT to access the[ Admin API](fuse-api/admin-api.md)

## Fuse API

Fuse provide a bundle of API's to access and perform community-centric payments on the Fuse Network. Most of the API do require a economy set up on Fuse Studio.

* [Token API](fuse-api/token-api.md) - fetching economy tokens
* [Economy API](fuse-api/economy-api.md) - accessing and manipulating the economy details
* [Wallet API](fuse-api/wallet-api.md) - accessing and deploying user wallets
* [Jobs API](fuse-api/jobs-api.md) - task execution API
* [Admin API ](fuse-api/jobs-api.md)- performing community payments.
* [Trade API](fuse-api/trade-api.md) - trading tokens and executing swaps

### API Key

The API key is used to access the Fuse API without a limit. The API key is associated with the economy you created on Fuse Studio. The key can be stored either on the client and server side, and does not need to be secured as its not used for authorization but merely for measurement  on quotas and metrics.

To use the API key you need to append it to any request in a form of the query parameter `apiKey={YOUR_KEY}`.  For example, the URL for fetching a community should look like:

`https://studio.fuse.io/api/v1/communities/:communityAddress?apiKey={YOUR_KEY}`



### JWT token

Admin JWT key used to control the economy and its a token. The admin API provides a simple way to perform crypto payments without diving in into the web3 technology stack.&#x20;

The JWT key should be stored in a secure way on your servers, and is used for backend to backend communication. Do not share the admin JWT with the client application (web or mobile).
