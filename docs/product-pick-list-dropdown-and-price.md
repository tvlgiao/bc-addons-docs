# Product Pick List Dropdown and Price

This extension provides you with the ability to showcase pricing for each product picklist item, offering a clear and detailed perspective for your customers. Additionally, it allows you to convert the product picklist into a dropdown format for a more streamlined and user-friendly interface. This helps to enhance customer experience on your site, promoting better understanding of your product offerings and potentially increasing conversions.

![Product Pick List Dropdown and Price](img/product-picklist-dropdown-price.png)

Demo Link: https://globalfuelingsystems.com/piusi-f0059423c-cube-70mc-1-0-120v-15-gpm-fuel-management-system/

## Installation

Navigate to **Storefront** > **Script Manager** and click **Create a Script**. Choose the following options:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `Store Pages`
- **Script type** = `Script`

Enter the script below into the **Script contents** section:

```html
<script>
    window.PapathemesCustomSettings = {
        graphQLToken: '{{{settings.storefront_api.token}}}',
        currencyCode: '{{currency_selector.active_currency_code}}',
        rules: [
        // {
        //     productIds = [],
        //     options: ['Software Version'],
        // },
        ],
        transformToDropdown: true,
    }
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/microapps/customizations/globalfuelingsystems.com/main.js" async defer></script>
```
