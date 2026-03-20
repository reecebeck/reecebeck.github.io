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


The goal here was to get moving fast. We wanted to create an initial prototype as soon as possible with the parts we had, because many of what we’d need to order were backordered or faced long lead times. 
However, we were given a list of design goals which were far more lofty than the capabilities of the parts we had. The requested specs were incredible - long battery range (300mi+), 250kW fast charging, Tesla Plaid level horsepower, yet with technology from 2013, with 400V architecture. Regardless, we proceeded. 

Starting with a subset of 8 batteries, we aimed to get the motor spinning. To provide power to the motor, inverter precharge was required, a circuit designed to slowly charge the inverter’s internal capacitance to full battery voltage through an external resistance. This served multiple goals, mainly preserving the life of the main contactor by reducing the inrush current, but also protecting the inverter itself from extreme current surges. 

Insert photo of inverter precharge circuit

This system was controlled through the VCU, which was set up next. Initial configuration and tuning is achieved through a CAN link connected to a computer with AEM’s proprietary software. This process would be trivial, however the software AEMCAL(insert link) used for firmware configuration has numerous bugs, and has issues recognizing the CAN adapter device.

Next the inverter and VCU are connected through CAN, on CAN line 2 of the VCU. Both require external termination, and the inverter’s CAN baud rate must be adjusted to 500kHz through a dedicated serial connection. At this point the devices will begin to attempt to send CAN frames to each other. However, in plain configuration these will not be received by the VCU, as the CAN ID of the inverter, or the can ID of the VCU must be adjusted. In the VCU software AEM CAL, this can be done by setting the values equal to the following:




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
