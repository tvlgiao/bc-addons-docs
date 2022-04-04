# Multi Storefronts Global Login

This extension enables customers to register with one store, can login to all of your storefronts that are associated with the same account. The Multi-Storefronts feature is available only to Enterprise accounts. When installing the extension, your existing customer accounts have been also connected to all of your channels.

## Enable global logins on your stores

Create an API key for BC API access by following this instruction: https://support.bigcommerce.com/s/article/Store-API-Accounts#creating

- Choose **Create V2/V3 API Token**.
- In **Oauth Scopes** choose:
    - **Customers**: `modify`
    - **Customers Login**: `modify`
    - **Sites & Routes**: `read-only`
    - **Channel Settings**: `modify`
    - **Channel Listings**: `read-only`

Send us the Access Token code to install on your database.

Run the following script to install the extension:

`https://051ilzoi51.execute-api.us-east-1.amazonaws.com/latest/STOREHASH/jackgameroom/install-global-logins`

replace **STOREHASH** by your store hash code.

