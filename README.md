MooProgressBar
===========

A simple Class for progress bars.

How to use
----------

Use the following HTML structure:
```html
    <div class="progressbar">                          <!-- Main container -->
        <div class="progressbar_inner">                <!-- The bar, this is resized -->
            <div class="progressbar_label"></div>      <!-- The bottom label -->
            <div class="progressbar_bg">               <!-- The bar background, this is what you see growing -->
                <div class="progressbar_label"></div>  <!-- The top label -->
            </div>
        </div>
    </div>
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
