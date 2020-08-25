# Advanced Custom Fields Responsive Images

This feature works great for any images within the standard WYSIWYG editor. The *srcset* and *sizes* attributes are added to each *img* tag to inform the browser of the available sizes for each image.

Add this to the function.php file for ACF responsive images.

```
/**
 * Responsive Image Helper Function
 *
 * @param string $image_id the id of the image (from ACF or similar)
 * @param string $image_size the size of the thumbnail image or custom image size
 * @param string $max_width the max width this image will be shown to build the sizes attribute 
 */

function awesome_acf_responsive_image($image_id,$image_size,$max_width){

    // check the image ID is not blank
    if($image_id != '') {

        // set the default src image size
        $image_src = wp_get_attachment_image_url( $image_id, $image_size );

        // set the srcset with various image sizes
        $image_srcset = wp_get_attachment_image_srcset( $image_id, $image_size );

        // generate the markup for the responsive image
        echo 'src="'.$image_src.'" srcset="'.$image_srcset.'" sizes="(max-width: '.$max_width.') 100vw, '.$max_width.'"';

    }
}
```

To use this within your custom theme, open an image tag, call the function and pass 3 parameters:

- The *image ID* (I’m getting this from an ACF image field which returns an ID)
- The *image size* (I’ve used a custom image size, added via the add_image_size )
- The *max width* (In this case the max width this image is 640px)

It will return the *src*, *srcset* and *sizes* attributes, you can assign your class and alt text as needed, see this example:

```
<img class="my_class" <?php awesome_acf_responsive_image(get_field( 'image_1' ),'thumb-640','640px'); ?>  alt="text" /> 

```

This will generate the responsive images markup, for all of the image sizes you have set (that have the same aspect ratio), similar to this:

```
<img class="my_class" 
src="http://aaronrutley.dev/wp-content/uploads/2015/10/wp-tips-640x150.jpg" 
srcset="http://aaronrutley.dev/wp-content/uploads/2015/10/wp-tips-320x75.jpg 320w, 
http://aaronrutley.dev/wp-content/uploads/2015/10/wp-tips-640x150.jpg 640w, 
http://aaronrutley.dev/wp-content/uploads/2015/10/wp-tips-1280x300.jpg 1280w, 
http://aaronrutley.dev/wp-content/uploads/2015/10/wp-tips-1920x450.jpg 1920w"
sizes="(max-width: 640px) 100vw, 640px" 
alt="text" >
```

In WordPress 4.4 max srcset size is set to 1600px wide by default, if you have images larger than that size that you’d like included in the srcset you can use this filter:

```
<?php
add_filter( 'max_srcset_image_width', 'awesome_acf_max_srcset_image_width', 10 , 2 );

// set the max image width 
function awesome_acf_max_srcset_image_width() {
    return 2200;
}

?>
```