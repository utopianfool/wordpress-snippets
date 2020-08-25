# Format Anchor Link String

```
/**
 * Format anchor link string
 *
 * @param  string          $string
 * @param  boolean|string  $includeHash
 *
 * @return string
 */
function formatAnchorLink($string, $includeHash = false)
{
    $sanitizedString = filter_var($string, FILTER_SANITIZE_STRING, FILTER_FLAG_STRIP_LOW | FILTER_FLAG_STRIP_HIGH);
    $rewrittenString = str_replace(array('&amp;', '&'), array('and', 'and'), $sanitizedString);
    $anchorString = strtolower($rewrittenString);

    return ($includeHash ? '#'.$anchorString : $anchorString);
}
```