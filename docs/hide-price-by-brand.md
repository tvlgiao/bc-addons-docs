# Hide product prices based on specific brands

This extension allows to hide product prices, add to cart and checkout buttons based on specific brands. Editing theme files is required.

Source Code: https://github.com/tvlgiao/brand-based-hide-prices-cornerstone-gloantiagingshop

## Installation

1. Edit the theme files.

2. Edit file `components/papathemes/hide-prices/head.html`, update the brand names for products to hide:

```handlebars
{{assignVar 'hidePriceBrands' 'Brand Name 1,Brand Name 2'}}
```


