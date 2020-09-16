# Add Popup Functionality to Gallery

Use with Bootstrap and Ekko lightbox

```

/**
 * And popup functionality to gallery shortcode
 */
function gallery_pops($atts) {
    
    global $post;
    $pid = $post->ID;
    // Use IDs if set
    if (empty($pid)) {$pid = $post['ID'];}
    if (!empty( $atts['ids'] ) ) {
           $atts['orderby'] = 'post__in';
           $atts['include'] = $atts['ids'];
    }
    // Use columns attribute
    $columns = 5;
    if (!empty( $atts['columns'] ) ) {
        $columns = $atts['columns'];
    }
    $gallery = "";
    $gallery .= "<div class='gallery gallery-size-thumbnail gallery-columns-$columns'>";

    extract(shortcode_atts(array('orderby' => 'menu_order ASC, ID ASC', 'include' => '', 'id' => $pid, 'itemtag' => 'dl', 'icontag' => 'dt', 'captiontag' => 'dd', 'columns' => $columns, 'size' => 'large', 'link' => 'file'), $atts));
        
    $args = array('post_type' => 'attachment', 'post_status' => 'inherit', 'post_mime_type' => 'image', 'orderby' => $orderby);

    if (!empty($include)) {$args['include'] = $include;}
    else {
           $args['post_parent'] = $id;
        $args['numberposts'] = -1;
    }

    if ($args['include'] == "") { $args['orderby'] = 'date'; $args['order'] = 'asc';}

    $images = get_posts($args);
        
    foreach ( $images as $image ) {
        // print_r($image); /*see available fields*/
        $image_id = $image->ID;
        $thumbnail = wp_get_attachment_image_src($image_id, 'large');
        $thumbnail = $thumbnail[0];
        $figure_classes = "gallery-item"; 
        $image_alt = $image->alt;
        if( $image_alt == ''){
            $image_alt = $image->title;
        }
        $icon_classes = 'gallery-item-size';
        // Compile figure format
        $gallery .= "
            <figure class='".$figure_classes."' data-toggle='lightbox' data-gallery='gallery' data-remote='".$thumbnail."'>
                <div class='".$icon_classes."' style='background-image:url(".$thumbnail.");'>
                    <img class='img-fluid' src='".$thumbnail."' alt='".$image_alt."' />
                </div>
            </figure>";
    }
    $gallery .= '</div>';
    
    return $gallery;
}
// Remove standard shortcode and update with new format
remove_shortcode('gallery');
add_shortcode('gallery', 'gallery_pops');

```