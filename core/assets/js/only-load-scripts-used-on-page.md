# Only Load Scripts Used on Page

Add this javascript to the footer and main.js then add a div with the id that is referenced in the functions to only load the scripts on the pages they are needed and not every page.

## Add to footer of site

```
<script>
    // Only load scripts that are used on the page
    window.templateDirectory = "<?php echo get_template_directory_uri(); ?>";
</script>
```

## Add div to page where the script is going to run

```
<div id="triangles"></div>
```

## Add to main.js

```
// Initialise animated Triangles on the Homepage
if($('#triangles').length){
    injectScriptAndRunCallback(
        // main script to run
        'js/triangles.js',
        function(){
            injectScriptAndRunCallback(
                // dependancies for the script to run
                'js/fss.js',
                function(){
                    triangles()
                }
            )
        }
    );
}

// This part does not change
function injectScriptAndRunCallback(source, callback){
    (function(d, script) {
        script = d.createElement('script');
        script.type = 'text/javascript';
        script.async = true;
        script.onload = function(){
            callback();
        };
        script.src = window.templateDirectory + '/' + source;
        d.getElementsByTagName('head')[0].appendChild(script);
    }(document));
}
```

