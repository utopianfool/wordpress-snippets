# Enqueue Fonts

```
/**
 * Enqueue fonts
 *
 * @since WP_Base 1.0
 */
function google_fonts()
{
    $query_args = array(
        'family' => 'Open+Sans:300,400,400italic,700'
    );
    wp_enqueue_style('google-fonts', add_query_arg($query_args, "//fonts.googleapis.com/css"), array(), null);
}      
add_action('wp_enqueue_scripts', 'google_fonts');
```