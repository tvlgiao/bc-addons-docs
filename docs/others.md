# Other Scripts

## (UNFINSHED !!!) Hide Add to Cart when product is low stock 

Display Out of Stock message and hide Add to Cart button when product is low stock.


Go to **Storefront** > **Script Manager**, click **Create a Script**, choose:

- **Location on page** = `Footer`
- **Select pages where script will be added** = `All Pages`
- **Script type** = `Script`

Enter the script below to **Scripts contents**:

```html
<script>
(function($) {
    /** debounce(func, wait, immediate) */
    function debounce(n,t,u){var e;return function(){var i=this,o=arguments,a=u&&!e;clearTimeout(e),e=setTimeout(function(){e=null,u||n.apply(i,o)},t),a&&n.apply(i,o)}}

    function css() {
        var style = document.createElement('style');
        style.innerHTML = '#form-action-addToCart:not(.show) { display: none }';
        document.head.appendChild(style);
    }

    function main() {
        $('#form-action-addToCart').addClass('show');

        $('[data-product-stock]').each(function(i, el) {
            var $el = $(el);
            var $form = $el.closest('form');
            var $btn = $form.find('#form-action-addToCart').hide();

            $btn.parent().append('<div class="alertBox">Out of Stock</div>');
            $btn.remove();
            $form.attr('action', '').off('submit');
            $el.closest('.form-field--stock').remove();
        });
    }

    $(document).ready(function() {
        css();
        main();
        (new MutationObserver(debounce(main, 300))).observe(document.body, { subtree: true, childList: true });
    })
})(window.chiarajQuery);
</script>
```
