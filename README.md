MooProgressBar
===========

A simple Class for progress bars.

How to use
----------

Use the following HTML structure:
```html
    &lt;div class="progressbar"&gt;                          &lt;!-- Main container --&gt;
        &lt;div class="progressbar_inner"&gt;                &lt;!-- The bar, this is resized --&gt;
            &lt;div class="progressbar_label"&gt;&lt;/div&gt;      &lt;!-- The bottom label --&gt;
            &lt;div class="progressbar_bg"&gt;               &lt;!-- The bar background, this is what you see growing --&gt;
                &lt;div class="progressbar_label"&gt;&lt;/div&gt;  &lt;!-- The top label --&gt;
            &lt;/div&gt;
        &lt;/div&gt;
    &lt;/div&gt;
```

and initalize the bars like this:
```js
    new MooProgressBar($('bar1')); /* simple case */

    /* See this Example for all options with their default values */
    new MooProgressBar($('bar2'),{
        range:[0,100],          // range of the bar
        start:0,                // initial value
        unit:'%',               // unit of the values
        precision:0,            // precision for presenting values
        effect_duration:200,    // duration of the grow effect
        tween_property:'width', // experimental
        
        // function to format the text for the label
        getLabel:function(progress, value, unit, precision){
            if (unit=='%'){
                return progress.toFixed(parseInt(precision))+unit;
            }else{
                return value.toFixed(parseInt(precision))+unit;
            }
        }
    });
```

Events
- progress: function(progress,value,unit,precision)
- complete: function(value,unit,precision)
