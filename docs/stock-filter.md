# Stock Filter

Display In Stock / Out of Stock filter on category pages and search pages.

## Install on your BigCommerce Store

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `Store Pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 


```html
<script>
    window.PapathemesStockFilterSettings = {
        debug: true,
        storeHash: "{{settings.store_hash}}",
        graphQLToken: "{{settings.storefront_api.token}}",
        currencyCode: "{{currency_selector.active_currency_code}}",
        restrictToLogin: {{default theme_settings.restrict_to_login false}},
        customerId: {{default customer.id 0}},
        showProductRating: {{default settings.show_product_rating false}},
        card_show_border: {{default theme_settings.card_show_border false}},
        card_show_button: {{default theme_settings.card_show_button false}},
        show_product_quick_view: {{default theme_settings.show_product_quick_view false}},
        show_product_quantity_box: {{default theme_settings.show_product_quantity_box false}},
        show_sku: {{default theme_settings.show_sku false}},
        show_compare: {{default category.show_compare false}},
        card_show_swatches: {{default theme_settings.card_show_swatches false}},
        ajax_add_to_cart: {{default theme_settings.ajax_add_to_cart false}},
        product_sale_badges: "{{default theme_settings.product_sale_badges 'label'}}",
        product_sale_label: "{{default theme_settings.product_sale_label 'Sale'}}",
        product_custom_badges: {{default theme_settings.product_custom_badges false}},
        categoryId: "{{category.id}}",
        defaultSortBy: "{{pagination.category.sort}}",
        defaultLimit: "{{theme_settings.categorypage_products_per_page}}"
    };
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/microapps/stock-filter/main.YOURDOMAIN.js" async defer></script>
```

Replace `YOURDOMAIN` by your domain name. For example: `example.com`.

Create and send us a v2/v3 API token wth OAuth Scopes:

- **Products** = `Read Only`
- **Information & settings** = `Read Only`
- **Sites & Routes** = `Ready Only`
- **Channel settings** = `Read Only`
- **Channel listings** = `Read Only`

<!--
Source code: https://github.com/tvlgiao/bc-bigcommerce-api-app/microapps/stock-filter/
-->

