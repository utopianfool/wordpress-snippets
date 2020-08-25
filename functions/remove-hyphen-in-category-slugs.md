# Remove Hyphen in Category Slugs

Add to functions.php to remove hyphen in category slugs for use in landing pages.

```
/**
 * Function to get rid of '-' in Category
 * slugs, for use in Landing Page Templates.
 *
 * @param string $string
 */
function stringNoHyphens($string)
{
    $toFormat = $string;
    $toFormat = str_replace('-', ' ', $toFormat);
    return $toFormat;
}
```