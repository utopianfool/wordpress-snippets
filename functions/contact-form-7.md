# Contact Form 7

Edit default select box text on contact form 7.

```
/**
 * Contact Form 7 default select box text
 */
function cf7_dropdown_form($html)
{
    $text = __('SELECT', 'wpbase');
    $html = str_replace('---', $text, $html);
    return $html;
}
add_filter('wpcf7_form_elements', 'cf7_dropdown_form');
```