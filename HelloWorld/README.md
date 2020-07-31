# HelloWorld

WIP

Hello World! This is a three-channel eurorack mixer based on the schematic of the [AI002](http://aisynthesis.com/ai002-diy-eurorack-mixer-module-build/), but more importantly, as the name might suggest, this is my first time doing several things. It's my first time...
 - Using KiCad
 - Making a eurorack module
 - Making something usable enough to give to someone (or maybe even sell)
 
I learned a lot in the process of making this, and I wanted to document those experiences - for myself as well as others that could be interested in learning the same. 

If you're just here to make the module, go ahead and skip to [Can I make this?](https://github.com/FlipTheEgg/eurorack/tree/master/HelloWorld#can-i-make-this).
 
 ## How did I  do it?

I wanted to start out simple, so I chose a schematic i *completely* understood: a simple mixer with a volume control. AI Synthesis has a wonderful selection of well-documented DIY builds, including schematics and build guides, and I chose to copy the AI002. The challenge with this project wasn't circuit design, but rather learning KiCad and designing to the specifications of Eurorack. My goal over time is to simultaneously design more sophisticated PCBs, and learn about more advanced circuits as I go.

With this specific project in mind I followed the guide [Getting Started in KiCad](https://docs.kicad-pcb.org/5.1/en/getting_started_in_kicad/getting_started_in_kicad.html), and substituted the example project with the AI002. I've previously experimented with [Fritzing](https://fritzing.org/), but I found it a little inaccurate and inflexible. Following the guide mostly went well and without issue. Not all the components I wanted to use had footprints in the standard Kicad library, but I managed to select some different components, or make my own footprints, which the guide also covers. I found KiCad to be slightly bulky to use at first, especially the disconnect between schematic symbol and footprint seemed cumbersome until I understood the flexibility this gives. I also had some confusion about how KiCad connects legs of the schematic components to the pins of the footprint (I can easily choose a 16-pin footprint to a 4-pin schematic component, for example), but  I realized that's where knowing how to edit footprints is really important and powerful. This also encouraged me to check the datasheets for my components whenever I was in doubt, which is good! The guide actually did answer almost all my questions, and upon revising my design, some of these quirks made more sense to me. For example, going back and choosing a different footprint or schematic symbol for a component, which I did a couple of times, was very quick and painless.

I also decided to design the panel as a PCB. I've seen this done on commercially available modules, and I think it looks good and seems both economical and practical. So I drew up a panel beside the main PCB (open the file HelloWorld.kicad_pcb to see how I did this), and followed the [Doepfer A100 Mechanical specification](http://www.doepfer.de/a100_man/a100m_e.htm) to see how to make the panel. I noticed that a lot of existing modules have oval mounting holes, which seemed smart. I also noticed that the Doepfer page said nothing about how tall my main PCB could be. Both of these problems were solved by measuring images of other modules on my screen, and calculating the length according to the known panel dimensions. This is not reccomended, *do* steal my findings from my schematics. I alsom made a custom footprint for the oval holes, as well as the holes for the potentiometers and the jacks. I might share these on GitHub at some point. Next time I think I'd like to make the PCB half a mm taller, so the offset, measured from the top and the bottom of the PCB, can be measured in whole mm's in relation to the panel. More on this measurement circus later. I later learned that having two boards in one file isn't as easy as I thought. KiCad handles it fine, but making it with a little breakoff part was incredibly difficult, and I couldn't figure it out. So I had to copy the main file, and make one file for the PCB and one for the panel. See (link...)

## What did I learn?
Here are some mistakes and experiences that I don't plan on repeating.

### mils
### Measure twice: Building the PCB before the panel is bad.
### Footprints: decide what components to use *before* you layout.
### File structure and you: This repository is a mess.
### Panel design.

## Can I make this?
Yeah, go ahead. Send the gerber zip files to JLCPCB or someone else, and read the BOM to find out what parts you need, and order them somewhere.

## Resources: 
 - [KiCad](https://kicad-pcb.org/)
 - [Getting Started in KiCad](https://docs.kicad-pcb.org/5.1/en/getting_started_in_kicad/getting_started_in_kicad.html)
 - [AI Synthesis AI002 build guide](http://aisynthesis.com/ai002-diy-eurorack-mixer-module-build/) Schematic is under "resources".
 - [Befaco](https://www.befaco.org/) also has the schematics available for all their modules. They're all significantly more advanced than this build, but I'll definitely be looking at them in the future!
 - [Doepfer A100 electrical specification](http://www.doepfer.de/a100_man/a100t_e.htm)
 - [Doepfer A100 mechanical specification](http://www.doepfer.de/a100_man/a100m_e.htm)
 - [DigiKey footprint library](https://www.digikey.com/en/resources/design-tools/kicad)
