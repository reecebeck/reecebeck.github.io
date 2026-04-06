---
layout: page
title: FRC Shooter Development
description: 
img: assets/img/Shooter.png
importance: 3
category: All
---
<strong>Background: </strong>
As part of 8033 Highlander Robotics, I led the team working on shooter development. This subsystem was built in about 5 weeks, from initial prototypes to the final revision. All CAD was done in OnShape, and the final shooter was milled from aluminum plate.

<strong>Design and Prototyping:</strong>

The game piece for this year was a foam ring about a foot in diameter and similar in density to a dodgeball. Our task was to develop a system to shoot it at targets up to 30 feet away, 12 feet in the air. 
Many different prototypes were constructed as we set to settle on a collection of parameters for our final shooter. These included shot speed and spin, ring compression, and wheel material and grip. 

Our first prototype is shown below in CAD. It lacks many of the features to be built into our final revision, spin and compression control. 
 

<div class="row">
<div style="max-width: 550px; margin: 0 auto;">
    <div class="col-sm mt-3 mt-md-0">
       {% include figure.liquid 
   loading='eager' 
   path='assets/img/Shooter_Rev1.png' 
   title='example image' 
   class='img-fluid rounded z-dep   th-1' 
%}
    </div>
    </div>
</div>
<div class="caption"> Figure 1: Initial prototype CAD</div>

The final shooter uses two independently controlled sets of Stealth wheels to create spin on the ring. Additionally visible in the photo is a Maxspline cross shaft, handling the majority of structural load in the shooter body while allowing for its precise angle adjustment pivot. 

<div class="row">
<div style="max-width: 550px; margin: 0 auto;">
    <div class="col-sm mt-3 mt-md-0">
       {% include figure.liquid 
   loading='eager' 
   path='assets/img/Shooter.png' 
   title='example image' 
   class='img-fluid rounded z-dep   th-1' 
%}
    </div>
    </div>
</div>
<div class="caption"> Figure 2: The final shooter revision</div>