# Hide Product Option Values based on Customer Groups

Example configuration:

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

GitHub: https://github.com/tvlgiao/bc-zacataklures-chiara-hide-product-options


