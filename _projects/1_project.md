---
layout: page
title: EV Conversion Project
description: EV Drivetrain
img: assets/img/IMG_1002.jpg
importance: 1
category: All
---
<strong>Project Overview: </strong>

Recently I began an internship in San Francisco where I was brought on to design and implement the drivetrain and battery systems of a completely custom electric vehicle. These electronics were to go on the frame of a 1960s Toyota FJ truck, completely retrofitted for the project.

The original design goals were similar to top EVs in the market - 300+ mile range, 250kW fast charging, and a dual motor drive system. Before these systems were to go in the final car, I built a full test bench to evaluate their performance and plan all electronics. From that point, with a finalized electrical layout, I would then translate it into a complete electrical plan and wiring harness for the car.


<strong>Bench test one: </strong>

Parts used:

- AEM VCU
- Cascadia Motors iM225 Permanent magnet motor and inverter
- AEM EV CCU (Combined Charging Unit)
- 6 Tesla Model 3 Battery units (Out of 28 total)



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
<div class="caption"> Figure 1: The original Tesla battery modules</div>

The goal here was to get moving fast. I wanted to create an initial prototype as soon as possible with the parts we had, because many of what I’d need to order was backordered or faced long lead times. 
However, I joined this project after the initial planning stage, and many of the parts initially ordered were not inline with the given design goals. Mainly, the parts we had were designed for a 480V architecture, but a modern EV with >150kW fast charging uses an 800V system. Additionally, the 480V architecture limited us in terms of battery capacity, because only a limited amount could be placed in series before reaching the max voltage.

Starting with a subset of 6 batteries for simplicity, I aimed to get the motor spinning. To provide power to the motor, inverter precharge was required, a circuit designed to slowly charge the inverter’s internal capacitance to full battery voltage through an external resistance. This served multiple goals, mainly preserving the life of the main contactor by reducing the inrush current, but also protecting the inverter itself from extreme current surges. I built a simple precharge circuit to perform this function - it works using a smaller contactor to switch the pack voltage through a series resistor, until high voltage is detected in the inverter, at which point it shuts off and the main contactor closes.
  

Insert photo of inverter precharge circuit

This system is controlled through the VCU, which was set up next. Initial configuration and tuning is achieved through a CAN link connected to a computer with AEM’s proprietary software. This process would be trivial, however the software AEMCAL(insert link) used for firmware configuration has numerous bugs, and has issues recognizing the CAN adapter device.

Next the inverter and VCU are connected through CAN, on CAN line 2 of the VCU. Both require external termination, and the inverter’s CAN baud rate must be adjusted to 500kHz through a dedicated serial connection. At this point the devices will begin to attempt to send CAN frames to each other. However, in plain configuration these will not be received by the VCU, as the CAN ID of the inverter, or the can ID of the VCU must be adjusted. In the VCU software AEMCAL, this can be done by setting the values equal to the following:

<div class="row">
<div style="max-width: 600px; margin: 0 auto;">
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
<div class="caption"> Figure 2: CAN ID designation </div>

At this point, the devices should communicate successfully. This allows for commands to be sent between the devices, such as temperature readings or even torque request commands. 

I then wired an accelerator pedal from a Tesla Model 3, and implemented a 3 position switch as a gear selector, providing sufficient inputs for the VCU to unlock its drive state, and spin the motor. This marked completion of the first phase of the project - our VCU and motor successfully functioned together.  

<strong>Bench test two, further goals:</strong>

Coming back to the initial goals of the project - a high performance, long range, fast charging EV, we conducted a design review. The bench test functioned well, and would scale up to full size properly with a full set of batteries. However, questions remained, namely with the desired specifications of the original build. 
During this project's conception, two Tesla vehicles were salvaged for their battery packs, and all were to be used for the benefit of added range. However, this came with technical challenges - the motor-inverter package we had could only support a max voltage of 480V, yet the complete use of two full Tesla batteries would put the pack voltage beyond 700V, far too high for the equipment. Additionally, 250kW fast charging requires a system voltage of 800V, and currently no consumer equipment exists for this build. Clearly the scope of this project had to be adjusted. 

Within our capabilities of this project, we had to rely on consumer hardware for the specific electrical components. Looking around, Felten makes a kit for 150kW fast charging designed to integrate with Tesla fast chargers. It would require us to use a different BMS than originally planned and redesign a bit of our charging circuitry but otherwise it seemed promising. 

We would also have to change the amount of batteries that we planned to use. Given our 480V max operating voltage from the inverter, we were limited on the amount of batteries we could use. At 22V nominal per pack, we could use a max of 21 in series, providing about 110kWh of energy storage within the car, a promising amount. Given factors such as battery wear and usable battery capacity, this value would definitely be significantly lower, however it gave a comfortable driving range.
 



