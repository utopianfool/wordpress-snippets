# HTML5 Reformat Telephone Numbers

```
/**
 * Reformat telephone numbers for use with HTML5 tel:
 */
function format_telephone_number($telephone)
{
    $reformattedTelephone = str_replace(array(' ', '(0)'), '', $telephone);
    return $reformattedTelephone;
}
```