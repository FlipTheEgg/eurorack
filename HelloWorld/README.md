# HelloWorld

WIP

Hello World! This is a three-channel eurorack mixer based on the schematic of the [AI Synthesis AI002](http://aisynthesis.com/ai002-diy-eurorack-mixer-module-build/), but more importantly, as the name might suggest, this is my first time doing several things. It's my first time...
 - Using KiCad
 - Making a eurorack module
 - Making something usable enough to give to someone (or maybe even sell)
 
I learned a lot in the process of making this, and I wanted to document those experiences - for myself as well as others that could be interested in learning the same. 

If you're just here to make the module, go ahead and skip to [Can I make this?](https://github.com/FlipTheEgg/eurorack/tree/master/HelloWorld#can-i-make-this).
 
 ## How did I  do it?

I wanted to start out simple, so I chose a schematic i *completely* understood: a simple mixer with a volume control. AI Synthesis has a wonderful selection of well-documented DIY builds, including schematics and build guides, and I chose to copy the AI002. The challenge with this project wasn't circuit design, but rather learning KiCad and designing to the specifications of Eurorack. My goal over time is to simultaneously design more sophisticated PCBs, and learn about more advanced circuits as I go.

With this specific project in mind I followed the guide [Getting Started in KiCad](https://docs.kicad-pcb.org/5.1/en/getting_started_in_kicad/getting_started_in_kicad.html), and substituted the example project with the AI002. I've previously experimented with [Fritzing](https://fritzing.org/), but I found it a little inaccurate and inflexible. Following the guide mostly went well and without issue. Not all the components I wanted to use had footprints in the standard Kicad library, but I managed to select some different components, or make my own footprints, which the guide also covers. I found KiCad to be slightly bulky to use at first, especially the disconnect between schematic symbol and footprint seemed cumbersome until I understood the flexibility this gives. I also had some confusion about how KiCad connects legs of the schematic components to the pins of the footprint (I can easily choose a 16-pin footprint to a 4-pin schematic component, for example), but  I realized that's where knowing how to edit footprints is really important and powerful. This also encouraged me to check the datasheets for my components whenever I was in doubt, which is good! The guide actually did answer almost all my questions, and upon revising my design, some of these quirks made more sense to me. For example, going back and choosing a different footprint or schematic symbol for a component, which I did a couple of times, was very quick and painless.

I also decided to design the panel as a PCB. I've seen this done on commercially available modules, and I think it looks good and seems both economical and practical. So I drew up a panel beside the main PCB (open the file HelloWorld.kicad_pcb to see how I did this), and followed the [Doepfer A100 Mechanical specification](http://www.doepfer.de/a100_man/a100m_e.htm) to see how to make the panel. I noticed that a lot of existing modules have oval mounting holes, which seemed smart. I also noticed that the Doepfer page said nothing about how tall my main PCB could be. Both of these problems were solved by measuring images of other modules on my screen, and calculating the length according to the known panel dimensions. This is not reccomended, *do* steal my findings from my schematics. I alsom made a custom footprint for the oval holes, as well as the holes for the potentiometers and the jacks. I might share these on GitHub at some point. Next time I think I'd like to make the PCB half a mm taller, so the offset, measured from the top and the bottom of the PCB, can be measured in whole mm's in relation to the panel. More on this measurement circus later. I later learned that having two boards in one file isn't as easy as I thought. KiCad handles it fine, but making it with a little breakoff part was incredibly difficult, and I couldn't figure it out. So I had to copy the main file, and make one file for the PCB and one for the panel. See (link...)

I realized that I needed a way to organize my Bill Of Materials (BOM) to keep track of what I needed to buy, so I made a spreadsheet where I listed and sourced my components, as well as held some other notes. This file is included in this repository, but it is a bit messy. I've deliberatly not cleaned it up, to give you an insight into how I worked. This process will likely be refined somehow. I chose to source my components at [Tayda](https://www.taydaelectronics.com/) and [Thonk](https://www.thonk.co.uk/) - more info in the BOM file.

Lastly I plotted the PCB to gerber files, ready to be manufactured, according to [the handy guide](https://support.jlcpcb.com/article/44-how-to-export-kicad-pcb-to-gerber-files) provided by my PCB manufacturer of choice, [JLCPCB](https://jlcpcb.com/). I reccomend following the guide for whereever you get them produced, it seemsl like they all have a lot of helpful information to help you to order correctly. I chose a black, Lead-free HASL board. Having the solder lead-free brought up the price a bit, but not by much. I made two seperate orders, one for the main board, and one for the panel, and ordered them together, choosing "europacket" as my shipping method. I'll report how it goes!

## What did I learn?
Here are some mistakes and experiences that I don't plan on repeating.
### Mils
While laying out the PCB, i quickly noticed that the standard grid wasn't in millimeters, but in [mils](https://en.wikipedia.org/wiki/Thousandth_of_an_inch). A mil is a thousandth of an inch, and 1 mil = 0.0254mm - just barely more than a quarter mm. This is apparently for historical reasons, but a lot of components are laid out with mil spacing between pins. I read somewhere that it has something to do with the tooling of PCB manufacturers, but I'm not really sure. What it meant for me, though, was, that I had to change the grid to mm. The Doepfer eurorack standard is defined in millimeters, and some of the components are measured in mils, so that's a bit annoying. I prioritized  setting millimeter spacings between externals - jacks, pots - and place the rest in mils. If I place the other components in mm, I can't align my IC and my caps properly, and that annoys me.

### Measure twice: Building the PCB before the panel is bad.
### Footprints: decide what components to use *before* you layout.
### File structure and you: This repository is a mess.
### Panel design.

## Can I make this?
Yeah, go ahead. Send the gerber zip files to JLCPCB or someone else, and read the BOM to find out what parts you need, and order them somewhere. But **Don't** send them the zip with the panel *and* the main PCB, that'll go wrong.

## Resources: 
 - [KiCad](https://kicad-pcb.org/)
 - [Getting Started in KiCad](https://docs.kicad-pcb.org/5.1/en/getting_started_in_kicad/getting_started_in_kicad.html)
 - [AI Synthesis AI002 build guide](http://aisynthesis.com/ai002-diy-eurorack-mixer-module-build/) Schematic is under "resources".
 - [Befaco](https://www.befaco.org/) also has the schematics available for all their modules. They're all significantly more advanced than this build, but I'll definitely be looking at them in the future!
 - [Doepfer A100 electrical specification](http://www.doepfer.de/a100_man/a100t_e.htm)
 - [Doepfer A100 mechanical specification](http://www.doepfer.de/a100_man/a100m_e.htm)
 - [DigiKey footprint library](https://www.digikey.com/en/resources/design-tools/kicad)
