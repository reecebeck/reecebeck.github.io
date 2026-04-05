---
layout: page
title: DC-DC Converter
description: 
img: assets/img/DSC06281.jpg
importance: 2
category: All
---
<strong>Background: </strong>
I needed to power an opamp circuit that required dual rail supply voltage, in my case +12V and -12V. Here is the circuit I designed to do it with a 9V battery. 

<strong>Design:</strong>
There are many different ways to achieve this basic voltage conversion - a basic boost converter with a single inductor, charge pump ics, transformer etc. However, the circuit had to put out a decent amount of current, and have little electrical noise. For the sake of simplicity, I chose a transformer based power supply with the SG3524 IC. 

Choosing an operating frequency of 100kHz meant electrical noise within the audible range would be low. It also meant a smaller transformer core could be used. 

Finding a core for this application requires considering core saturation as a function of turn count and core material, given a known operating frequency, supply voltage, and saturation flux. We rewrite Faraday's law to find cross sectional area for a rectangular switching waveform (constant dB/dt), which gives the equation Ae = (V × Δt) / (N × ΔB). ΔB is found based off the core material used - here n87 ferrite. At 100kHz, we will target a flux density of 300mT as core losses are reasonable. With a primary turn count of 12 turns, at 9V, this gives a cross section of 12.5mm^2. I chose the TDK 20X10X7 T35 TOROID for extra safety factor. 

<div class="row">
<div style="max-width: 550px; margin: 0 auto;">
    <div class="col-sm mt-3 mt-md-0">
       {% include figure.liquid 
   loading='eager' 
   path='assets/img/DSC_0589.jpg' 
   title='example image' 
   class='img-fluid rounded z-dep   th-1' 
%}
    </div>
    </div>
</div>
<div class="caption"> Figure 1: Voltage spikes due to leakage inductance</div>

Initially this circuit suffered from large voltage spikes on the primary, as the leakage inductance of the transformer was high. I rewound the transformer to have a bifilar wound primary to correct this. Coupling was also improved by overlapping the primary and secondary windings.

<div class="row">
<div style="max-width: 550px; margin: 0 auto;">
    <div class="col-sm mt-3 mt-md-0">
       {% include figure.liquid 
   loading='eager' 
   path='assets/img/DSC06281.jpg' 
   title='example image' 
   class='img-fluid rounded z-dep   th-1' 
%}
    </div>
    </div>
</div>
<div class="caption"> Figure 2: The completed board with linear regulation</div>