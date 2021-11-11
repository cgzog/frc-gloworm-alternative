# PhotonVision Module

This a fully self-supporting PhotonVision platform for teams that want to roll their own.  Functionally, it is similar to the Gloworm - I want to be right out there and say the Gloworm is a great platform, you can't really beat it for the cost and level of integration but at or around the time of release for this design, they aren't available.  I own one and would buy more if they were available but to help spread the goodness of PhotonVision, I've put this project together to leverage a lot of commonly available parts into a single cohesive platform.  It ends up  little larger than the Gloworm or the Limelight but those are the breaks when you're using off the shelf modules and not custom hardware - you just can't hit the same level of integration.


## DESIGN OVERVIEW

### General Considerations

I've experimented with a number of different approaches to designing these sorts of enclosures.  Rather than take elaborate and detailed measurements for commercial parts like PCBs or camera modules, or what have you and then accommodate them in the design, I've chosen to just go ahead and actually model them.  I don't bother with every single component or aspect but I do make sure to include important aspects; "important" in this case means locations, shape and orientation of things like connectors or major components that impact the overall or other characteristics of the module.

This has a number of powerful advantages:

1. It's easy to see the overall module you are working with as it's an actual visible component and not just an abstract set of dimensions.

2. It's easy to verify that your design seems reasonable because you can actually see the module and can often see mistakes or errors because you can compare your CAD representation with the actual module.

3. You can easily visualize the final assembly and spot alignment problems or interference problems at an early stage in the design.

Once you designed a PCB (as one example) including aspects like mounting holes and connectors, it's easy to use those features in other parts of the design to easily create openings or mounting points.  Doing it in this way, you'll easily be able to reorganize or move the locations of things like PCB modules and have the pertinent features follow without having to do a lot of manual design changes.


### Raspberry Pi version support
The design accommodates both Raspberry Pi 3 and Raspberry Pi 4 PCBs; to configure one or the other, suppress the folder containing the version you don't want and make sure the other is unsuppressed.

A couple of notes here:

1. It's been a while since I even tried to generate a design using the RPi4 features so it's likely there could be problems there.  If you find some, I'd be willing to take a look if you can't figure it out.

2. You really don't WANT the RPi4 anway; the RPi3 has graphic acceleration that PhotonVision uses to great benefit so go with the RPi3 to get it.

### Driving the LEDs

Different CC modules for driving LEDs

parallel / serial wiring


## PRINTING

I like nicely printed parts so I'm willing to trade quality for time.  I printed my parts at .1mm layer height but up to .2mm should be fine.  An infill of 30% and 5-6 outside / top / bottom layers with supports enabled will yield very strong parts.

With only 2 3D printed parts, the natural orientation of the bottom with the bottom surface on the build plate and the top oriented so that the top, outer, layer on the build plate will yield great results.

### Support Considerations

On the case bottom, depending on your slicer settings, some of the supports may meld together.  This is prone to happen at the corners where the vent slots are as well as the adjacent corner where the RPi Ethernet connector opening is located.  I like dense supports to get the nicest bottom surfaces but you may want to create some test prints by sectioning the bottom to do some test prints of the corners.  Using the preview capabilities of your slicer will help here as well.  The best advice is to remove these supports carefully to avoid damaging the case bottom.  You may find doing some scoring for the vent slots with a sharp hobby knife to be helpful in removing supports there.


## ASSEMBLY

### General Wiring Considerations

Depending on how you do things, there are numerous different connections that will need to be made.  At a minimum, you'll be soldering wires to the DC-DC converter and connecting to the RPi using the Dupont-style connectors on it's header.  I use move connectors to allow things to be installed separately and allow the top and bottom to be removed which includes 2.0mm and 2.54mm JST connectors and locking JST-style connectors but whether you use them is up to you and your build - they aren't required.

