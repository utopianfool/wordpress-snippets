#Tiny MCE

Insert into functions.php for Tiny MCE options, custom stylesheet and plain text by default, plus add core buttons.

- [Activate Tiny MCE Options](#activate-tiny-mce-options)
- [Tiny MCE Custom Stylesheet](#tiny-mce-custom-stylesheet)
- [Tiny MCE Plain Text by Default](#tiny-mce-plain-text-by-default)
- [Show Custom Styles in Format Dropdown](#show-custom-styles-in-format-dropdown)
- [Add Core Buttons Disabled by Default](#add-core-buttons-disabled-by-default)

## Activate Tiny MCE Options
Activate TinyMCE style drop down. Add style selector to the beginning of the toolbar. Remove the format dropdown select and text color selector and define the style_formats array.
```
/**
 * Tiny MCE
 *
 * EXAMPLES of 'format' dropdown. Tiny MCE documentation is execrable. Try https://codex.wordpress.org/TinyMCE_Custom_Styles and http://www.thecoolagency.com/blog/wordpress/add-hidden-mce-buttons-functions-php/
 */

// Activate TinyMCE style drop down
function myplugin_tinymce_buttons($buttons)
{
    // Add style selector to the beginning of the toolbar
    array_unshift($buttons, 'styleselect');

    // Remove the format dropdown select and text color selector
    $remove = array('formatselect','forecolor');

    return array_diff($buttons, $remove);
}
add_filter('mce_buttons_2','myplugin_tinymce_buttons');

// Setup TinyMCE style drop down options
function my_mce_before_init_insert_formats($init_array)
{
    // Define the style_formats array
    $style_formats = array(  
        // Each array child is a format with it's own settings  
        array(
            'title' => __('Page Heading', 'wpbase'),
            'block' => 'h1',
            'wrapper' => false,
        ),
        array(
            'title' => __('Page Subheading', 'wpbase'),
            'block' => 'h2',
            'wrapper' => false,
        ),
        array(
            'title' => __('Article Heading', 'wpbase'),
            'block' => 'h3',
            'wrapper' => false,
        ),
        array(
            'title' => __('Article Subheading', 'wpbase'),
            'block' => 'h4',
            'wrapper' => false,
        ),
        array(
            'title' => __('Paragraph', 'wpbase'),
            'block' => 'p',
            'wrapper' => false,
        ),
        array(
            'title' => __('Lead Text', 'wpbase'),
            'block' => 'p',
            'classes' => 'lead-text',
            'wrapper' => false,
        ),
        /*
        array(
            'title' => 'Button',
            'selector' => 'a',
            'classes' => 'btn btn-primary',
            'wrapper' => false,
        ),
        */
    );  
    // Insert the array, JSON ENCODED, into 'style_formats'
    $init_array['style_formats'] = json_encode( $style_formats );   
    return $init_array;  
} 
add_filter('tiny_mce_before_init', 'my_mce_before_init_insert_formats');
```

## Tiny MCE Custom Stylesheet
```
/**
 * Locate TinyMCE custom stylesheet
 */
if (! constant('WP_DEBUG') && file_exists(dirname(__FILE__).'/css/theme-editor.min.css')) {
    $themeEditorStyles = 'theme-editor.min.css';
} else {
    $themeEditorStyles = 'theme-editor.css';
}
add_editor_style(get_template_directory_uri().'/css/'.$themeEditorStyles);
```

## Tiny MCE Plain Text by Default
```
/**
 * Activate TinyMCE paste as plain text by default
 */
function tinymce_paste_as_text($init)
{
    $init['paste_text_use_dialog'] = false;
    $init['paste_as_text'] = true;
    return $init;
}
add_filter('tiny_mce_before_init', 'tinymce_paste_as_text');
```

## Show Custom Styles in Format Dropdown
```
/**
 * Unset the default preview styles so custom styles show in format dropdown
 */
function fb_mce_before_init($settings)
{
    unset($settings['preview_styles']);
    return $settings;
}
add_filter('tiny_mce_before_init', 'fb_mce_before_init');
```

## Add Core Buttons Disabled by Default
```
/**
* Add in core buttons that are disabled by default
*/
function my_mce_buttons_2($buttons) {   
    $buttons[] = 'superscript';
    $buttons[] = 'subscript';

    return $buttons;
}
add_filter('mce_buttons_2', 'my_mce_buttons_2');
```