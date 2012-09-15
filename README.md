MooProgressBar
==============

A simple Class for progress bars.

How to use
----------

````js
new MooProgressBar($('my_bar_container')); /* simple case */

new MooProgressBar($('my_bar_container2'),{ /* simple upload progress */
    range:654,
    unit:'kB',
    precision:2
});

/* Access the Instance via the element's storage */
$('my_bar_container2').retrieve('MooProgressBar').setValue(25);

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



### Events

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




### Methods

#### setValue

Set the current value of the bar

*signature*:
````js
setValue(value,no_anim)
````

*Arguments*:
- value - (*integer*) the new value
- no_anim - (*boolean*, defaults to false) don't animate, just set the value

#### getValue

Get the current value of the bar

*signature*:
````js
getValue()
````

#### setProgress

Set the current progress of the bar in percent

*signature*:
````js
setProgress(progress,no_anim)
````

*Arguments*:
- progress - (*integer*) the new progress
- no_anim - (*boolean*, defaults to false) don't animate, just set the progress


#### getProgress
Get the current value of the bar

*signature*:
````js
getProgress()
````

#### setLabel

Set the current progress of the bar in percent

*signature*:
````js
setLabel(text)
````

*Arguments*:
- text - (*string*) the new value for all labels




### Default HTML & CSS

For a good result, you can use, for example, the following HTML structure:
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