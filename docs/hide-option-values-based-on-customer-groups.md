# Hide Product Option Values based on Customer Groups

## Install the script to your store

```html
<script>
    window.ZACATAKLURES_HIDEOPTIONS = {
        rules: [
            {
                options: [
                    {
                        name: 'Size',
                        value: 'Extra Small',
                    },
                    {
                        name: 'Size',
                        value: 'Extra Large'
                    },
                    {
                        name: 'Size',
                        value: 'Monster',
                    },
                    {
                        name: 'Head Type',
                        value: 'Soft Skull'
                    },
                    {
                        name: 'Rigging Option',
                        value: 'Twin Hook Shackle Rig - Mustad 7691S'
                    }
                ],
                customerGroups: [
                    // 'Guests',
                    'Dealer Australia',
                    'Dealer International'
                ]
            }
        ],
        customerGroupName: '{{{customer_group_name}}}',
        graphQLToken: '{{{settings.storefront_api.token}}}',
        debug: true
    };
</script>
```

- GitHub (new): https://github.com/tvlgiao/bigcommerce-api-app/tree/master/microapps/hide-product-option
- GitHub: https://github.com/tvlgiao/bc-zacataklures-chiara-hide-product-options


## Installation for strideanimalhealth.com

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `Store Pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**:


```html
<script>
window.PapathemesHideProductOptionSettings = {
    rules = [
        {
            options: [
                {
                    name: 'Order Frequency',
                    value: 'One Time Purchase',
                },
                {
                    name: 'Order Frequency',
                    value: 'Subscribe & Save',
                },
                {
                    name: 'Ships Every',
                    value: 'Ships Every (2-8 weeks)'
                },
                {
                    name: 'Ships Every',
                    value: 'Ships Every (1-3 months)',
                },
            ],
            customerGroups: [
                'Veterinarian',
                'BB Dealer',
                'STRIDE DEALER',
                'APC - Lifeline only @ dealer cost',
            ]
        },
    ],
    customerGroupName: '{{customer.customer_group_name}}',
    graphQLToken: '{{settings.storefront_api.token}}',
};
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/microapps/hide-product-option/main.strideanimalhealth.com.js" async defer></script>
```
