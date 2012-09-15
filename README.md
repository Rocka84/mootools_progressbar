MooProgressBar
==============

A simple Class for progress bars.

How to use
----------

Use the following HTML structure:
````html
<div class="progressbar">                          <!-- Main container -->
    <div class="progressbar_inner">                <!-- The bar, this is resized -->
        <div class="progressbar_label"></div>      <!-- The bottom label -->
        <div class="progressbar_bg">               <!-- The bar background, this is what you see growing -->
            <div class="progressbar_label"></div>  <!-- The top label -->
        </div>
    </div>
</div>
````

add some css:
````css
.progressbar{
    width:160px;
    height:24px;
    border:1px solid black;
    overflow:hidden;
    white-space:nowrap;
    font-size:small;
    text-align:center;
    line-height:24px;
    display:inline-block;
}
.progressbar_inner{
    width:0;
    height:100%;
    position:relative; /* This is important! */
}
/* The visual bar */
.progressbar_bg{
    position:absolute;
    top:0;
    width:100%;
    height:100%;
    background-color:darkcyan;
    overflow:hidden
}
/* The labels */
.progressbar_label{
    position:relative;
    width:100%;
    overflow:visible;
    padding:0 4px;
}
/* The bottom label */
.progressbar_inner > .progressbar_label{
    color:black;
}
/* The top label */
.progressbar_bg > .progressbar_label{
    color:white;
}
````

and initalize the bars like this:
````js
new MooProgressBar($('bar1')); /* simple case */

new MooProgressBar($('bar2'),{ /* simple upload progress */
    range:654,
    unit:'kB',
    precision:2
});
````

### Options

- range - (*array*, defaults to [0,100]) range of the bar
- start - (*integer*, defaults to 0)  initial value
- unit - (*string*, defaults to '%')  unit of the values
- precision - (*integer*, defaults to 0)  precision for presenting values
- effect_duration - (*integer*, defaults to 200)  duration of the grow effect
- tween_property - (*string*, defaults to 'width')  experimental
- inner_class - (*string*, defaults to 'progressbar_inner')  the class to select the inner bar
- label_class - (*string*, defaults to 'progressbar_label')  the class to select the label elements
- getLabel - (*function*, see default below) function to format the text for the label

The getLabel option defaults to:
````js
function(progress, value, unit, precision){
    if (unit=='%'){
        return progress.toFixed(parseInt(precision))+unit;
    }else{
        return value.toFixed(parseInt(precision))+unit;
    }
}
````

### Events:

#### onProgress

Will fire when the progress property was changed

*signature*:
````js
onProgress(progress,value,unit,precision)
````

#### onComplete

Will fire when the progress reached 100%

*signature*:
````js
onComplete(value,unit,precision)
````
