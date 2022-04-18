# Shipping Countdown

## Installation

Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `Store Pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**: 

```html
<script>
    window.PapathemesShippingCountdownSettings = {
        storeTZ = 'America/Mexico_City',
    };
</script>
<script src="https://d3r059eq9mm6jz.cloudfront.net/microapps/shipping-countdown/main.YOURDOMAIN.js" async defer></script>
```

Replace `YOURDOMAIN` by your store's domain name, for example `imrbatteries.com`. The complete URL should look like `https://d3r059eq9mm6jz.cloudfront.net/microapps/shipping-countdown/main.imrbatteries.com.js`


Add a HTML widget in the product page with the content below:

```html
<div
    data-papathemes-shipping-countdown="12:00:00"
    data-hour-text="Hr"
    data-hours-text="Hrs"
    data-minute-text="Min"
    data-minutes-text="Mins"
    style="display:none">
    <div data-today-hm>In Stock & Ready To Ship!<br/>Order In The Next <strong>%HOUR%</strong> and <strong>%MINUTE%</strong> to ship today.</div>
    <div data-today-m>In Stock & Ready To Ship!<br/>Order In The Next <strong>%MINUTE%</strong> to ship today.</div>
    <div data-tomorrow-hm>In Stock & Ready To Ship!<br/>Order In The Next <strong>%HOUR%</strong> and <strong>%MINUTE%</strong> to ship tomorrow.</div>
    <div data-tomorrow-m>In Stock & Ready To Ship!<br/>Order In The Next <strong>%MINUTE%</strong> to ship tomorrow.</div>
    <div data-monday>In Stock & Ready To Ship!<br/>Order now to ship Monday.</div>
    <div data-custom></div>
</div>
```

### Custom CSS

```html
<script>
    (function() {
        var style = document.createElement('style');
        style.innerHTML = `
            [data-papathemes-shipping-countdown] {
                padding: .75rem;
                background-color: #fff;
                order: 26; /* below bulk pricing for Chiara theme */
            }
            @media (min-width: 801px) {
                width: 50%;
                float: right;
                clear: right;
                padding: .75rem 1.5rem;
            }
        `;
        document.head.appendChild(style);
    })();
</script>
```

## Configuration

```html
<script>
    window.PapathemesShippingCountdownSettings = {
        countdownSelector = [data-papathemes-shipping-countdown]',
        debug = false,
        graphQLToken = '{{{settings.storefront_api.token}}}',
        storeTZ = 'America/Mexico_City',
        checkMetaField = false,
        countdownValues = {
            parcel: '15:00:00',
            LTL: '12:00:00',
        },
        defaultCountdownTime = '12:00:00', // use this value if checkMetafield = false or data-papathemes-shipping-countdown = empty
        findProductIdFunc = ($scope) => Number($scope.closest('.productView').find('form[data-cart-item-add] input[name="product_id"]').val()),
    };
</script>
```



