# Limit Countrtes and States

## Install on your BigCommerce store

Insert the script below to **Advanced Settings** > **Web Analytics**:

```html
<script>
    window.PAPATHEMES_LIMIT_COUNTRIES_SETTINGS = {
        supportedCountries: ['US', 'EG'],
        supportedCountryNames: ['United States', 'Egypt'],
        excludeStates: ['Alabama']
    };
</script>
<script src="//papathemes.com/content/supermarket/addon.limit-countries.js" async></script>
```

