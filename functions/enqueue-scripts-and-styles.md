# Enqueue Scripts and Styles

```
/**
 * Enqueue scripts and styles.
 *
 * @since WP_Base 1.0
 */
function wpbase_assets() {
    $debugMode = constant('WP_DEBUG');

    // Load theme styles
    $productionStyles = array(
        'core' => 'theme.min.css'
    );
    foreach ($productionStyles as $key => $css) {
        $path = dirname(__FILE__).'/css/'.$css;

        if (! $debugMode && file_exists($path)) {
            $asset = $css;
        } else {
            $asset = str_replace('.min', '', $css);
        }

        wp_enqueue_style('theme-styles-'.$key, get_template_directory_uri().'/css/'.$asset);
    }

    // Load theme scripts
    $productionScripts = array(
        'vendor' => 'vendor.min.js',
        'core' => 'theme.min.js'
    );
    foreach ($productionScripts as $key => $js) {
        $path = dirname(__FILE__).'/js/'.$js;

        if (! $debugMode && file_exists($path)) {
            $asset = $js;
        } else {
            $asset = str_replace('.min', '', $js);
        }

        wp_enqueue_script('theme-scripts-'.$key, get_template_directory_uri().'/js/'.$asset);
    }
}
add_action('wp_enqueue_scripts', 'wpbase_assets');
```