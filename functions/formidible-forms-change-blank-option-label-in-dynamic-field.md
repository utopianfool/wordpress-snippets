# Formidible Forms Change Blank Option Label in Dynamic Field

Add to functions file to change the blank option label in the dynamic field on a formidible form.

```
<?php

/**
 * Change the blank option label in Dynamic field
 */
add_filter('frm_setup_new_fields_vars', 'change_dynamic_blank_option', 25, 2);
function change_dynamic_blank_option($values, $field){
if ( in_array( $field->id, array( 91 ) ) ) {//Replace 100, 101, and 102 with the IDs of your Dynamic fields
    if ( empty( $values['options'] ) ) {
        return $values;
    }
        $values['options'][''] = 'Select a resource';
}
return $values;
}

?>
```