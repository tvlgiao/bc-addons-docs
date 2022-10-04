# Tooltips for Product Options

## Install tooltips for product options

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `Store pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**:

```html
<script>
    window.PapaThemesProductOptionTooltipSettings = {
        tooltips: [
            {
                optionName: 'Back',
                tooltip: 'Duct Size (Face Size) - Measure the size of the duct opening - NOT the size of the exisitng vent cover -Includes Mounting Clips for Wall Installations'
            },
            {
                optionName: 'Karat',
                tooltipHtml: 'Select the <b>Species of Wood</b> (Unfinished and Factory Sanded)'
            }
        ]
    };
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/microapps/product-option-tooltip/main.YOURDOMAIN.js" async defer></script>
```

Replace `YOURDOMAIN` by your store's domain name, for example: `imrbatteries.com`, the complete URL is `https://d3r059eq9mm6jz.cloudfront.net/microapps/product-option-tooltip/main.imrbatteries.com.js`.

## Install tooltips for product options and the faceted filters

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `Store pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**:

```html
<script>
    window.PapaThemesProductOptionTooltipSettings = {
        scopeSelector: '[data-product-option-change], #facetedSearch',
        labelSelector: '[data-product-attribute] label:first-child, .accordion-title',
        tooltips: [
            {
                optionName: 'Back',
                tooltip: 'Duct Size (Face Size) - Measure the size of the duct opening - NOT the size of the exisitng vent cover -Includes Mounting Clips for Wall Installations'
            },
            {
                optionName: 'Karat',
                tooltip: 'Select the Species of Wood (Unfinished and Factory Sanded)'
            },
            {
                optionName: 'Brand',
                tooltip: 'Temporibus aspernatur vero assumenda qui nostrum molestias dignissimos et.'
            },
            {
                optionName: 'Color',
                tooltip: 'Non debitis fuga reprehenderit nisi vel.'
            }
        ]
    };
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/microapps/product-option-tooltip/main.YOURDOMAIN.js" async defer></script>
```

- Replace `YOURDOMAIN` by your store's domain name, for example: `imrbatteries.com`, the complete URL is `https://d3r059eq9mm6jz.cloudfront.net/microapps/product-option-tooltip/main.imrbatteries.com.js`.
- Edit `optionName` and `tooltip` variables to reflect your actual product option name / filter name and tooltip content.


## Source Code (Not Published)

- Git: https://github.com/tvlgiao/bc-bigcommerce-api-app/microapps/product-option-tooltip/

