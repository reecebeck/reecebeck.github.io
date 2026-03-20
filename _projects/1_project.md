---
layout: page
title: EV Conversion Project
description: EV Drivetrain
img: assets/img/CANID.png
importance: 1
category: work
related_publications: true
---
<b>Project Overview: </b>

	Recently I began an internship in San Francisco, where myself and two other interns were hired to completely design the electrical drive system, as well as all infotainment and electronics for a custom electric vehicle from scratch. I took ownership of the drivetrain and power systems within the car - designing and building what we needed for an initial bench test of the project. 

<b>Bench test one: </b>

Parts used:
AEM VCU
Cascadia Motors iM225 Permanent magnet motor and inverter
AEM EV CCU (Combined Charging Unit)
8 Tesla Model 3 Battery units (Out of an optimistic 28 total)



<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid 
        loading="eager" 
        path="assets/img/Batteries.jpg" 
        title="example image" 
        class="img-fluid rounded z-depth-1" 
        style="max-width: 300px%}
    </div>
</div>


You can also put regular text between your rows of images, even citations {% cite einstein1950meaning %}.
Say you wanted to write a bit about your project before you posted the rest of the images.
You describe how you toiled, sweated, _bled_ for your project, and then... you reveal its glory in the next row of images.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    You can also have artistically styled 2/3 + 1/3 images, like these.
</div>

The code is simple.
Just wrap your images with `<div class="col-sm">` and place them inside `<div class="row">` (read more about the <a href="https://getbootstrap.com/docs/4.4/layout/grid/">Bootstrap Grid</a> system).
To make images responsive, add `img-fluid` class to each; for rounded corners and shadows use `rounded` and `z-depth-1` classes.
Here's the code for the last row of images above:

{% raw %}

```html
<div class="row justify-content-sm-center">
  <div class="col-sm-8 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm-4 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
```

{% endraw %}
