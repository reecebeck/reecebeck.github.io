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

Our first full prototype is shown below in CAD. Its purpose was to test the reproducibility of shots that we could produce at full power. We decided that full independent control of each side of the shooter was necessary for increased accuracy, as it would allow us to develop precise control of the spin of the ring.
 
 

<div class="row">
<div style="max-width: 550px; margin: 0 auto;">
    <div class="col-sm mt-3 mt-md-0">
       {% include figure.liquid 
   loading='eager' 
   path='assets/img/Shooter_Rev1.png' 
   title='First Shooter Prototype' 
   class='img-fluid rounded z-dep   th-1' 
%}
    </div>
    </div>
</div>
<div class="caption"> Figure 1: Initial prototype CAD</div>

The final shooter uses two independently controlled sets of Stealth wheels to allow a precise torque to be generated on the ring, similar to a frisbee. Additionally visible in the photo is a Maxspline cross shaft, handling the majority of structural load in the shooter body while allowing for its precise angle adjustment pivot. 

<div class="row">
<div style="max-width: 550px; margin: 0 auto;">
    <div class="col-sm mt-3 mt-md-0">
       {% include figure.liquid 
   loading='eager' 
   path='assets/img/Shooter.png' 
   title='Final Shooter CAD' 
   class='img-fluid rounded z-dep   th-1' 
%}
    </div>
    </div>
</div>
<div class="caption"> Figure 2: The final shooter revision</div>

This version functioned very effectively in our final robot, and led us to a top 16 finish in the FRC world championship. We also placed #9 in California in EPA, a scoring metric that heavily factors shooting performance. 

Overall, this project showcases not just effective implementation and design, but a success of the prototyping process. We were able to figure the exact parameters necessary to achieve our design goals, learning much about a difficult to model process. Over the course of 5 weeks, we produced 2 finalized prototypes - but many more small models that considered a range of variables. Many of these were lower fidelity - constructed from plywood, no computer control, but led us to effective design decisions.

An earlier prototype is shown below in slow motion:

<div class="row">
  <div style="max-width: 550px; margin: 0 auto;">
    <div class="col-sm mt-3 mt-md-0">
      
      <video 
        class="img-fluid rounded z-depth-1" 
        controls 
        autoplay 
        muted 
        loop 
        playsinline
        style="width: 100%;">
        
        <source src="{{ 'assets/video/Shooter_Prototype.mov' | relative_url }}" type="video/mp4">
        Your browser does not support the video tag.
      </video>

    </div>
  </div>
</div>
<div class="caption">Figure 3: Prototype Testing</div>