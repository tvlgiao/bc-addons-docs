# Fractional Quantity & Unit Labels

The Fractional Quantity & Unit Labels extension enables the display and adjustment of product quantities in fractional increments, such as 0.5, 1, 1.5, 2, 2.5, and so on. Additionally, it allows for customization of unit price labels, like "Yards." Users can configure both the unit price label and fractional quantity increments for individual products through custom product fields. This extension is easily installed via the Script Manager without the need to modify theme files and is compatible with all BigCommerce themes.

Please note that this extension is specifically designed for the **Supermarket** theme. If the merchant is using a different theme, our developer may need to modify some CSS code and configuration settings to ensure proper compatibility with their custom theme.

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
        fractionUnitCustomField: '__unit',
        fractionUnitLabelCustomField: '__unit_label'
    }
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/microapps/customizations/gstreetfabrics/main.js" async defer></script>
```

Edit your product:

- Add a custom field named `__unit` with a value representing the fractional quantity number (e.g., `0.5`).
- Add a custom field named `__unit_label` with a value representing the unit price label (e.g., `Yards`).



## DEV ONLY

GitHub: https://github.com/tvlgiao/bc-bigcommerce-api-app/microapps/customizations/gstreetfabrics

### Run the script in development mode:

```bash
cd microapps/customizations
npm i
npm run dev --domain=gstreetfabrics
```

Edit the `base.html` file of the theme and add the following code below the `{{{footer.script}}}` line:

```html
<script>
    window.PapathemesCustomSettings = {
        graphQLToken: '{{{settings.storefront_api.token}}}'
    }
</script>
<script src="http://localhost:9000/gstreetfabrics/main.js" async defer></script>
```

Edit a product:

- Add a custom field named `__unit` with a value representing the fractional quantity number (e.g., `0.5`).
- Add a custom field named `__unit_label` with a value representing the unit price label (e.g., `Yards`).


After making these changes, test the product quantity box of the edited product to ensure proper functionality.



### Deploy the script to production server

```bash
npm run deploy --domain=gstreetfabrics
```

