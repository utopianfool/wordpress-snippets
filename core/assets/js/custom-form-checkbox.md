# Custom Form Checkbox

## jQuery

```

// Custom checkboxes
    $('.frm_checkbox input').on('click', function() {
        if ($(this).is(':checked')) {
            $(this).parent().addClass('checked');
        } else {
            $(this).parent().removeClass('checked');
        }
    });

```

## SCSS

```

.with_frm_style {
    form.frm_pro_form {
        .frm_opt_container {
            margin-top: 10px;
            .frm_checkbox {
                label {
                    position: relative;
                    padding-top: 3px;
                    padding-left: 30px;
                    text-indent: 0;
                    input[type="checkbox"] {
                        display: none;
                    }
                    &:before {
                        content: '';
                        position: absolute;
                        top: 8px;
                        left: 0;
                        width: 10px;
                        height: 10px;
                        border: 1px solid $site-grey;
                        border-radius: 0;
                        box-shadow: 1px -1px 0px $site-grey;
                    }
                    &.checked {
                        &:after {
                            content: '';
                            position: absolute;
                            top: 10px;
                            left: 2px;
                            width: 6px;
                            height: 6px;
                            background-color: $site-orange;
                        }
                    }
                    &:hover {
                        @include cursor(pointer);
                    }
                }
                & + .frm_checkbox {
                    margin-top: 7px;
                }
            }
        }
    }
}

```