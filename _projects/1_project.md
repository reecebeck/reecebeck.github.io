---
layout: page
title: EV Conversion Project
description: EV Drivetrain
img: assets/img/CANID.png
importance: 1
category: work
---
<strong>Project Overview: </strong>

Recently I began an internship in San Francisco where myself and two other interns were hired to completely design the electrical drive system, infotainment, and electronics for a custom electric vehicle. I took ownership of the drivetrain and power systems within the car - designing and building what we needed for an initial bench test of the project.


<strong>Bench test one: </strong>

Parts used:

- AEM VCU
- Cascadia Motors iM225 Permanent magnet motor and inverter
- AEM EV CCU (Combined Charging Unit)
- 6 Tesla Model 3 Battery units (Out of an optimistic 28 total)



<div class="row">
<div style="max-width: 550px; margin: 0 auto;">
    <div class="col-sm mt-3 mt-md-0">
       {% include figure.liquid 
   loading='eager' 
   path='assets/img/Batteries.jpg' 
   title='example image' 
   class='img-fluid rounded z-dep   th-1' 
%}
    </div>
    </div>
</div>
<div class="caption"> </div>

The goal here was to get moving fast. We wanted to create an initial prototype as soon as possible with the parts we had, because many of what we’d need to order were backordered or faced long lead times. 
However, we joined this project after the initial planning stage, and many of the parts initially ordered were not inline with the given design goals. Mainly, the parts we had were designed for a 400V architecture, but a modern EV with >150kW fast charging uses an 800V system. This would later give us more difficulty regarding battery capacity.  
 
Starting with a subset of 6 batteries, we aimed to get the motor spinning. To provide power to the motor, inverter precharge was required, a circuit designed to slowly charge the inverter’s internal capacitance to full battery voltage through an external resistance. This served multiple goals, mainly preserving the life of the main contactor by reducing the inrush current, but also protecting the inverter itself from extreme current surges. I built a simple precharge circuit to perform this function - it works using a smaller contactor to switch the pack voltage through a series resistor, until high voltage is detected in the inverter, at which point it shuts off and the main contactor closes.  

Insert photo of inverter precharge circuit

This system is controlled through the VCU, which was set up next. Initial configuration and tuning is achieved through a CAN link connected to a computer with AEM’s proprietary software. This process would be trivial, however the software AEMCAL(insert link) used for firmware configuration has numerous bugs, and has issues recognizing the CAN adapter device.

Next the inverter and VCU are connected through CAN, on CAN line 2 of the VCU. Both require external termination, and the inverter’s CAN baud rate must be adjusted to 500kHz through a dedicated serial connection. At this point the devices will begin to attempt to send CAN frames to each other. However, in plain configuration these will not be received by the VCU, as the CAN ID of the inverter, or the can ID of the VCU must be adjusted. In the VCU software AEMCAL, this can be done by setting the values equal to the following:

<div class="row">
<div style="max-width: 700px; margin: 0 auto;">
    <div class="col-sm mt-3 mt-md-0">
       {% include figure.liquid 
   loading='eager' 
   path='assets/img/CANID.png' 
   title='example image' 
   class='img-fluid rounded z-depth-1' 
%}
    </div>
    </div>
</div>
At this point, the devices should communicate successfully. This allows for commands to be sent between the devices, such as temperature readings or even torque request commands. 

We quickly added an accelerator pedal from a Tesla Model 3, and implemented a 3 position switch as a gear selector, providing sufficient inputs for the VCU to provide torque request commands to the motor. This marked completion of the first phase of the project - our VCU and motor successfully functioned together. 

<b>Bench test two, further goals:</b>

Coming back to the initial goals of the project - a high performance, long range, fast charging EV, we conducted a design review. Our bench test functioned well, and would scale up to full size properly with a full set of batteries. However, questions remained, namely with the desired specifications of the original build. During this project's conception, two Tesla vehicles were salvaged for their battery packs, and all were to be used for the benefit of added range. However, this came with technical challenges - the motor-inverter package that was purchased could support a max voltage of 480V, yet the complete use of two full Tesla batteries would put the pack voltage beyond 700V, far too high for our equipment. Additionally, 250kW fast charging requires a system voltage of 800V, and currently no consumer equipment exists for this build. Clearly the scope of this project had to be adjusted. 



