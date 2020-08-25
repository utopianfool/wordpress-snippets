# Custom Shortcodes

Add custom shortcode to site. Requires the folloowing elements:

- html or php file with the template code, put in an 'inc' folder.
- shortcode function in functions.php.
- The '[shortcode]' to be used on the page.


## Create a shortcode.html file in the inc folder

```

<div class="post-signup-form">
    <h2>Find this article useful?</h2>
    <p>Get regular web design and development news updates, tips and resources delivered straight to your inbox</p>
    <form action="https://evolvedigital.us7.list-manage.com/subscribe/post?u=0cf2abe664672cb1aeabc9912&amp;id=b70ac4dc96" method="post" id="mc-embedded-subscribe-form" name="mc-embedded-subscribe-form" class="validate" target="_blank" novalidate>
        <div id="mc_embed_signup_scroll">
            <input type="email" value="" name="EMAIL" class="email" id="mce-EMAIL" placeholder="Email address" required>
            <div style="position: absolute; left: -5000px;" aria-hidden="true"><input type="text" name="b_0cf2abe664672cb1aeabc9912_b70ac4dc96" tabindex="-1" value=""></div>
            <div class="">
                <input type="submit" value="Subscribe" name="subscribe" id="mc-embedded-subscribe" class="button">
            </div>
        </div>
    </form>
</div>

```



## Add the function to call the shortcode in the functions.php file

```

/**
 * Add custom shortcode
 */
function mailchimp_shortcode() {
    require_once( __DIR__ . '/inc/shortcode-mailchimp.html');
}

add_shortcode('mailchimp', 'mailchimp_shortcode');

/* Here 'mailchimp' is used inside the shortcode like this [mailchimp] */


```


## Use the shortcode in the content

```
[mailchimp]
```