I won't cover soldering but for the Dupont and other connectors, proper crimping tools are a must.  While I won't use regular crimp connectors (the red, blue, and yellow insulated stuff) without a ratcheting crimper, there are other options available for the smaller crimp connectors.  My personal favorite is one of the simpler ones out there, the Engineer PA-09 crimper (http://www.amazon.com/SHIPPER-Molex-Style-CRIMPER-PLIERS/dp/B01EGS7KXQ); make you you get the real deal made in Japan model.  What I especially like with it is that it seems easier to me to deal with the wire and insulation crimps separately for the smaller connectors rather than the all-in-one action of ratcheting crimpers.  If you're a fan of the ratcheting style, I've had decent results with the Iwiss IWS-3220M crimper (https://www.amazon.com/IWISS-IWS-3220M-Connector-0-03-0-52mm%C2%B2-Ratcheting/dp/B078WPT5M1).  There are a lot of resources out there talking about various crimpers and there are a lot of crummy ones out there - buyer beware!  Buy it, test it, and if you don't like it, try another.

When wiring for the Dupont-style connectors, my experience is 22ga wire, PVC or similar insulation, is about right - any larger and it won't fit into the connector body correctly.  Also, avoid the "silicone" insulated wire - it's really nice and flexible but the insulation is "squishy" and the insulation crimps tend to not crimp well (the  squish and cut the insulation so they are not a durable strain relief which is the whole point on that part of the crimp.  Regular PVC and similar insulation works best for me.
22ga for the Dupont

Practice

### Bottom

The main issues here are removing the supporting material.  Care needs to be taken on the slotted vents, the fan openings, and the USB / Ethernet Raspberry Pi opening with special care on the RPi openings.  The supports for the lid mounts should be very easy to remove with care taken where your slicer might merge them with the supports for adjacent vent slots so just work carefully and consider using something like a hobby knife to cut through some vent supports where appropriate.

When installing the threaded inserts, some of the lower inserts are quite close to the sides of the case so some care needs to be taken to prevent damage to the sides of the case when installing them; I made extended tips for my soldering iron for installing inserts in the bottom portion to allow the straight-in installation of the inserts with touching the bottom sides.

The rest of the bottom assembly of mounting the PCBs is fairly straight forward using 4-40 screws; you'll find the RPi holes will need to be slightly opened to clearance but the RPi PCBs have no traces in this area and the holes can be opened with great confidence.  Maneuvering the RPi into the bottom corner of the case can be a bit of a challenge so it is strongly suggested to install it first.  Installation of the FET module and the DC-DC converter is fairly direct though the input and output wires for the DC-DC converter should be soldered in place on the PCB before installation of the PCB since they will not be accessible later; soldering 8" lengths in place for both + / - input and output is more than long enough to allow trimming and the installation of appropriate terminations later in the assembly process.

Once the RPi PCB is installed, the case fan can be mounted.  The moting orientation is with the label towards the outside.  This will cause the fan to pull air through the case and out the fan holes.

A couple of words of note regarding the DC-DC converter:

** Not everyone making that LM2596-based DC-DC converter got the PCB mounting holes spacing memo.  I based the design on a set I had on hand but I have seen some that have a slightly closer location of the mounting holes (along the axis of the long side of the PCB).  If yours are closer and you've already printed your bottom, take a file or a hobby knife and open the holes towards the center of the board, parallel to the long edge, about .25mm or so for both holes.  DON'T re-drill them to a bigger size as they are already pretty close to the outside edge of the PCB.  The mounting holes are typically plated through but are electrically isolated from the rest of the circuit so there is no concern about breaking conductivity or having the metal screws touch anything else on the board (the mounting screw near the input side of the board can come very close to the + side of the input electrolytic capacitor but even if the screw touches it, there is not a problem).  If you haven't printed the bottom yet, you can verify your mounting holes and adjust the model of the DC-DC converter in the design to accommodate your holes; the input side of the DC-DC converter ends up pretty close to the small side of the case so you probably don't want to move that mounting hole too far inboard to prevent interference with the case.  You should be able to check the design for problems here before you print the bottom.

** Before powering up the DC-DC module, turn the adjustment potentiometer all the way down (counter clockwise).  Once things are wired to the RPi, you can use a voltmeter to turn the voltage up to 5VDC but you don't want to risk over voltage on the RPi the first time you power it up.

When you install the primary power connector, there will be 3 pair of wires connecting to it:

** Power to the DC-DC converter
** Power to the FET module to control the LEDs (going into the Vin connection)
** Power to the fan

## Top

### Threaded Inserts
The primary issue with the top is careful installation of the threaded inserts - they install in printed "pedestals" so they need to be installed straight and not installed too deeply.  When inserting them, work quickly and decisively because there isn't a lot of 3D printed material here and going to slowly will distort the mounting pedestals and your holes will no longer be located properly.

### LEDs and Heatsinks

### Constant Current Driver

### Camera

### Light Pipes

### Wiring


# PHOTONVISION CONFIGURATION

Most of the configuration settings needed for using this build are in the XXX.json file.

Here is a sample file that will get you going:

```json

dfsfdfdfd
```
