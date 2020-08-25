# Formidible Forms Populate Dropdowns From Post

Add to function file to populate dropdown menus in formidible forms from custom post types

```
<?php

/**
 * Formidable - Populate dropdown field with WordPress Post
 * https://formidableforms.com/knowledgebase/frm_setup_new_fields_vars/
 */
add_filter('frm_setup_new_fields_vars', 'frm_populate_posts', 20, 2);
add_filter('frm_setup_edit_fields_vars', 'frm_populate_posts', 20, 2); //use this function on edit too
function frm_populate_posts($values, $field){
  if($field->id == 91){ //replace this ID with the ID of the field to populate
    $posts = get_posts( array(
        'post_type' => 'resources', 
        'post_status' => array(
            'publish', 
            'private'
        ), 
        'numberposts' => 999,
        'orderby' => 'title',
        'order' => 'ASC')
);
    unset($values['options']);
    $values['options'] = array(''); //remove this line if you are using a checkbox or radio button field
    $values['options'][''] = ''; //remove this line if you are using a checkbox or radio button field
    foreach($posts as $p){
      $values['options'][$p->ID] = $p->post_title;
  }
    $values['use_key'] = true; //this will set the field to save the post ID instead of post title
    unset($values['options'][0]);
}
return $values;
}

?>

```